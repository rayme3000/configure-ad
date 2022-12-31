<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the Client-1 and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Setup Remote Desktop for non-administrative users on Client-1

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Create the Domain Controller VM (Windows Server 2022) named “DC-1”.
  <br>
2. Set Domain Controller’s NIC Private IP address to be static.
  <br>
3. Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet.
  <br>
4. Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher.

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping).
<br>
6. Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall.
<br>
7. Check back at Client-1 to see the ping succeed.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
8. Login to DC-1 and install Active Directory Domain Services.
<br>
9. Promote as a DC: Setup a new forest as mydomain.com (for example).
<br>
10. Restart and then log back into DC-1 as user: mydomain.com\labuser.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11. In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”.
<br>
12. Create a new OU named “_ADMINS”.
<br>
13. Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”.
<br>
14. Add jane_admin to the “Domain Admins” Security Group.

<p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
15. Log into Client-1 as mydomain.com\jane_admin and open system properties.
<br>
16. Allow “domain users” access to remote desktop.
<br>
17. You can now log into Client-1 as a normal, non-administrative user now.


<p>
<br />

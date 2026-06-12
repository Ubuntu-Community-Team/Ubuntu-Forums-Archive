---
title: "Can't SSH into Ubuntu Server 14.05 LTS from PuTTY"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by djschwartz2 on 2016-11-23
Hello all,

I am trying to SSH into my VirtualBox vm of Ubuntu Server 14.05 from PuTTY. For networking, I have configured 2 network adapters (Adapter 1 = Bridged and Adapter 2 = NAT), both of which I've tried changing to Host Only and to NAT Networking. I configured Port Forwarding to create a rule for a port 22 SSH connection. I have installed OpenSSH Client and Server on my VM multiple times, and I see that it is running when I run the "service ssh restart" command. I can do normal networking fine on the VM, and I am able to ssh WITHIN the VM (ssh <username>@127.0.0.1), but still, I am unable to ssh via PuTTY, which leads me to believe that it's a PuTTY or VirtualBox setting issue. 

I've put my "192.x.x.x" address of my bridged adapter interface and port 22 into the settings of PuTTY so I have no idea why it's not working. Any ideas? Thanks!

---

### Post by kpatz on 2016-11-23
What's the output of **netstat -an | grep ':22'** inside your VM?

You should be able to connect to the bridged adapter, or to a NAT one with port 22 forwarded.  I'd start with the bridged since it's simpler.

Did you change anything in /etc/ssh/sshd.config?

Can you ping the VM's bridged IP from your machine that has PuTTY?

What is the error message you're getting from PuTTY when you try to connect?

Have you configured any firewall on the VM, or on the VM's host (i.e. iptables, ufw)?  What's the host OS?

---

### Post by djschwartz2 on 2016-11-23
[LIST]
[*]Attached is what I'm seeing when I run the "netstat -an | grep "22" " command
[/LIST]

[LIST]
[*]I'm still unable to connect to the Bridged adapter IP address having port forwarded rules established on NAT adapter. Attached is my screenshot of my port forwarding settings:
[/LIST]

                      Name: SSH
                      Protocol: TCP
                      Host Port: 3322
                      Guest Port: 22
               

[LIST]
[*]I didn't change anything at all in the /etc/ssh/ssh_config file
[*]I cannot ping my VM from my local Windows 7 machine
[*]I am receiving "Network error: Connection Timed Out"
[*]I have not configured a firewall on my Ubuntu Server.
[/LIST]

---

### Post by ajgreeny on 2016-11-23
*Thread moved to **Networking & Wireless**.* which is more appropriate for the problem and should be a better fit.

---

### Post by kpatz on 2016-11-23
> **djschwartz2 said:**
> I cannot ping my VM from my local Windows 7 machineCan you ping the host machine (the one the VM is running on) from your Windows 7 machine?  What OS is the host running?  If it's a Windows host, it could be the firewall preventing access to the VMs.

If the adapter in the VM is bridged, it should have an IP in the same subnet as the rest of your network.  So, for example, if your network uses 192.168.1.x IPs, the VM's bridged adapter should have an IP in this subnet as well.  If your VM adapter is NAT, it'll have a 10.x.x.x IP.

For example, let's assume your network has IP address in the 192.168.1.x range.  If your Windows 7 machine is 192.168.1.10 and your VM host machine is 192.168.1.11, the bridged adapter in the VM is 192.168.1.12 and the NAT adapter is 10.1.1.1, you should be able to ssh to the VM via the bridged adapter at 192.168.1.12 port 22, or through the NAT adapter via port forwarding at 192.168.1.11 port 3322.

BTW, you can post your 192.168.x.x IPs here.  They're private IPs and aren't accessible from the internet at large.  It might help with troubleshooting your issue, especially if you can't ping the host machine from the Win7 machine.

---

### Post by djschwartz2 on 2016-11-23
I'm able to ping the Ubuntu server VM from my Windows 7 local machine when I run sudo ufw disable but still can't SSH. I can ping my VirtualBox host adapter IP fine from my Windows 7 local machine.

My eth0 interface (bridged adapter) is configured for 192.168.56.110, which is the IP I am using to attempt to SSH in from the PuTTY host. This is configured in my VirtualBox network settings as the lowerbound IP in the IP range. I've attempted changing it to a different suffix as well (111) but still having the same issues. My NAT is indeed 10.x.x.x but I still can't ping it from the method you described in your post

---

### Post by kpatz on 2016-11-23
> **djschwartz2 said:**
> My eth0 interface (bridged adapter) is configured for 192.168.56.110, which is the IP I am using to attempt to SSH in from the PuTTY host. This is configured in my VirtualBox network settings as the lowerbound IP in the IP range. I've attempted changing it to a different suffix as well (111) but still having the same issues. My NAT is indeed 10.x.x.x but I still can't ping it from the method you described in your postCan you show me what you mean in a screenshot showing the Virtualbox network settings?  How are IPs assigned on your network, via DHCP from a router?  Or are they statically assigned, manually to each system?  Are all your IPs (other than the NAT adapter) in the 192.168.56.x range?

If your IPs are assigned dynamically, the VM should use DHCP on the bridged adapter, to get an IP from the router.  The NAT adapter gets its 10.x.x.x IP from DHCP provided by VirtualBox.

Bridged essentially "plugs" your VM's "network cable" directly into your network, like a physical machine would be connected, so it gets an IP on your local network.  NAT is basically putting your VMs behind their own virtual router, so they get their own range of IP addresses, and to connect to them from outside requires using port forwarding.

---


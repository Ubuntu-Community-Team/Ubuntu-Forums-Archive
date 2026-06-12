---
title: "Easy Networking w/ SSHFS"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Emerzen on 2007-04-24
First, a caveat, I'm new to networking, so take this w/ a grain of salt.

I have a home network consisting of a Linksys WRT300N wireless router, a Desktop connected directly to it and two laptops all running Feisty now.  After reading up on the many ways to home network I, first, settled on NFS but found it too cumbersome.  I then came across SSHFS (SSH w/ a GUI essentially) and it was ridiculously simple compared to everything else I tried.  So, here it is:

1.  Configure your router to maintain static ip's for all the PC's on your LAN.  (This does not mean your WAN ip is static, just that your router assigns static ip's inside your network).  With my router it's a simple checkmark on the first router config page.

2.  Write down those ip #'s and which machine they're assigned to.

3.  On each machine search Synaptic and install ssh and sshfs (w/ any dependencies).

4.  If you have a firewall you must allow incoming reception for those ports...22 I believe for each computer's static ip on your LAN.  With Firestarter, under policy add SSH for incoming for each computer.  I also allow connections from each of those ip's under host, but not sure if that is necessary.

5.  Reboot those pc's to make sure all the necessary services are running.

6.  On any Feisty->Places->Connect to Server->pick SSH and enter the ip of the computer you want to network with-> wait and give username and passwords for those boxes.  A network folder should shortly appear on your desktop that, when clicked, will bring up the root of the networked PC.

That's it.  If anyone w/ more knowledge cares to add to this, please feel free.  I know it's possible to add these mounts to fstab, but I don't like to do this so I don't care to figure it out.  I also know that it's possible to connect to a Windows PC this route if that PC has SSHFS installed, which is available from Cygwin's site.  I'm going to work on that and if it's just as simple, I'll add the directions.

---

### Post by Emerzen on 2007-04-25
Update -- How to connect to the SSH server via a Windows Client
--------------------------------------------------------------------------------

There are many solutions to this problem as I alluded to above mentioning Cygwin.  However, I found a simpler one via a native Windows app and w/ a GUI.  The situation is that I want to be able to access my Ubuntu network from work.  My solution:

I installed a program from this website , [rs4u]("http://www.rs4u.com/Products.htm"), which is a GUI native Windows client to log into your SSH server.  Just download it and install it on any windows machine.  It can be run as a web client, thereby circumventing any corporate firewalls that may make this difficult.  A second  problem is figuring out what your ip is if your ISP assigns it to you via DHCP.  A way around this is to sign up for this free service at [DynDNS]("http://www.dyndns.com/") .  They assign you a hostname attached to your ip.  Okay, what happens when your ISP changes your ip?  1.) if you're on your pc that has the SSH server go to the DynDNS homepage, log in, and run their update tool.  2.) Install any of several programs (available in Windows and Linux) that runs as a service on your SSH server-> it will check for your ip every so often and if changes, updates it at DynDNS automatically.  3.) If your router supports it, as mine does, you can configure it to send the updated/new ip to DynDNS automatically. 

-Hope this helps some of the community members.

---

### Post by Emerzen on 2007-04-28
Forget about rs4u, [here's the easiest solution yet]("http://winscp.net/eng/index.php") for client side GUI access (Windows).

---

### Post by Mud.Knee.Havoc on 2007-10-24
I can't believe it... that was so easy.  It took me a total of about 2.5 minutes to get both of my computers connected with your instructions.  I didn't bother rebooting, just typed "sudo /etc/init.d/ssh start" on both computers and it got ssh going.  

Just too easy!!  Keep up the great work!

---

### Post by mcrae on 2007-10-26
> **Emerzen said:**
> 
A network folder should shortly appear on your desktop that, when clicked, will bring up the root of the networked PC.



Does anybody know what is the path to this network folder on the desktop...I prefer to work in a shell..

---

### Post by Endolith on 2007-11-08
> **Emerzen said:**
> Configure your router to maintain static ip's for all the PC's on your LAN.

I just type the computer's name instead of the IP, analogous to using "ssh computername" instead of "ssh 192.168.1.2".

---

### Post by Endolith on 2007-11-08
Wait a second.  Is this really sshfs?  Because I don't have that installed.  :-)  So I suspect it is something else.  I am trying to figure out "the easy way" (GUI way) for mounting so that Quod Libet can read it:

[http://ubuntuforums.org/showthread.php?t=596406](http://ubuntuforums.org/showthread.php?t=596406)

---

### Post by kalmi on 2008-04-22
This technique works without having to install anything.

---


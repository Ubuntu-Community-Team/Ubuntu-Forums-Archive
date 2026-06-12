---
title: "Port forwarding my ubuntu NAS to access remotely"
date: 2016-07-12
forum: Networking &amp; Wireless
---

### Post by blake12 on 2016-07-12
Hi all,

Firstly id like to say that my experience with the cmd side of things is limited at best and also my background knowledge in networks is also limited but growing, so id ask if you can please try and explain everything in the fullest to help me understand. 

My network topology:

Internet -> Modem/Router (Netgear D6300) -> Switch (Cisco 300 series) -> all network devices at home hardwired 
Hardwired: - Ubuntu
                 - TV
                 - Laptop
                 - PS4
                 - PS3
                 - Access Point (Netgear R7000)

I am wanting to access my ubuntu server (running ubuntu desktop) remotely both by remote desktop and also having a permanent network drive on my computer. I have created a dynamic DNS which directs to my main modem router (netgear D6300) at home and have forwarded ports 80(web), 20/21(FTP), 1701(VPN L2TP), and 3389 (remote desktop) to the ubuntu machine with IP address 192.168.0.100 which is statically set. 

The problem i am having is when i use port checker it tells me that the connection was refused for port 80 but times out of 3389. I have added the ports to be forward using:

[FONT=monospace]sudo ufw allow 22[/FONT]I have also done this for the other ports i have mentioned here and it still seems that the port checker returns the same result. Is this a correct way to do it?

I have had issues in the past with Samba not allowing my MAC OS to connect to the server yet remote desktop works fine from the laptop mentioned above. 

Thanks in advance for your help.

Blake

---

### Post by TheFu on 2016-07-12
The secure and easy way to access your home LAN from anywhere else in the world is to use ssh.  That means only 1 port need be opened and secured.  [FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") and RDP are not secure and shouldn't be made available over the internet directly.  

There's good news. ssh is an amazing tool that uses a single port and secure authentication (always use keys for authentication, never passwords). It is enough for remote file access via sftp, remote desktop via x2go (which is an NX protocol), and remote terminal access via ssh. If the clients are Unix-based, then sshfs will remotely mount storage from your network anywhere in the world too. There should be a port for OSX.  ssh is THE WAY that Unix systems communicate and that administration is performed world-wide.  Right now, I'm logged into 7 other systems ... all thru ssh.

As for the VPN, I prefer IPSec over L2TP ... can't remember the reasons why now, just that there was something important that IPSec does. Don't recall any specific issues with l2tp - it isn't pptp - which is a good thing. Very few people should use pptp since 2002, well, unless you want the other side to think you don't know they have complete access to your (cough) encrypted tunnel. 

Your dynamic DNS provider needs to point to the WAN IP.  Do all your devices get static IPs inside your network?  I've had issues with netgear routers NOT forwarding ports before.  Also, some ISPs block commonly used services, unless you have a business account. I'm pretty certain they block 3389 to protect people from themselves, the same for CIFS ports.

If you do decide to go with ssh for remote access, [be certain to secure it.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")

So in short, setup ssh and get that working from outside. That will cover all the router and authentication checks. If ssh works, then sftp, scp, sshfs, and x2go will work too.  Then add x2go-server (on the machine inside) and x2go-client on the laptop outside.  x2go as a remote desktop is about 2-3x faster than either VNC or RDP.  Just follow the instructions and use the PPA for the packages.  No remote desktops work with DEs that need HW accelerated GPUs, so you'll need to avoid Unity/Gnome3 ... basically, use LXDE, XFCE, KDE or some pure WM as the desktop.

Bam. All your access needs are solved.  If you want to run a VPN inside the house so you can forward all your smartphone traffic through it instead of trusting open wifi, great - openvpn is the well-known solution for that and deployed worldwide by organizations of all sizes.

Of course, you can elect to go in the same direction you are headed if you like. Someone else will need to help.

---

### Post by blake12 on 2016-07-13
> **TheFu said:**
> The secure and easy way to access your home LAN from anywhere else in the world is to use ssh.  That means only 1 port need be opened and secured.  [FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") and RDP are not secure and shouldn't be made available over the internet directly.  

There's good news. ssh is an amazing tool that uses a single port and secure authentication (always use keys for authentication, never passwords). It is enough for remote file access via sftp, remote desktop via x2go (which is an NX protocol), and remote terminal access via ssh. If the clients are Unix-based, then sshfs will remotely mount storage from your network anywhere in the world too. There should be a port for OSX.  ssh is THE WAY that Unix systems communicate and that administration is performed world-wide.  Right now, I'm logged into 7 other systems ... all thru ssh.

As for the VPN, I prefer IPSec over L2TP ... can't remember the reasons why now, just that there was something important that IPSec does. Don't recall any specific issues with l2tp - it isn't pptp - which is a good thing. Very few people should use pptp since 2002, well, unless you want the other side to think you don't know they have complete access to your (cough) encrypted tunnel. 

Your dynamic DNS provider needs to point to the WAN IP.  Do all your devices get static IPs inside your network?  I've had issues with netgear routers NOT forwarding ports before.  Also, some ISPs block commonly used services, unless you have a business account. I'm pretty certain they block 3389 to protect people from themselves, the same for CIFS ports.

If you do decide to go with ssh for remote access, [be certain to secure it.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")

So in short, setup ssh and get that working from outside. That will cover all the router and authentication checks. If ssh works, then sftp, scp, sshfs, and x2go will work too.  Then add x2go-server (on the machine inside) and x2go-client on the laptop outside.  x2go as a remote desktop is about 2-3x faster than either VNC or RDP.  Just follow the instructions and use the PPA for the packages.  No remote desktops work with DEs that need HW accelerated GPUs, so you'll need to avoid Unity/Gnome3 ... basically, use LXDE, XFCE, KDE or some pure WM as the desktop.

Bam. All your access needs are solved.  If you want to run a VPN inside the house so you can forward all your smartphone traffic through it instead of trusting open wifi, great - openvpn is the well-known solution for that and deployed worldwide by organizations of all sizes.

Of course, you can elect to go in the same direction you are headed if you like. Someone else will need to help.

Thanks for your response @TheFu. 

I have just been having a read on that link you have posted and it seems like it certainly is the easiest way to go about it. I will give it some more reading this afternoon/tonight and I will try and do as you mentioned and get back to you.

Thanks again for the response ill give this a crack and see how we go!

---

### Post by blake12 on 2016-07-14
> **TheFu said:**
> The secure and easy way to access your home LAN from anywhere else in the world is to use ssh.  That means only 1 port need be opened and secured.  [FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") and RDP are not secure and shouldn't be made available over the internet directly.  

There's good news. ssh is an amazing tool that uses a single port and secure authentication (always use keys for authentication, never passwords). It is enough for remote file access via sftp, remote desktop via x2go (which is an NX protocol), and remote terminal access via ssh. If the clients are Unix-based, then sshfs will remotely mount storage from your network anywhere in the world too. There should be a port for OSX.  ssh is THE WAY that Unix systems communicate and that administration is performed world-wide.  Right now, I'm logged into 7 other systems ... all thru ssh.

As for the VPN, I prefer IPSec over L2TP ... can't remember the reasons why now, just that there was something important that IPSec does. Don't recall any specific issues with l2tp - it isn't pptp - which is a good thing. Very few people should use pptp since 2002, well, unless you want the other side to think you don't know they have complete access to your (cough) encrypted tunnel. 

Your dynamic DNS provider needs to point to the WAN IP.  Do all your devices get static IPs inside your network?  I've had issues with netgear routers NOT forwarding ports before.  Also, some ISPs block commonly used services, unless you have a business account. I'm pretty certain they block 3389 to protect people from themselves, the same for CIFS ports.

If you do decide to go with ssh for remote access, [be certain to secure it.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")

So in short, setup ssh and get that working from outside. That will cover all the router and authentication checks. If ssh works, then sftp, scp, sshfs, and x2go will work too.  Then add x2go-server (on the machine inside) and x2go-client on the laptop outside.  x2go as a remote desktop is about 2-3x faster than either VNC or RDP.  Just follow the instructions and use the PPA for the packages.  No remote desktops work with DEs that need HW accelerated GPUs, so you'll need to avoid Unity/Gnome3 ... basically, use LXDE, XFCE, KDE or some pure WM as the desktop.

Bam. All your access needs are solved.  If you want to run a VPN inside the house so you can forward all your smartphone traffic through it instead of trusting open wifi, great - openvpn is the well-known solution for that and deployed worldwide by organizations of all sizes.

Of course, you can elect to go in the same direction you are headed if you like. Someone else will need to help.

Hey mate so i have had a chance to go through the installation instructions and it seems i have created a public and private key for the ssh pointing to a completely different port but editing the sshd_config file. 
The private key i have copied over to my mac laptop and have copied it to the key chain using the below instructions:

[https://wiki.hpcc.msu.edu/display/hpccdocs/Adding+a+Private+Key+to+Your+Mac+OSX+Keychain](https://wiki.hpcc.msu.edu/display/hpccdocs/Adding+a+Private+Key+to+Your+Mac+OSX+Keychain)

Do i still have to keep the key file in the documents folder if i have copied it to the key chain?

To access the server from outside the home do i just use 'my_dnsaddress.com.au: port number forwarded'?

Yep ok officially confused. The public and private keys saved in the home directory under my username. I copied the private key to the mac and used the above method. I can't find it in the keychain though? Do i need to copy the public key to the /etc/ssh/ directory? I think they key is confusing me a little. 

The blog is also down mate so i haven't completed all the instructions as of yet.

Thanks for your help mate :)

---

### Post by TheFu on 2016-07-14
The client should make the ssh keys, not the server.
The client should use ssh-copy-id to push the public key to the server.
Using different ports has ZERO effect on the keys. Doesn't matter.

I don't know anything about OSX. Had a Mac for a few weeks and gave it back. Too restrictive for me, just glad it wasn't thrown against the wall over frustration and ruined. That was really close to happening. I can see why people love them - consistency, just consistently WRONG for my expectations and desires.

As far as my site being up/down - been having ISP issues the least month. Finally have enough proof of the issue that they will do something. Been capturing data since Monday. For the last decade it has been very solid (business connection with multiple static IPs). Prior to that, I had a fairly solid residential connection.
```
$ internet-up-summary.sh 
 Period 20160709-094101  - 20160714-084211
  Total % Down Time: 15.74 
  Total Down Time (min): 1126 
  Total Down Time (hrs): 18.77 
 Currently: UP

```
But this thread is about your issues, not mine. We all got issues. ;)

---


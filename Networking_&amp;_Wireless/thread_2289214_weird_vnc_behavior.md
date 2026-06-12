---
title: "weird vnc behavior"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2015-08-02
I have 17 computers to do and have a weird issue in about half of them even tough I think I set them up exactly the same. On the problem computers, all running xubuntu 14.04 (including the computer I am sitting at) this happens:
 
Within the  LAN I can  VNC connect, disconnect, connect etc anytime. Over a WAN I can VNC connect once, then server fails after one disconnect and I can't get back in over VNC WAN until the computer is rebooted. This must be a misconfig somewhere. I am quite sure the router isn't the issue as I can always get in once over WAN.

---

### Post by TheFu on 2015-08-02
Just curious - how did you set them up to be identical?  Ansible, puppet, rsync?

Have you stopped the VNC service after the issue and restarted it?

I assume the WAN connections are through an ssh tunnel for security, yes?  Might be good to force all VNC connections through ssh by using the vncserver --localhost option. Having passwords transmitted in plain text on any network is scary.

---

### Post by cmcanulty on 2015-08-03
no they aren't through a ssh tunnel because I have never got ssh to work remotely even though I have read numerous tutorials. I can get ssh to work in the LAN  within a terminal  but can't get it to ssh with a vnc in the LAN even though again I have studied it a lot. how do you start and restart the service if you can't connect? I do have the forever and share options set in x11vnc.config. I would love to use a ssh tunnel but can't make it work I have to connect to a remote router ip address and then to a specific port for each xubuntu computer. I give remote live support so if I help someone on a live computer then close the session I can't reconnect until the remote one is restarted which I can't do because I can't connect. I have googled forever to find a way to not stop x11vnc on disconnect but no luck except one machine which always works.I copied all the x11vnc options on that one to others but that doesn't make them connect after a disconnect.

---

### Post by TheFu on 2015-08-03
> **cmcanulty said:**
> how do you start and restart the service if you can't connect? 


You use ssh.  IMHO, THAT should be the first thing you fix.  Trying to manage systems with point-n-click is just crazy.

Just so we are clear - you are allowing VNC to be accessed over the internet without a full VPN or ssh tunnel????!!!!!!

---

### Post by cmcanulty on 2015-08-03
I need to see the desktops for our patrons to call me and I interact with them and help them through whatever they are having problems with. If I could ever get shh to work over a WAN with VNC I would surely do it. I can vnc in and then ssh to computers but every tweak I try to get in with a ssh tunnel gets a hostname not known. I have all the proper ports and firewalls and openssh installed and operating. I can'y ssh to other computers with VNC either,that always returns can't open display :0. Believe me I have spent hundreds of hours trying to get this to work. rdp is an option too but that will never connect.

---

### Post by weatherman2 on 2015-08-03
How about setting up a VPN, so you can connect to your network securely?  VNC itself is not encrypted (only the passwords are).

That would solve your "can't connect over WAN after one connection" issue too, because a VPN puts you on your local network, so you are in effect connecting over LAN.

I use OpenVPN with certificates.  You can install it on one Ubuntu computer or even on your router/firewall if it has DD-WRT or Tomato firmware that supports it.

---

### Post by cmcanulty on 2015-08-03
I will try that but I just made a huge breakthrough. After reading and installing x11rdp it suddenly works. I guess xrdp in the repositories is messed up as I have tried that with various tweaks forever. Thanks I will look into openVPN also.
[http://scarygliders.net/2014/03/19/x11rdp-o-matic-version-3-10-released/http://]("http://scarygliders.net/2014/03/19/x11rdp-o-matic-version-3-10-released/http://")

---


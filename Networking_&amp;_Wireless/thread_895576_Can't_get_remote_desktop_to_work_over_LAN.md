---
title: "Can't get remote desktop to work over LAN"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by naiku on 2008-08-20
I am 100% new to Ubuntu, and while it feels strange trying to learn a new operating system, its at the same time interesting. My first problem I have run into is getting remote desktop to work over a LAN.  

I have configured the remote desktop on the Ubuntu machine, and installed RealVNC on my XP laptop. When I try to connect I get a message "unable to connect to host: Connection refused (10061)" I can ping the Ubuntu machine from my laptop, but cannot get the connection to work. I am only (at this point) trying to connect on my LAN.

2nd - When I am working from home I use Juniper Network Connect to connect to the office, when I am connected using this I get even less of a response to remote desktop, and can't even ping the Ubuntu machine. What do I need to do in order to be able to remote into the Ubuntu machine when connected to the office? 

3rd (and final, for now)........ if I want to remote in over a WAN do I simply need to open port 5900 on my router and point it to the IP of the Ubuntu machine?

Thanks.

---

### Post by Sooner Al on 2008-08-20
When you try to connect over the LAN from another PC on the same LAN are you using the private LAN IP of the Ubuntu VNC host? Calling a PC from another PC on the same LAN using the public IP address of your router is not supported by many consumer grade routers.

If your running a firewall on the Ubuntu machine then you need to allow TCP Port 5900 traffic through it.

Is Juniper a VPN? If so its possible the network administrators at work have configured your Juniper client to force all traffic through the VPN as a security measure. That can be done on the server side or the client side. I would talk with them about that issue.

Yes, open TCP Port 5900 and forward that to the static LAN IP of the Ubuntu machine.

---

### Post by naiku on 2008-08-20
Hi, thanks for replying, yes I am using the private LAN IP of the Ubuntu host. As far as I know I am not running a firewall on the Ubuntu machine (like I said, I have never used it before) but I don't know how to check.

I found something about installing Firestarter and opening port 5900 there on another thread, but when I try to install Firestarter I get an error message (can't remember what off the top of my head). Is there an easy way to find out if I have a firewall installed? there is nothing under the System menu. 

Yes, Juniper is a VPN solution, will talk to IT at work. Thanks.

Thanks again for the reply.

---

### Post by naiku on 2008-08-21
Ok, so I still can't get this to connect. I opened the viewer on the Ubuntu PC and tried to connect to localhost, but could not connect here either. So figure that there must be something on the Ubuntu PC blocking the connection, I installed Firestarter and set it to allow VNC ports 5800-5900, but still no luck in connecting remotely. 

Any other ideas? I have the port open on my router, open in Firestarter yet still can't connect. The other thing I noticed is that in Firestarter the "Apply Policy" button is always greyed out and I am unable to click on this button.

---

### Post by Sooner Al on 2008-08-21
Which version of VNC server are you running on your Ubuntu host? Are you sure its running? I don't have a VNC server installed at the moment so I can't test on my machine.

As far as Firestarter is concerned go into the **Perferences -> Interface -> Policy** window and **check** the **Apply policy changes immediately** checkbox then click on **Accept**. That way any changes you make will take effect immediately.

---

### Post by Sooner Al on 2008-08-21
OK...

I configured the GNOME Remote Desktop (VNC) server package on my Ubuntu laptop and configured the firewall via Firestarter to allow TCP Port 5900 traffic incoming. See the screen shot...

[IMG]http://theillustratednetwork.mvps.org/ScreenShots/VNCPolicy.jpg[/IMG]

Everything worked as advertised when I installed a free RealVNC viewer on my wife's XP Pro desktop and connected. If I remove the incoming VNC rule in the Ubuntu firewall the connection fails with a timeout error 10060.

---

### Post by Sooner Al on 2008-08-22
You also may be interested in this old thread concerning your original error message...

[http://www.realvnc.com/pipermail/vnc-list/2004-August/046401.html](http://www.realvnc.com/pipermail/vnc-list/2004-August/046401.html)

---

### Post by naiku on 2008-08-22
Thanks again for the help, I have not had any time yet to give it another shot, I Will probably spend some time tomorrow trying to figure it out. 

I am not sure which version of VNC server is running, I basically completed the settings under the System > Preferences > Remote Desktop and Firestarter on my machine looks the same as the screenshot you provided. I will double check on the Apply Policy Changes Immediately setting when I get the chance.  

Its bugging me that I can't get it to work, I have a decent knowledge of Windows and its very weird starting from scratch, even though I feel like this should be something simple to configure. 

Thanks again, will post a reply if and when I get it working.

---

### Post by timcredible on 2008-08-22
if you can't get vnc working, click on the link in my sig for a how to on using xdm

---

### Post by Sooner Al on 2008-08-22
FWIW here is how I have my VNC server configured for the test. Your using, or trying to use, the same VNC server. When I address the server/host from my wife's XP desktop I use the local LAN IP of the Ubuntu laptop.

[IMG]http://theillustratednetwork.mvps.org/ScreenShots/RemoteDesktopGeneralPreferences.jpg[/IMG]

[IMG]http://theillustratednetwork.mvps.org/ScreenShots/RemoteDesktopAdvancedPreferences.jpg[/IMG]

Good luck...

---

### Post by naiku on 2008-08-23
Got it working, thanks for your help Sooner Al.... I took a look at your screenshots of how you have VNC configured, the only difference was that I had the box "Only allow local connections" checked, as soon as I cleared that box it worked.

Not sure why that made the difference, but for now its working, and thats good enough for me. Now to start figuring out some more things (like why I can't get Realplayer to play music from a website). Thanks again.

---

### Post by GiveLove on 2008-09-09
I was having similar problems connecting "Remote Desktop Viewer" between two Ubuntu 8.04 computers on a local area network also. This thread pointed me in the right direction. 

Besides going to "System--> Preferences--> Remote Desktop" and check marking "Allow others users to view your desktop". I made a new inbound policy in "Firestarter" to allow port 5900 to the local IP of each computer. In theory this should have been successful at this point. 

But naiku thankfully pointed out in the prior post that it worked by un-check marking "Only allow local connections", even though my two computers are on a local network. This was the exact same solution that allowed me to use the "Remote Desktop Viewer" successfully. It must be an unresolved bug in the program. Thank you naiku! :)

---


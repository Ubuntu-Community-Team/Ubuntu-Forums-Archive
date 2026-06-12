---
title: "Get Ubuntu to Reverse VNC into Windows."
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by rmconard on 2008-05-02
First off, let me start my saying I am brand new to Ubuntu. I am a hardcore Windows user but am slowly making the transition. I'm an IT Technician for a major hearing aid company in Florida and we're trying to switch our network over to *nix to save on money and also stop the annoying Windows problems that continue to persist.

At my work, I am required to connect remotely to computers in the field to fix problems. We have 2 types of connections... DHCP and PIP. For our DHCP connections we use Windows NetMeeting and we have the user in the field initiate the connection to us, because of their firewalls and routers in the center. For our PIP users we use VNC and we initiate the connection to them.

So it's pretty simple... but then the Network Administrator came along and said we need to try to switch some of the computers in our centers nationwide over to Ubuntu.

At first I thought it couldn't be done. If we issued Ubuntu to all of our PIP users then we could do it, because a Windows machine CAN connect to a Ubuntu machine using the Xvnc server. This is easy.

The problem is that our DHCP users MUST be able to initiate a connection with us because of their routers. VNC is out of the option for DHCP users because you have multiple computers sharing a single static IP. Port mapping is out of the question because the IT Department here does not configure the routers. So I was forced to find something similar to NetMeeting that would work with Ubuntu. I searched and searched and searched and found nothing but tips, hints, and tricks... finally, I pieced them all together and came up with this:

**-- THE SUPER UBER-SPECIAL WAY TO INITIATE A REVERSE VNC CONNECTION WITH A WINDOWS XP MACHINE SO THE WINDOWS XP MACHINE CAN CONTROL THE DESKTOP OF THE UBUNTU MACHINE --**

(p.s. That's a patented title, so no touchy)

Anyways.. here's how I did. Follow this and you should be good.


1) Go on your Windows machine and set your VNC Viewer to "listen" mode. This can be done through the Start menu under the RealVNC menu. 

2) Go to your Ubuntu machine and open up the terminal window.

3) In the terminal, type in **sudo apt-get install x11vnc**. Then type your password for sudo.

4) Let it install and type **yes** if it asks you to.

5) When that's done, close the terminal window and go back to the Desktop.

6) Right-click on the Desktop and click **Create Launcher...**

7) Inside that window, choose the Type that says **Application in Terminal**.

8) Name it whatever you want, i.e. My VNC Connection.

9) For the Command, type in **x11vnc -connect WINDOWS_IP:5500** - *Note: Replace WINDOWS_IP with the external (or internal, if in a network) IP address of the Windows computer you want to have control your Ubuntu machine. Also note that port 5500 is the STANDARD, DEFAULT listening port for VNC. If you changed this port on the Windows computer, then it needs to coincide here. 

10) Once you have all that in, click Ok and you'll see your new Reverse VNC launcher on your desktop.

11) Double-click on your newly created launcher and you will notice that (if your watching your Windows computer) a new VNC viewer will pop up on your Windows machine. You just started the Reverse connection and now you can control that Ubuntu machine with Windows VNC.

Cool, huh?


If there are any problems, let me know...

---

### Post by rmconard on 2008-05-02
BTW...


Sorry, I kind of posted this thinking like an IT guy. For those novice users out there, you'll want to make sure that there is no Windows Firewall running and that your connection between the Windows machine and Ubuntu machine is open. Any port forwarding, routing, firewalls, etc, etc.. that are in between may get in the way unless you remove/disable them.

Have fun.

---


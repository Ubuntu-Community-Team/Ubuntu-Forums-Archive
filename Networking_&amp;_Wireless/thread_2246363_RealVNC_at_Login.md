---
title: "RealVNC at Login"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by ryan114 on 2014-09-30
So I have ditched Windows as my main OS and now use Ubuntu 14.04.
I have gotten to grips with most things, driver installs and specific software packages for my needs etc but RealVNC Server continues to be the one thing holding me back.

In Windows I am able to access my RealVNC at Windows Login screen, thus meaning I can reboot my PC from work for example then just connect back and enter my windows password and continue doing anything I require.

However with Ubuntu I have not been able to do this, Only by logging in to my GUI then starting the server can i then access my RealVNC.

This is how I installed my package from within Ubuntu GUI.
Open terminal
sudo dpkg -i VNC-Server-5.2.1-Linux-x64.deb

After this installs i then navigate to the menu within gnome to launch the server gui, set it to VNC password, alter port to 7001 etc and then I am able to connect without issue.

So my question is how to get this to start at the login screen so I do not need to be at the PC to login to start the service, because right now the only reason I have Windows is because I have been unable to resolve this.
I also use gnome-session-fallback

---

### Post by TheFu on 2014-09-30
VNC is NOT secure and should never be used without a full VPN or at least an ssh tunnel where all the traffic goes. This applies to any platform and for RDP too.

Or ... for Linux remote desktop needs, use FreeNX or x2go clients and servers.  Both are based on NX, which is easily 2x faster than either VNC or RDP and the protocol uses ssh tunnels automatically.  Using a non-Unity desktop is very important. Excellent that you've discovered that.

On the LAN, there are easier ways to remotely control other systems. This assumes a trusted network with 100BT networking. [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)  I'm only sharing this due to the bean count.  X/Windows has supported remote GUI applications for ... perhaps 30+ yrs.  Again, this only works well where bandwidth is sufficient.

Oh - and try to avoid installing programs using .deb files. This breaks all the great things about package managers on Linux.  This isn't Windows and shouldn't be treated that way. Use the package manager, Luke.  [http://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop](http://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop) is a little old, but still relevant for most things (just not virtualization).

---

### Post by ryan114 on 2014-09-30
Thank you for the information, I do run a VPN, however SSH keys and most of the above is new to me and I will need to learn a lot :)
Any links to clear cut tutorials appreciated :)

---

### Post by slickymaster on 2014-09-30
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by weatherman2 on 2014-09-30
I use the built-in "Desktop Sharing" feature of Ubuntu desktop - which you can access via VNC clients like RealVNC.  I don't have any other VNC server installed.  "Desktop Sharing" isn't perfect, but it works for me.

I have my Ubuntu servers set to login to the desktop automatically upon boot, so I don't have the issue of needing to login manually.

---


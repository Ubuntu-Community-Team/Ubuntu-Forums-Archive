---
title: "Controlling server from another desktop"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by baltadt on 2009-12-20
Title says it all. I need a program that will allow me to control my server from another computer. I don't keep a monitor hooked up because I want the extra room. I looked around on Google but could not find an answer. Please help.

---

### Post by srt4play on 2009-12-20
If your server has a gui installed, then vnc or nx.  If not, then ssh.

---

### Post by marcosamson on 2009-12-21
can you teach how to do what you suggest? in windows, i don't know how to configure windows remote desktop, but i use teamviewer. teamviewer has almost no configuration....

---

### Post by diablo75 on 2009-12-21
VNC is an open-source remote desktop control program that runs on more or less every OS platform you can think of.  It is split into two parts:  The Client, and The Server.  The Server is any computer that you wish to remote into, and the client is the computer FROM which you use to connect to the server.  These terms and the software can be interchanged depending on your physical location and which computer you need to access.

The first thing you'll have to do is enable or install a server-side service to listen for inbound connection requests.  VNC listens on port 5900 by default.  In Ubuntu, you can enable remote desktop accessability through the System>Preferences menu (or maybe it's System>Administration>Remote Desktop, I can't remember; not using Linux at this moment).  Once in there, you just enable it and I would highly recommend you secure the connection with a strong password (so a hacker doesn't sniff this port and gain unrestricted access to your machine).

Next is the networking aspet of the Server-side.  If you have a computer directly connected to the Internet (and is not behind a router) all you need to know is the IP address.  If the computer is behind a router, you will have to configure the router to forward incoming traffic addressed to port 5900 to be forwarded to the correct PC (Port Forwarding).  You can visit [http://portforward.com/](http://portforward.com/) to get a tutorial with pictures of how to configure your router if you have one.

Another thing you'll want to do (if you have a router) is setup Dynamic DNS redirection with [www.dyndns.org](www.dyndns.org).  If you have a router, the external (Internet) IP address it is being given is assigned by your ISP, and it can change without notice.  So if you logged in via your IP address one day, it might not work the next if the address changes on you and you didn't know it changed.  So instead of using an IP addres, you can use a web address that will redirect your client to the correct IP address because your router updates a dyndns server informing it what it's current address is at all times.  Your IP can then be replaced with an easy to remember hostname, like "johnscomputer.homeip.net"

That takes care of the Server side.  You can connect to it using any client you wish.  There are several to pick from for all operating systems.  TightVNC or UltraVNC are good clients to use if the client is Windows.  If you're using Ubuntu, x11vnc is a great viewer.  Server software for Windows come along with TightVNC and UltraVNC, it's just a matter of setting them up to function as constantly running services so they're always on and listening.  In Linux, it's just a matter of enabling Remote Desktop access as mentioned earlier.

You can also use Reverse VNC connectios to make it easy for someone who is not tech-savvy to "throw" their desktop to you.  This works great for people who need help and are behind a firewall.  Google "Reverse VNC" to learn more about this.

---

### Post by Iowan on 2009-12-21
[https://help.ubuntu.com/]("https://help.ubuntu.com/") has several pages that may be of use. Use its Search option to look for information on VNC, VPN, SSH, etc. It'll pay dividends in the long run...

---

### Post by ubudog on 2009-12-21
I would recommend ssh.  Here is a little more info: [https://help.ubuntu.com/community/SSH]("https://help.ubuntu.com/community/SSH")

---


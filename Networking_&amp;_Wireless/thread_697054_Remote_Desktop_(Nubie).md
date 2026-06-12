---
title: "Remote Desktop (Nubie)"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by dj_padawan on 2008-02-14
Hi all, let me start by saying I've been playing with Ubuntu for about a month now so my experience is pretty limited.  I started using Ubuntu because I had an old Dell Laptop running XP that was becoming slow and unusable.  I figured I would give Linux a try before sending it to computer heaven.  To my surprise it ran great and was like a using a bran new computer.

Anyway, I am turning others on to using Ubuntu as well and I'm trying to figure out how to setup Remote desktop so I can provide support.  The people I'll be supporting have very little computer know how and it is usually with Windows so getting them to configure things on their end after I've given them their new OS is out of the question.  I have setup remote desktop on the systems but I'm not sure how I'll be able to connect to them once they leave my house.

I've been told by a friend who is a network engineer that I need to setup a VPN but I would like to try and avoid having to buy a router for everyone.  Any help or HOWTO would be great.

Thanks

---

### Post by ayenack on 2008-02-14
Hello dj_padawan and welcome to Ubuntu.

take a look at this it will show you how to setup Remote Desktop on Ubuntu.

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)

Before doing this look into the security issues that can occur when using remote desktop. May be better to use VNC or SSH with X forwarding to help your friends.

Good luck.

Edit:
May also be wise to install a firewall and config it so that only you can connect from your IP if it's static. Best firewall for this would be Firestarter.

**sudo apt-get install firestarter** (to install Firestarter on a system. Look into the documentation for config options. Documentation is available at the bellow address.)

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by lawentzel on 2008-02-15
Here is my suggestion.  I've gone to a site [http://www.logmein.com](http://www.logmein.com) and set up my aunt on there.  This allows you to access the computer remotely through your browser and JAVA.  You can log in using your Linux system.  You don't need to know the customers IP address.  So long as they have internet access you will be able to see if their computer is up and connected.  I suppose the only thing you would want to do business wise to cover your rear, is tell them it is on there.  Finally, when you log on, they can see you take control of the computer.  So it isn't a surprise.  They offer a free account which works perfectly for me.

---

### Post by Lars Noodén on 2008-02-16
Run [krfb]("http://docs.kde.org/stable/en/kdenetwork/krfb/")  on the machine you wish to connect to and then run [krdc]("http://docs.kde.org/stable/en/kdenetwork/krdc/") to connect to it.  These will allow you to show or control the desktop, mouse and keyboard input.

Usually they are under the "Internet" submenu.

These use VNC or RDP, so you can use other programs to connect, just as long as these use the same protocol.

---


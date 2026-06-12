---
title: "Setting up dial up connection in edgy"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by HgBoy on 2007-06-10
I am trying to setup a dial up connection in 6.10. Everything is enabled and all of the correct isp information is correct. How do I actually get it to "dial" out to the internet? I read about the gnome ppp manager, but I need it to get connected to the internet to install that. The computer is my dad's and he is nowhere near an edgy cd or an ethernet connection, so he has to get it setup first to get the gnome ppp app.

---

### Post by HgBoy on 2007-06-10
[http://www.kcore.org/?menumain=4&menusub=1](http://www.kcore.org/?menumain=4&menusub=1)

under modem, this looks like what I would need to do to setup my dial up connection. I dont know how to do the majority of this. like setting up the daemon?

---

### Post by xDaveManx on 2007-06-17
I am no expert, but I have been poking around the forums looking for ways to connect via dial up for my mom's old computer.

GnomePPP is apparently just a graphical frontend for the command ```
wvdial
```

If you open a terminal and run that, I think it should dial you into the internet if all your other settings are correct.  Then you can go get GnomePPP;)

Hope this helps.

---

### Post by faithsnathan on 2007-06-20
> **xDaveManx said:**
> ```
wvdial
```If you open a terminal and run that, I think it should dial you into the internet if all your other settings are correct.  Then you can go get GnomePPP;)

Hope this helps.


[FONT=Century Gothic][SIZE=4][COLOR=DarkRed]Thank you for the tip.  I'll try it tonight when I get home.  It is very *stupid *that dial up is so hard to get to work when there are some people like me who have to use with no broadband available in my area.  :([/COLOR][/SIZE][/FONT]

---

### Post by Bartender on 2007-06-20
Hey, guys -
I just tried something today.  Gnome-ppp can be downloaded to a Windows PC, burned to CD, and added to a new Ubuntu install.
[http://ubuntuforums.org/showthread.php?t=479663&highlight=dial-up](http://ubuntuforums.org/showthread.php?t=479663&highlight=dial-up)

As DaveManx said, gnome-ppp gives you a fairly straightforward interface.  It doesn't solve your problems if you have a winmodem that doesn't communicate with Ubuntu.  However, with a used US Robotics serial external modem (ebay) gnome-ppp, and a cooperative ISP you should be able to get online.

ISP.com, TotalSpeed, Copper.net are examples of Linux-compatible ISP's.  Juno is a great example of a non-Linux friendly ISP.

---


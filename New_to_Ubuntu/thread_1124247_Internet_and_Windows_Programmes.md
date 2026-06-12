---
title: "Internet and Windows Programmes"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-13
I am a complete novice at Ubuntu, never used it before. I've installed it once, within Windows. Now I plan to make it my primary os. 

I need help on how to use the internet. I use a D-Link Wireless ADSL2+ Router. It is plugged into my computer by a lan cable. Please help telling me about installation details etc.

Also, I want to run programmes like Adobe CS 3 on my computer, as I am a graphic designer and I much prefer this rather than GIMP. I also want to run Winamp, utorrent, Dreamweaver etc. Is there any way that I can run these?

If not, then I will just have to use XP instead. So please help.

---

### Post by adw on 2009-04-13
Hi,
I don't know about your network setup, but you say it's connected via cable it should work right out of the box.

As for the Adobe software, you can install them through Wine [http://www.winehq.org/]("http://www.winehq.org/").
Either by downloading wine as is, or through the Ubuntu installation system Synaptic.
```
sudo apt-get install wine
```

---

### Post by ianhaycox on 2009-04-13
Using a wired connection, 99% of the time just works without special configuration, drivers etc.

In order to run Windows applications within Ubuntu you should investigate Wine, [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) However before switching completely I would suggest installing Wine in your current installation and checking Dreamweaver/Photoshop work as expected within Wine.

This may also help [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by kevmitch on 2009-04-13
> 
I need help on how to use the internet. I use a D-Link Wireless ADSL2+ Router. It is plugged into my computer by a lan cable. Please help telling me about installation details etc.


Under normal circumstances using a LAN cable should work out of the box. What does the Network Manager icon in the upper right look like? If you have a working connection is should be a picture of two computers, if it's not connected it will probably be some empty wireless signal bars with an "X". What does the menu say if you left click it? Right click it?

What happens if you open up a terminal (Applications->Accessories->Terminal) and type
```

sudo dhclient

```
> 
Also, I want to run programmes like Adobe CS 3 on my computer, as I am a graphic designer and I much prefer this rather than GIMP. I also want to run Winamp, utorrent, Dreamweaver etc. Is there any way that I can run these?


You could give Wine a try for CS 3 and winamp. CS3 was supposed to be one of the reference programs that wine 1.0 was supposed to run well. I have also successfully installed winamp through wine and got it to play fine. That said, you might take a look at audacious as this has the same "look and feel" as winamp and will probably run better on Linux. 

I just tried utorrent on wine, but this didn't work out so well. It installed and ran fine, but it wasn't able to actually download anything. It just gave me a hostname not found error indicating that there is somehow a DNS problem. For Linux alternatives, you might want to look at transmission, or deluge. 

I can't comment on Dreamweaver.

If you find that there are certain windows applications that you simply cannot live without and do not work in wine, you can always run them in a virtual machine. Virtualbox is ridiculously easy to set up with a windows install and everything is almost guaranteed to work unless it needs direct hardware access.

---

### Post by irfan9727 on 2009-04-13
For Photoshop, you can set-up a virtual machine using Virtualbox, then install Windows on it, then install Guest Addons, then install Photoshop on it.
Wine never worked for me :(

---

### Post by nandemonai on 2009-04-13
Photoshop / Dreamweaver use a Virtual Machine.

Everything else, better Linux alternatives exist.

---


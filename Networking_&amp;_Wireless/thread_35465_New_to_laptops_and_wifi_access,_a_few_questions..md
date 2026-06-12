---
title: "New to laptops and wifi access, a few questions."
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by Blob on 2005-05-19
Hello,

I just bought a thinkpad t30 and killed my MS partition and going all out Linux.

I have my first business trip next week and will need to access hot spots for email and internet.

I am thinking of getting an account with Boingo. Can anyone answer the following:

1) How do you find hot spots other than looking at their map and locations: I can't find any program for sniffing out signals. Does the laptop do it automatically or something? Does the OS default to the wireless card when the lan connection if out? Are there any software packages that will do that or is it already part of gnome and ubuntu somewhere hidden in the menus?

2) How will I log into Boingo? When I am near their hot spot will a screen pop up asking me for a password or something? They have a program for all that for windows and do not support linux. What do linux users use?

I am completely new to wifi and almost completely new to linux, so the most basic and simple instructions would be appreciated.

Thanks,

Bob

---

### Post by Zelut on 2005-05-19
[QUOTE=Blob]Hello,

I just bought a thinkpad t30 and killed my MS partition and going all out Linux.

I have my first business trip next week and will need to access hot spots for email and internet.

I am thinking of getting an account with Boingo. Can anyone answer the following:

1) How do you find hot spots other than looking at their map and locations: I can't find any program for sniffing out signals. Does the laptop do it automatically or something? Does the OS default to the wireless card when the lan connection if out? Are there any software packages that will do that or is it already part of gnome and ubuntu somewhere hidden in the menus?

2) How will I log into Boingo? When I am near their hot spot will a screen pop up asking me for a password or something? They have a program for all that for windows and do not support linux. What do linux users use?

I am completely new to wifi and almost completely new to linux, so the most basic and simple instructions would be appreciated.

Thanks,

Bob[/QUOTE]
 Well first you'll need to see if your wireless hardware is supported under linux.  I'm not familiar with your notebook so I can't tell you without doing some research.  You could check out the Wireless resource page for linux ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)) which will have a list of supported drivers & hardware.  Also you could look into NDISwrapper which uses windows drivers... that how I got my emachines notebook to work.

As far as hotspots go the best I could tell you is use the command: iwlist scan which will scan for any wifi broadcasts in range.  This is assuming, of course, that you're wireless is configured & working (which is the 1st key issue).

The OS will not automatically switch between LAN & wifi when one is disconnected.  You'll need to use the 'configure' on your connection to tell it to switch.  Its really pretty simple.  Just switch the 'default connection' at the bottom of the configure window.

As far as boingo is concerned I have no idea... sorry.  I hope some of this other info helped though.  I hope you can get it working.  It felt great for me when I finally made the switch :)

---


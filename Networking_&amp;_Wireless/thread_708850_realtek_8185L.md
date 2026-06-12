---
title: "realtek 8185L"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by outofstep2 on 2008-02-26
Hey guys. I am new to linux and would love some help. I am trying to get the Realtek 8185L wifi card that came with my gateway working. I dual boot vista and ubuntu. Here's were I am at.  I noticed that ubuntu preinstalled the linux 8180 driver for the card. But I was having the same problem as this guy:

[http://ubuntuforums.org/showthread.php?t=416993](http://ubuntuforums.org/showthread.php?t=416993)

and I  had already installed ndiswrapper per the instructions on the ubuntu forums, however there was no XP driver available so I used the Vista driver (which had the same name):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But I couldnt figure out how to get the blacklist to work (blacklist rtl8180) ; so I followed the instruction of the 1st thread, and then added an x to the end of the Essid, and magically I now show an IP and am sending and receiving packets in the Network tools manager.  However, I cannot get any of the programs to work (Foxfire, etc..).  They do work with the ethernet card.  It is showing an IPv6 address in wlan0 (the one receiving packets) and there is an additional wlan0:avahi. I was wondering what i should do. I dont know which one is making it work halfway. I assume its the 8180, but then the IPv6 is throwing me for a loop, because vista is running in IPv6. Any suggestions?

---

### Post by jhetrick62 on 2008-02-27
Vista drivers are very spotty and don't work many times.  To see if your blacklist worked and what driver is still loading try this command:

lshw -C network

If it is not loading the correct driver, manually edit the /etc/modprobe.d/blacklist file.  If it is loading the ndiswrapper and it's driver, then the Vista drivers probably won't work.

Check out this page for the correct winxp driver.  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)


Goodluck,
Jeff

---

### Post by outofstep2 on 2008-02-27
I appreciate the response btw.  Ok, I ran lshw -C network and it showed the driver=rtl8180.  So I wanted to see if I could get it removed so i manually edited blacklist in /etc/modeprobe.d/, this is what i wrote

blacklist rtl818x   (Note: I tried each one alone and the same result)
blacklist rtl8180
#blacklist rtl818x
#blacklist rtl8180

I restart, and it still loads the driver. But here is what i also noticed.  When there isn't a WPA password for the network it sends and receives packets (however it seems to lose alot). But when the WPA password is entered, there is no IP and no packets are received.

I would like to try the windows driver, but i cant seem to get the linux driver to not load at boot. And i looked at the link to realtek, and I think I dl the wrong version, so I am re-dl'ed the 2KXP version.

So I'm stuck. It seems the linux driver is close to working, and I can't figure out how to try the windows driver because the linux version doesnt unload.  Any help would be appreciated.

---


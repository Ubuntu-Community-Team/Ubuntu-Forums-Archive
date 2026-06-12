---
title: "Wifi issues in 16.04 - Possible Workaround"
date: 2016-07-13
forum: Networking &amp; Wireless
---

### Post by speartip on 2016-07-13
From googling, many people are suffering with wifi issues in 16.04. Not being able to connect after install, no wireless after suspend, no wireless after reboot, etc etc..
Some of these issues appears to lie with Network-Manager. The same problems have been noted in Manjaro, but they have a wonderful tool called downgrade, which allows users to roll back to Network-Manager 1.0xx which works well. This cannot be done in Ubuntu which uses the 1.2xx version.
 The workaround for me was to replace Network-Manager with WICD, as per this wiki page:
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
 I have now had flawless internet for 48 hours. The only downside was no network icon in the panel, but I can live with that.
 Hope this may help someone else.

---

### Post by Bucky Ball on 2016-07-19
Worked for me. Thanks. I was having issues with wireless dropping out after suspend. It would say I was disconnected, but I was still connected! Then it would randomly, eventually disconnect. So far so good with WICD. Blast from the past. Haven't used for years and looks fine.

Could you mark this thread as solved, please, as that would help more users. :)

I am using xfce4 not Unity and creating a taskbar icon is as easy as dragging and dropping it on the taskbar. I'm asked if I want to create a WICD launcher and that's that.

Not sure how you go about it in Unity, but shouldn't be that hard to create a shortcut/launcher. I remember on one install a few years ago I had to create a shortcut on a desktop, then drag that to the taskbar. Just thought I'd throw that in in case it helps. :)

* Update: I restarted the machine and WICD had an icon in my taskbar that shows me it's connected! I right click that and I can check connection info. It's different from the program icon I realise I'd created and I've removed that. :)

---

### Post by speartip on 2016-07-19
Checked here. Works perfectly in Xubuntu 16.04, with panel applet included after reboot.

---

### Post by Bucky Ball on 2016-07-19
Good news the icon popped up. :)

I'm liking it so far, and not just because it has fixed my issue. It is simple, discreet, and shows the connection details when you hover the cursor over it, which I like. 

To be specific, when I say I am using xfce4, I am using Xubuntu-core 16.04 customised to my liking (in other words, it's by no means a full-blown Xubuntu install but the Ubuntu kernel, xfce4 desktop environment and the few apps I need/want). 

Cheers and thanks again. :)

---

### Post by speartip on 2016-07-19
> **Bucky Ball said:**
> 

To be specific, when I say I am using xfce4, I am using Xubuntu-core 16.04 customised to my liking (in other words, it's by no means a full-blown Xubuntu install but the Ubuntu kernel, xfce4 desktop environment and the few apps I need/want). 

Cheers and thanks again. :)

Actually i've just done exactly the same thing. Xubuntu minimal from the mini.iso, plus only what I needed. After playing with it a while, I think I will make it my main Desktop rather than stock Ubuntu.

---

### Post by dahumph on 2016-07-19
did not work for me, wifi with wicd still unstable or not working ;(

---

### Post by Bucky Ball on 2016-07-19
That's the way I used to go. Then I found [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") which got me a long way in the right direction I was heading with the mini.iso method I'd previously been using and saved me a lot of time. :)

It's a bit late now, and working up the mini.iso is a fun and educational thing to do, but check the 'communty ISOs' link on the second to last line of the Xubuntu-core link above. 

The mini.iso method with xfce4 and now Xubuntu-core is all I've used for ages, years, on all machines. Love it. (I have it running on my 16Gb RAM, Intel 6700, GTX 9700 audio/video production beast. Rocket-like). :)

Enjoy.

@dahumph: You might want to start a new thread about your issue. Mention that you tried the fix on here and it didn't work. Include a link to this. Good luck. :)

---

### Post by speartip on 2016-07-19
@Bucky Ball.
Interesting links. Have bookmarked for future installations. Thanx.

---

### Post by wmstrome on 2016-07-20
How can you install wicd if you cannot connect via WiFi and you have no access to a wired connection? Also, in
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
the instructions given (which might work if I could connect via a cable) are for Gnome and KDE. Which did people use for Xfce, or did they do something different?

---

### Post by vasa1 on 2016-07-20
> **wmstrome said:**
> How can you install wicd if you cannot connect via WiFi and you have no access to a wired connection? Also, in
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
the instructions given (which might work if I could connect via a cable) are for Gnome and KDE. Which did people use for Xfce, or did they do something different?
Xubuntu uses a lot of GNOME stuff and hardly any KDE stuff that I know of. So my guess is: follow the GNOME instructions.

BTW, there were updates to network manager recently. Don't know if they fixed any of the issues people reported in this thread:```
$ grep " installed network-manager" /var/log/dpkg.log.1 /var/log/dpkg.log
/var/log/dpkg.log.1:2016-06-02 15:08:13 status installed network-manager:amd64 1.2.0-0ubuntu0.16.04.2
/var/log/dpkg.log.1:2016-06-16 05:46:34 status installed network-manager-gnome:amd64 1.2.0-0ubuntu0.16.04.3
/var/log/dpkg.log:2016-07-19 06:59:41 status installed network-manager:amd64 1.2.0-0ubuntu0.16.04.3
$ 
```

---

### Post by speartip on 2016-07-20
vasa1 is correct. The Gnome package is what you need.
If you have no internet connection you will need to download the package from another computer, perhaps onto a usb stick and install it that way. The package can be found here:
[https://pkgs.org/download/wicd](https://pkgs.org/download/wicd)
Remember that although this resolved my problems and others, there are no guarantees without knowing your specific issue.

---

### Post by The Cog on 2016-07-23
Thank you for the reminder about wicd. I had almost forgotten about it (I used it years ago). But with the default Network Manager getting more and more unreliable over the last year or so, sometimes failing to connect and sometimes simply refusing to list any wireless networks at all, this thread nudged me into trying wicd again. What a breath of fresh air it is - easy to use, tells you what it is doing, and reliable.

---

### Post by Bucky Ball on 2016-07-23
This has worked for me 'sort of' I realise. Doesn't seem to be happening as often, but I'm once in awhile offline when I open the laptop lid after suspend. I thought it was cured.

All I need to do is click the WICD network icon in the taskbar (using xfce4) and it reconnects immediately. I can work with that. With Network Manager, I was having to reboot the machine. :|

---


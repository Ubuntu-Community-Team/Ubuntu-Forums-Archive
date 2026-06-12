---
title: "controlling client's xp computer via ubuntu?"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by stock99 on 2006-11-19
HI,

  i just tried the ultravnc 'single click' server which is a customizable exe that you can simply send to ppl how need desktop help. All they have to do is run the executable and my zp computer (with viewer listening) can control ones computer.

  Now i am thinking to migrate to full linux but not sure how do i achieve the same result. Can someone give me some advice?



thx in advance.

---

### Post by dbott67 on 2006-11-19
The UltraVNC 'single-click' does not exist in the Linux world, however, you can write a script to accomplish the same thing.

The first link in my sig has all the details for setting up [Reverse VNC]("http://www.ubuntuforums.org/showthread.php?t=299489").

-Dave

---

### Post by stock99 on 2006-11-21
does it also work even if the remote computer (ie. one sending her/his desktop to me) is running winxp with ultravnc single click? Or any other version of vnc server with single click to run?

---

### Post by dbott67 on 2006-11-21
Yes... any version of *vnc (ultra, real, tight, single-click, etc.} can be send their desktop.  Also any OS (Mac OS 9 & OSX, Windows 9x+, Linux).

At home, I've got Mac OSX, Ubuntu & Windows XP/MCE/2003 computers and can send or receive the desktop.  On my website, I've got a UltraVNC single-click that forwards to my dynamic IP address, which is then forwarded to my desktop PC (multi-boot Ubuntu, Vista Ultimate RTM & XP Pro).  I just set the OS to "vncviewer -listen" mode and I can receive their desktop.

If you run into any issues, just post here.

---

### Post by bmt on 2006-12-02
> **stock99 said:**
> i just tried the ultravnc 'single click' server
[snip]
Now i am thinking to migrate to full linux but not sure how do i achieve the same result. Can someone give me some advice?
I had the same need.  Problem is, UltraVNC won't talk to another vnc viewer.  However, the Ultra viewer works well in wine (I'm using v0.9.26 from winehq) and connects to the remote.exe version of Single-Click.  File transfers also work well.  I haven't used it in anger yet, only on the LAN, but it seems okay so far.

Just put the viewer executable in wine's C:\Program Files and set up a Launcher: <wine "c:\program files\vncviewer.exe" -listen> to start it minimised and listening.  An icon appears in the Notification Area: right-click for viewer options/settings.

There is quite a swell of desire for a Linux version of Single-Click on the UltraVNC forums, so we may have a native client one day.

@OP: BTW, did you post this question on the Whirlpool forum?  I found it while Googling for a solution myself, before I tried wine.  I couldn't post there without the hassle of registering -- a bit OTT for one post -- so I'm pleased to have come across it here.

---

### Post by dbott67 on 2006-12-02
> **bmt said:**
> I had the same need.  **Problem is, UltraVNC won't talk to another vnc viewer.**  However, the Ultra viewer works well in wine (I'm using v0.9.26 from winehq) and connects to the remote.exe version of Single-Click.  File transfers also work well.  I haven't used it in anger yet, only on the LAN, but it seems okay so far.

Sure it does... I use it regularly.  I've got UltraVNC running on my **Windows XP Pro** laptop and **Ubuntu** on my desktop in listen mode.  Running the 'Single-click' from **Windows**, I can connect to my **Ubuntu** desktop PC *[COLOR="Blue"](see screenshot #1).[/COLOR]*

I can also connect from Ubuntu (using vncviewer) to my Windows XP computer running UltraVNC server [COLOR="Blue"]*(2nd screenshot)*[/COLOR].

-Dave

---

### Post by dbott67 on 2006-12-02
> **bmt said:**
> I had the same need.  Problem is, UltraVNC won't talk to another vnc viewer.  However, the Ultra viewer works well in wine (I'm using v0.9.26 from winehq) and connects to the remote.exe version of Single-Click.  File transfers also work well.  I haven't used it in anger yet, only on the LAN, but it seems okay so far.

Just put the viewer executable in wine's C:\Program Files and set up a Launcher: <wine "c:\program files\vncviewer.exe" -listen> to start it minimised and listening.  An icon appears in the Notification Area: right-click for viewer options/settings.

There is quite a swell of desire for a Linux version of Single-Click on the UltraVNC forums, so we may have a native client one day.

@OP: BTW, did you post this question on the Whirlpool forum?  I found it while Googling for a solution myself, before I tried wine.  I couldn't post there without the hassle of registering -- a bit OTT for one post -- so I'm pleased to have come across it here.

Just in case I'm confused about the problem you're facing, I'll tell you how I have **Reverse VNC** configured:

1. I have created an **UltraVNC 'Single-click'** executable using *Dynamic DNS* that points to my home IP.  
2. I have my router set to port-forward 5500 to my Ubuntu computer.
3. I run the following command on my Ubuntu destkop:
```
vncviewer -listen
```
4. Windows users can connect to my PC by going to my website & clicking on the "remote help" link (which downloads the UltraVNC 'single-click' reverse VNC connection).
5. Linux users need to install **x11vnc** and then run the following command:
```
x11vnc -connect myhost.dyndns.org:5500
```

The full **HOWTO: Reverse VNC** is below in my signature.

-Dave

---

### Post by bmt on 2006-12-03
> **dbott67 said:**
> ... connect to my Windows XP computer running UltraVNC server
So can I, using the full server -- but I'm using the SC variant 'remote.exe', which has had many of the protocol support options removed for lightness.  I'm aiming for the simplest XP server launch possible.

My statement that U-VNC won't talk to other viewers referred to the 'remote.exe' server and came from the developer, on the UltraVNC forum (can never find the link when you need it! :rolleyes: )  Anyway, single-click is now deprecated, in favour of PCHelpware, which is not as appealing, so far.  The core will be closed and it relies on DirectX for the viewer functions.

---

### Post by vgsangiuliano on 2007-01-17
Hi I would like to know if it is possible to install ultravnc viewer on ubuntu via apt or wine or compiling sources (if anyone can link me a detailed guide on te web to do this....) because I want to control winpc's in a LAN using ultavnc MSRC4Plugin_NoReg.dsm plugin to crypt communication between pc's and using vnc "default" software in ubuntu can't allow it.
I know that I could tunnel vnc communication via ssh using the ssh server installed on my sme server that controls the lan but I don't want to overload my server which is very poor in cpu.
Can anyone help me?
The only thing is to be able to install ultravncvierwer on ubuntu, I don't won't to install an image of windows using VMware only to run ultravncviewer!!!
Please forgive my bad english, I'm italian.
thanks

---

### Post by dbott67 on 2007-01-17
You can try running UltraVNC Viewer using Wine, although the MSRC4 plug-in does not appear to work:

[http://forum.ultravnc.info/viewtopic.php?p=31633](http://forum.ultravnc.info/viewtopic.php?p=31633)

One of the things I've noticed is that you must run it as root (i.e. **sudo wine vncviewer.exe**)

The other DSM plug-ins that may be compatible with Wine are here:

[http://msrc4plugin.home.comcast.net/index.html](http://msrc4plugin.home.comcast.net/index.html)

Hope this helps.

-Dave

---


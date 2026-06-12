---
title: "LiveCD has no menu bars"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Acharn on 2009-01-17
I just downloaded and burned the iso for the 8.10 live cd. I want to try Ubuntu out, and I DO NOT want to install it at this time. I have an Acer Aspire M1610 with a Radeon X1550 graphics card. I have a 19 inch monitor which under Windows shows 1440x900 pixels. When I boot from the CD I get the desktop wallpaper, but there is no login prompt. There are no menu bars. There is nothing on the desktop but the wallpaper.

Because I used to administer a FreeBSD system, I just started playing around and found that hitting <Ctl><Alt><BkSp> shut down the X server (as it should) and immediately brought up a new desktop which DOES give a login prompt for user ubuntu, which is logged in automatically after 5 seconds. After more fiddling around I was able to type in the user name before the automatic login and *did* get one menu bar, at the top of the screen. It's hard to be sure, because the wallpaper is so dark, but it looks like there's no graphic display at the right one quarter or so of the screen. After still more fiddling around I managed to get the menu bar populated with some icons and was even able to start up Firefox. It looks awful, but at least it works.

I have a feeling the problem is with the X server not correctly detecting the video card. I managed to find a thread which described how to install the ATI binary driver, although it indicated the X server **should** properly detect the card by default. Unfortunately, the instructions included using apt-get to install the driver, and I don't see how I can do that with a CD. I emphatically DO NOT want to install Ubuntu on my hard drive. What options do I have?:confused:

---

### Post by grekei on 2009-01-17
How much Ram are you running.I have had problems similar with live CD's and have found anything under 1Gig is horrible because it has to hold so much in Ram or in a swap partition(very slow).Have you done a MD sum check on the CD to see if its not the disk itself.
Only other suggestion which may work if you don't want to install but really want to give the system a workout(the CD is way too slow even with plenty of Ram) is install "Virtual Box" or similar and install Ubuntu as a guest system.It does not sit on your HD and you can delete it with 1 click.

Hope this helps, Cheers

---

### Post by minsf on 2009-01-17
to get the panels and the "trash bin" corner, maybe you can do atrl+alt+f1 and run "gnome-panel" from the cli and then "exit" back to gnome.
(by the way, ctrl+alt+backspace RESTART the X, not shut down)

---

### Post by Acharn on 2009-01-18
I've got 1 Gig of RAM. I suspect I need to edit Xorg.conf, but don't know how to do that on a CD-R.

The "Virtual Box" idea sounds intriguing. I haven't played with virtualization before; maybe this is the time to start learning.

---

### Post by Acharn on 2009-01-18
> **minsf said:**
> to get the panels and the "trash bin" corner, maybe you can do atrl+alt+f1 and run "gnome-panel" from the cli and then "exit" back to gnome.
(by the way, ctrl+alt+backspace RESTART the X, not shut down)

Hmmm. Really? On my FreeBSD system it always stopped the X server and brought me back to the CLI. I think I tried the ctrl-alt-F1 route without any result, but I'll try it again. It's possible I only hit alt-F1, or maybe ctrl-F1 (which I know is wrong). Thank you for the suggestion.

Maybe this is just a hardware problem. I have to say I'm not happy with the Acer machine I got; it has USB 1.0 installed, and I hate the way I have to uninstall the ATI drivers to install an upgrade. On the other hand it works fine for what I mostly want to do which is surf the internet and play games -- most of which probably wouldn't work under WINE, but that's another discussion.:)

---

### Post by theozzlives on 2009-01-18
On the live CD everything is in RAM, and just disappears when you reboot. You can install software, edit conf files, etc. Just remember if you reboot it's all gone. Remember Linux is not UNIX, just very similar.

---

### Post by grekei on 2009-01-18
I run 2 gig of ram and still reckon the live CD is pretty average with that much.
If you want to try a virtual environment as I did (because I needed to run Windows Vista for a course I was doing but did not want it on my hard drive ever again).
 I found "Virtual Box" from Sun Microsystems very easy to use (I knew nothing about virtualisation)its free, well documented and pretty easy to install.
I have had Vista,Open Solaris and various Distros working on it.You can have shared folders so you can access files from the host system,use your normal network connections etc.A very safe way of playing without installing and dual booting.

---

### Post by Acharn on 2009-01-18
> **grekei said:**
> I run 2 gig of ram and still reckon the live CD is pretty average with that much.
If you want to try a virtual environment as I did (because I needed to run Windows Vista for a course I was doing but did not want it on my hard drive ever again).
 I found "Virtual Box" from Sun Microsystems very easy to use (I knew nothing about virtualisation)its free, well documented and pretty easy to install.
I have had Vista,Open Solaris and various Distros working on it.You can have shared folders so you can access files from the host system,use your normal network connections etc.A very safe way of playing without installing and dual booting.

Thanks for the information. As I stated above I haven't yet used virtualization. I have a lot of faith in Sun because of the terrific stuff they put out for Java. I'll check this out.

---


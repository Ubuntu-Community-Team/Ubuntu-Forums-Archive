---
title: "New to Ubuntu. Can't connect wirelessly"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by pounditflat on 2008-08-17
I've done some reading over the past couple of days and as far as I can tell, my Toshiba Satellite a205 s5804 has a realtek RTL 8187B network adapter that is not recognized by Ubuntu. The connection works perfectly with the wire. But I would really like to use it wireless. I can't seem to find drivers for the realtek. Can someone talk me through (if it's even possible?) If it's not possible, is there another option such as Kubuntu? From what I've read, it looks like it may work, but I really don't know. If the fix has to be done at the command line, I'll need step by step instructions. Thanks.

---

### Post by Zorael on 2008-08-17
Hmm. The MSI Wind/Advent 4211/Medion whatsitsname models have a  [Realtek **8187SE**](http://www.cisco.com/web/partners/pr46/pr147/realtek_RTL8187SE.html) wireless card, and it seems there aren't any drivers for the 8187xx series in the kernel (yet). Assuming your 8187A can use the same drivers (likely?), there is one you could download and manually compile. I haven't tried this myself yet, still need to resize partitions and install {U,Ku,Xu}buntu.

Please see [http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:). Scroll down to the second option.

You'll need to do this once every kernel update, so bookmark the page. :>

Regarding Kubuntu; the only difference between Ubuntu, Kubuntu, Fluxbuntu, and other *buntus are the set of packages that come installed by default. It's still the same Ubuntu underneath, but the desktop environment and installed programs differ. Again, per default; they all share the same repositories, so all programs can be installed regardless of what desktop environment you're running. So technically, you could install Kubuntu's (KDE's) default file manager and run it in Ubuntu (Gnome). Mix away, me hearties.

By extension, all the flavors are running the same kernel and using the same module packages (same linux underneath), so if a piece of hardware doesn't have drivers in one, it doesn't in the other either.

---

### Post by pounditflat on 2008-08-17
I just found this... is it relevant to my wireless adapter? If so do you think I could do it, since I can't write ANYTHING in command prompt.
Sorry that I am so lame, but if you can help, I would really appreciate it.

[http://forums.msiwind.net/default-msiwind/have-the-wireless-drivers-but-t840.html](http://forums.msiwind.net/default-msiwind/have-the-wireless-drivers-but-t840.html)

---

### Post by dodle on 2008-08-17
You can install the Windows driver with ndisgtk, some wireless cards will work that way (unless it's a broadcom >.<).  Either go into synaptic and install "ndisgtk" or go to a terminal and type:```
sudo apt-get install ndisgtk
```That should also install ndiswrapper.  Next open ndisgtk.  If it's not in your menu:  Go to a terminal and type:```
gksu ndisgtk
```Click "install driver" and find the .inf file for your Windows driver.  If all goes well you should now be able to see wireless networks under your network manager.

Edit: Sorry, I put "sudo ndisgtk", when it's supposed to be "gksu ndisgtk".  "sudo" might work too, I can't remember.

---

### Post by pounditflat on 2008-08-17
thanks

---

### Post by binobooks on 2008-08-17
I am having a problem installing ndisgtk.  when I type inthe code for installing it it says could't find package ndisgtk

---

### Post by pounditflat on 2008-08-17
did you see where the edit was, check the entire post by dodle

---

### Post by dodle on 2008-08-17
> **binobooks said:**
> I am having a problem installing ndisgtk.  when I type inthe code for installing it it says could't find package ndisgtk

You probably need to add a repository to your system.  I'm trying to figure out which repository it is in but I am having trouble connecting to packages.ubuntu.com.  I'll post it as soon as I figure it out.

---

### Post by pounditflat on 2008-08-17
where do I find the .inf file?

---

### Post by dodle on 2008-08-17
If you have it stored on a windows partition, you'll need to access that partition and find it.  But it will probably be easier just to download the driver from the computer manufacturer's website to your system and extract it.  You may need to install wine if the driver comes in a self-extracting .exe.

If you want the newest version of wine you can go to [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") and follow the instructions to add it to your list of repositories.

---

### Post by dodle on 2008-08-17
Pounditflat, I found a link for your driver.  This is from a mirror on RealTek's websit.  [ftp://210.51.181.211/cn/wlan/87B_Mac10.4_v1117.zip]("ftp://210.51.181.211/cn/wlan/87B_Mac10.4_v1117.zip")

Binobooks, [packages.ubuntu.com]("packages.ubuntu.com") still isn't working so I'm not able to look up which repository ndisgtk is under.  I'll try to figure it out by looking through synaptic.

---

### Post by dodle on 2008-08-17
> **binobooks said:**
> I am having a problem installing ndisgtk.  when I type inthe code for installing it it says could't find package ndisgtk

From doing a google search, it looks like you can access it after you enable the universe repositories, which you should be able to do from synaptic.

---

### Post by pounditflat on 2008-08-25
dodle, I've done everything except install wine and find the .inf file to add. Not sure about what steps to take at this point i'm totally lost. Not feeling well at present, will resume work on this realtek issue tomorrow. Thanks for all your help.

---

### Post by pounditflat on 2008-08-27
are you still around. I posted to this and did not hear back from you. I have been out of town for a week attending my grandmother's funeral. But I'm back now and want to try to get my laptop online wirelessly. If you can help it would be geatly appreciated. lb

---

### Post by pounditflat on 2008-08-27
dodle, I've done everything except install wine and find the .inf file to add. Not sure about what steps to take at this point i'm totally lost. Not feeling well at present, will resume work on this realtek issue tomorrow. Thanks for all your help.

are you still around. I posted to this and did not hear back from you. I have been out of town for a week attending my grandmother's funeral. But I'm back now and want to try to get my laptop online wirelessly. If you can help it would be geatly appreciated. lb

---

### Post by panhandle on 2008-08-27
The 8187b is blacklisted, but there are workarounds.

There is a ton of information on the chipset here on this website. perform a simple search and start reading. 

There are tutorials to walk you through the process, but it will take some work.

Good luck.

---

### Post by pounditflat on 2008-09-17
panhandle -what website?

---

### Post by panhandle on 2008-09-17
[http://ubuntuforums.org/showthread.php?t=546663](http://ubuntuforums.org/showthread.php?t=546663)

For starters.

---


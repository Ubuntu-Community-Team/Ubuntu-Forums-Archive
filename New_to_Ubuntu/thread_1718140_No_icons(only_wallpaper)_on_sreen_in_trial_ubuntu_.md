---
title: "No icons(only wallpaper) on sreen in trial ubuntu netbook"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by lumop on 2011-03-30
Hello. I'm using windows vista and have never used any linux distro as an OS but I've been interested in ubuntu for a while. Now i'm ready to finally install it. I used a 4gb usb drive to boot ubuntu netbook 10.10 remix onto my laptop. I clicked "try ubuntu" first to make sure it ran properly on my laptop. It loaded only displaying the default wallpaper, no icons or words. The top and side bars were there but there was nothing on them. When I moved my mouse over to the top bar, I was able to see the menu my mouse was on. When I moved my mouse to the side bar, grey boxes with smaller white boxes in them would appear to the right. When I clicked around there, icons on the bar would be visible for a sec and disappear again. I didn't open anything. Obviously I don't want it to install it like this. If anyone could help me out I would really appreciate it.

Here are my computer specs.

Acer Extensa 4420-5910

4GB DDR2

250 GB HDD

AMD Turion 64 X2 Mobile Technology TL-60

2 GHz

ATI Radeon X1250

---

### Post by waynefoutz on 2011-03-30
I have the same CPU and graphics processor in my Dell Latitude D531. I have a similar experience when I try to run 10.10. 10.04, however, runs flawlessly. I've never tried the Netbook Remix, just the plain vanilla Ubuntu. You can find either version of Lucid here:

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

Lucid is an LTS release, so in the long run you are far better off with it anyway, because 10.10 is only supported for one more year as I type this, while Lucid has 2 more years. 

After the basic install, you are still going to find Ubuntu to run somewhat sluggish. This is due to the fact that when Lucid (10.04) was released, the open source drivers that are installed out of the box, weren't up to snuff yet. There are no proprietary drivers for your graphics card. Meaning, the ones you download from ATI. Don't install those, they will break everything. Instead, go here 

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")
 and halfway down the page, click the link where it says "read about installing" and follow the instructions as how to add this source to your list of software sources. After you do that, you'll get the newer drivers in your update manager. 

Speaking of update manager, before you run all the updates, you might want to heed this warning. The latest Kernels broke my system. The last working kernel was version 2.6.32-25. If you run all  the updates after install, you might get system freezes. I did. To counter this, you need to lock the kernel version, to keep it from upgrading. Instructions on how to do that are here:

 [http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html]("http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html") 

Follow the instructions to open Synaptic package manager, in the "quick search" box, type in "2.6.32-2" and click on the "installed" tab and you should end up with the three files you want to lock. Lock them as described in that last link. When locked, they will turn red. What you'll end up with is this:

[[IMG]http://img850.imageshack.us/img850/2333/screenshotsynapticpacka.png[/IMG]](http://img850.imageshack.us/i/screenshotsynapticpacka.png/)

Uploaded with [ImageShack.us](http://imageshack.us)



Once those are locked, and you add the xorg-edgers PPA to your software sources, THEN do Update Manager, and download the updates. 

Everything will run flawlessly after that, I promise you. Sorry this is such a long and drawn out process, and I hope that doesn't turn you off on Ubuntu. That graphics card you're using is a real pain as far as Linux goes, because ATI no longer supports it. Older versions of Ubuntu ran perfect with it, without the extra gymnastics, but unfortunately none of those are supported any more.

---

### Post by patryk77 on 2011-03-30
Hey!

As far as I know, Unity requires graphic acceleration as of 10.10, which would explain why 10.04 works and 10.10 does not; you might have to install the ATI drivers using the restricted driver manager (which require a reboot, which means you cannot install them on a live cd / test run)

What I would suggest is installing side by side (so you can still boot into Vista), and trying the Gnome Desktop instead of Unity. You can do that from the login screen, at the bottom you have options for language, desktop environment and keyboard layout.

From there, you should be able to install the drivers under System / Admin / Additional Drivers, and be able to use Unity after you reboot.

Personally, I much prefer to use the Gnome Desktop even on a netbook, but I encourage you to give both a try :)

Good luck!

---

### Post by lumop on 2011-03-30
Thanks a lot for all the detailed steps. I'm willing to follow your instructions but on the [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) page there are so many links, I don't know which to download. Can you tell exactly which one? Not sure if it matters but i'm going to be using a ubs again. I don't have a disk.

---

### Post by waynefoutz on 2011-03-30
> **patryk77 said:**
> Hey!

As far as I know, Unity requires graphic acceleration as of 10.10, which would explain why 10.04 works and 10.10 does not; you might have to install the ATI drivers using the restricted driver manager (which require a reboot, which means you cannot install them on a live cd / test run)

What I would suggest is installing side by side (so you can still boot into Vista), and trying the Gnome Desktop instead of Unity. You can do that from the login screen, at the bottom you have options for language, desktop environment and keyboard layout.

From there, you should be able to install the drivers under System / Admin / Additional Drivers, and be able to use Unity after you reboot.

Personally, I much prefer to use the Gnome Desktop even on a netbook, but I encourage you to give both a try :)

Good luck!

System/Additional drivers will NOT find any graphics driver. The only way to install them is to compile them yourself, and they will BREAK your video. From then on you'll only be able to boot into a command line.

---

### Post by waynefoutz on 2011-03-30
> **lumop said:**
> Thanks a lot for all the detailed steps. I'm willing to follow your instructions but on the [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) page there are so many links, I don't know which to download. Can you tell exactly which one? Not sure if it matters but i'm going to be using a ubs again. I don't have a disk.

the netbook edition: 

[http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso]("http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso")


With your setup, I'd go 64 bit. I don't see a link for the 64 bit netbook remix. 

Plain Ubuntu:

32 bit:
[http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso")

64 bit
[http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso")


As for 64 bit and 32 bit, I've had both. I couldn't tell the difference as far as performance is concerned. I started out 32 bit, then all of the sudden.I had the graphics freezes. Everyone online told me to try 64 bit to fix it, so I did. They were wrong and it turned out to be the kernel update.  Which one you use is up to you.

---

### Post by lumop on 2011-03-31
I Booted Ubuntu 10.04 desktop 64 bit on my laptop and it went straight to a trial version. Everything seemed to work well. I clicked install and after I pressed forward on the keyboard layout screen the mouse turned into the white circle, but only while it's over that window. I have the keyboard layout window on these settings  [https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step3.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step3.png)
 
I figured I just needed to wait but it was taking very long. I canceled, restarted the computer and tried again. The trial version still works while the install is running, I'm currently on it. Same thing happened so I thought I would wait longer. It's been on the keyboard layout screen for over 6 hours and still nothing. What should I do?

Edit: I canceled it, shut down, and booted vista. Going to wait for a reply. I'm thinking about just trying the 32 bit version.

Edit: Not sure if the size of my laptop would have anything to do with it. The screen is 7 1/2 tall, 12 wide. My key board doesn't have a number pad on the right.

---

### Post by waynefoutz on 2011-03-31
You have me baffled. If you were typing that last message using the Live CD, yeah I know you were using a usb drive, but still, since you were typing on that, obviously the keyboard is functioning. I'm not sure what would make it hang, especially there. I can make a guess, I just watched a youtube video of someone installing Lucid to jar my memory...The screen after the keyboard layout is the partitioning section, where it first looks at your hard drive. You might want to scan your hard drive for errors with Windows, and defrag it. I'm guessing that's your problem. It could also be the usb drive you are installing it from is bad, but less likely so, since it boots into the live environment. I'm guessing you have a file system error on your drive and need to use Windows Scandisk first. Just a guess. You might want to try the 32 bit as well, if you want.

---

### Post by lumop on 2011-03-31
Thanks for your help. I see what I can do.

---

### Post by cariboo on 2011-03-31
The 10.10 version of Unity is broken on a lot of systems, and has more or less been orphaned, as development on a new version based on compiz, instead of mutter was started last October. There is no longer a separate netbook version, the new version code named Natty Narwhal, will be released at the end of April.

---

### Post by Blasphemist on 2011-03-31
Here is an idea. I haven't done this as I upgraded to Natty and Unity but Unity is working great for me even though it is still beta. Download and make your Natty install from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Boot to this and verify that your video isn't a problem. If not, live a bit on the edge and go for it. I use it on my Toshiba Satellite and Acer add on monitor. During alpha it was quite rocky but now during beta it has been very solid. You'll know from the start if the video will be a problem and if not you'll have the best you can do for your system.

Give it a thought.

---

### Post by waynefoutz on 2011-04-01
> **Blasphemist said:**
> Here is an idea. I haven't done this as I upgraded to Natty and Unity but Unity is working great for me even though it is still beta. Download and make your Natty install from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Boot to this and verify that your video isn't a problem. If not, live a bit on the edge and go for it. I use it on my Toshiba Satellite and Acer add on monitor. During alpha it was quite rocky but now during beta it has been very solid. You'll know from the start if the video will be a problem and if not you'll have the best you can do for your system.

Give it a thought.

I  have the exact same video and CPU as the original poster. His GPU is old and unsupported. I haven't tried Natty yet, but 10.10 was a disaster. It was slow to boot up, and very sluggish, even with compiz turned off. After the install, I'd boot up into a wallpaper, the panels and icons would show up about 3 minutes later. 

It works beautiful with Lucid. 
[http://www.youtube.com/watch?v=vi2UcEPgn50]("http://www.youtube.com/watch?v=vi2UcEPgn50")
As you can see, my desktop effects work fine. Like the OP, I have an AMD Athlonx2 running at 2 gigahertz, and an ATI x1270 graphics chip. We have basically the same rig.

---

### Post by lumop on 2011-04-07
So waynefoutz, I switched my usb and was able to install it. I followed all your instructions from your 1st reply and Ubuntu has been working fine. Thanks a ton for all your help and everyone else for the input. (:

---


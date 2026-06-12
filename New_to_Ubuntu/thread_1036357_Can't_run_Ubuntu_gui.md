---
title: "Can't run Ubuntu gui"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Omegaxis on 2009-01-10
When the gui is loading the progress bar gets to about 95%, and the screen goes black and I see a squished version of the loading screen with alternating white and black lines under it. I think I may need Nvidia drivers (I have a geforce 7600 series card), but I don't know how to install them from the cd in the commmand prompt.
It may also have to do with my screen which has a native resolution of 1680X1050, but I can't change any of the settings in xconfig.


Edit: Pictures are now available on page 4.

---

### Post by joshmuffin on 2009-01-10
Press Ctrl + Alt + F1 that will take you to a command line, login then try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by JoshuaRL on 2009-01-10
> **joshmuffin said:**
> Press Ctrl + Alt + F1 that will take you to a command line, login then try:

```
sudo dpkg-reconfigure xserver-xorg
```

That may not work.  From Hardy on, the new version of Xorg doesn't reconfigure the graphics driver that way anymore.  Instead, get into the VESA driver to get a working desktop (although it will be slow) by doing this from the recovery console:
```

xfix

```
Then from there, go to System->Administration->Hardware Drivers.  It will let you know what proprietary drivers are available.  Activate, and restart.  See if that helps.

---

### Post by Omegaxis on 2009-01-10
> **joshmuffin said:**
> Press Ctrl + Alt + F1 that will take you to a command line, login then try:

```
sudo dpkg-reconfigure xserver-xorg
```

I reconfigured and disabled the frambuffer, but I still get the same result when I try to do a normal boot.

---

### Post by Omegaxis on 2009-01-10
> **JoshuaRL said:**
> That may not work.  From Hardy on, the new version of Xorg doesn't reconfigure the graphics driver that way anymore.  Instead, get into the VESA driver to get a working desktop (although it will be slow) by doing this from the recovery console:
```

xfix

```
Then from there, go to System->Administration->Hardware Drivers.  It will let you know what proprietary drivers are available.  Activate, and restart.  See if that helps.

Ran xfix, still have the same issue. Just for clarity, I can only run xfix from the recovery menu.
Also I get this:
xserver-xorg posit warning: overwritten possibly customized configuration

---

### Post by Omegaxis on 2009-01-10
I've neglected to mention that if I press ctr+alt+f1 when the screen is messed up I get this:

```
kinit: name_to_dev_t(/dev/mapper/ubuntu-swap-1)dev(2541)
kinit: trying to resume from /dev/mapper/ubuntu-swap1
kinit: no resume, doing normal boot
```

---

### Post by The-IRS on 2009-01-10
does your motherboard have onboard video?
I experienced a similar problem with a version of debian (ubuntu is based on it) because I had onboard video and ended up having to use a different motherboard to solve the problem.

---

### Post by Omegaxis on 2009-01-10
> **The-IRS said:**
>  onboard video?


No, I have a PNY Geforce 7600 GS agp card.

---

### Post by The-IRS on 2009-01-10
> **Omegaxis said:**
> No, I have a PNY Geforce 7600 GS agp card.
beats me.

---

### Post by Omegaxis on 2009-01-16
So it seems that nobody knows what to do with this, should I report it as a bug? Could this possibly have something to do with running my video card from an AGP slot? I was also thinking that it may have to do with my monitor's native resolution of 1680x1050

---

### Post by JoshuaRL on 2009-01-16
Do you have the most current drivers enabled?  System->Administration->Hardware Drivers if you didn't already know.

I can't believe i didn't ask that before.

---

### Post by Omegaxis on 2009-01-16
> **JoshuaRL said:**
> Do you have the most current drivers enabled?  System->Administration->Hardware Drivers if you didn't already know.

I can't believe i didn't ask that before.

I can't get that far to check it that way, when I boot I get the loading screen, but it only loads to about 95% and then goes black, after that I get graphical glitch with remnants of the loading screen. all I can do from there is ctrl+Alt+F1 to get to the console. I also have since tried it with an ATI video card, but get identical results.

---

### Post by bailbath on 2009-01-16
I had a similar problem with a laptop resolution and it was the resolution 1680 x 1050 but only had problems with Ubuntu Gnome! When I used PCLinuxOS KDE it was fine! In the end I copied the xorg.conf monitor section from PCLinuxOS to the Ubuntu installed on the laptop via a Live cd of PCLinuxOS.
This may help you or not but it worked for me and is worth a try!
Ian

---

### Post by Omegaxis on 2009-01-18
The problem seems to be that I cannot edit xorg.conf in regards to driver info for my video card. Would Hardy heron possibly remedy this?

---

### Post by Omegaxis on 2009-01-18
Can anyone here help me or am I on my own?

Edit:
Errors in the log
```
Vesa(0): Unable to estimate virtual size
```

and

```
Audit:Client 4 rejected from local host (uid=0 gid=0 pid=5164)
```

---

### Post by JoshuaRL on 2009-01-18
> **Omegaxis said:**
> Can anyone here help me or am I on my own?

Edit:
Errors in the log
```
Vesa(0): Unable to estimate virtual size
```

and

```
Audit:Client 4 rejected from local host (uid=0 gid=0 pid=5164)
```

Well, unfortunately I have no idea what would cause this.  If you don't have any data that you're standing to lose, I would suggest just reinstalling.  Normally I don't like to say that, but it may be by far the easiest thing for you.

---

### Post by Omegaxis on 2009-01-18
> **JoshuaRL said:**
> Well, unfortunately I have no idea what would cause this.  If you don't have any data that you're standing to lose, I would suggest just reinstalling.  Normally I don't like to say that, but it may be by far the easiest thing for you.

I've never successfully started Ubuntu. I've tried reinstalling, but I get the same result. The disk passes the MD5 checksum, as well as the disc's own integrity check.

---

### Post by JoshuaRL on 2009-01-19
> **Omegaxis said:**
> I've never successfully started Ubuntu. I've tried reinstalling, but I get the same result. The disk passes the MD5 checksum, as well as the disc's own integrity check.

Alright, do you want to try burning another disk?  Maybe that will help.

---

### Post by Omegaxis on 2009-01-19
I've tried multiple discs now, but still have the same problem.
I've been poking around at this for about 2 weeks now, and it appears that it has something to do with my screen (
Acer® AL2216Wbd)are there any known issues with this?


I'm fairly certain it's not detecting my monitor (which is DVI) now.
I can't even find the monitor in lshw, or lspci.
I also get a "Cannot open Display" on commands like gedit and xrandr.
Am I really the only one that has had these problems.

---

### Post by Omegaxis on 2009-01-20
Bump

---

### Post by JoshuaRL on 2009-01-20
> **Omegaxis said:**
> Bump

Do you have an old CRT, or something running off of VGA to test whether its the monitor or not?

---

### Post by Omegaxis on 2009-01-20
Tried with a CRT monitor, same results.
Tried with different (ATI) video card, same results.
Tried with CRT and ATI card, same results.
I also put in a separate hard drive with windows on to see if any of my hardware had crapped out, everything worked fine.

---

### Post by Omegaxis on 2009-01-21
Does anyone know if there is like a master list of Hardware that Ubuntu has compatibility issues with.

---

### Post by JoshuaRL on 2009-01-21
> **Omegaxis said:**
> Does anyone know if there is like a master list of Hardware that Ubuntu has compatibility issues with.

Do you think you could try ordering a CD from Shipit?  I'm kind of at a loss to figure out what is going on.

---

### Post by Omegaxis on 2009-01-23
Just to toss this out there, my motherboard is an MSI K8T NEO-V. That seems to be about the only piece of hardware I haven't mentioned. I'll tinker with it since I really don't have anything to lose and post back here if anything works.

---

### Post by Omegaxis on 2009-01-28
Bump

---

### Post by Omegaxis on 2009-01-29
So apparently nobody here seems to know how to even begin to help me. Where should I go from here?

---

### Post by bodhi.zazen on 2009-01-29
boot to recovery mode. This will be command line only.

Then install envy :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy is in the repos (so you can install it with apt-get)

```
apt-get install envyng-core
```

envy is a command line only tool so it will install and configure your nvidia card.

Once X is up and running run :

```
gksu nvidia-settings
```

save your settings in a NEW xorg.conf (do NOT merge with the old, ie un select that option).

Post back any error messages.

---

### Post by Omegaxis on 2009-01-30
> **bodhi.zazen said:**
> boot to recovery mode. This will be command line only.

Then install envy :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)



Unfortunately the wireless card that my computer uses to connect to the Internet is not working either. I was going to try and get that figured out after I got the gui working.

---

### Post by EnGorDiaz on 2009-01-30
at first it look like a swap problem did you just recently build this computer?

---

### Post by Omegaxis on 2009-01-30
> **EnGorDiaz said:**
> at first it look like a swap problem did you just recently build this computer?

I built it in 2003, Up until about a 2 months ago I ran Windows XP off of a 250gig IDE drive. Unfortunately I had a power outage that ruined the windows boot init file. So I bought a 500gig sata drive and installed Ubuntu on that. Also I just remembered that I had originally tried to use Ubuntu, and had this exact same problem. I attributed it to the video card, and bought a new card and installed windows.

Edit: This could just be grasping at straws, but when I ran:
```
lshw
```
There were several pieces of hardware it Identified as 64KiB Bios, I am using a 32-bit AMD sempron proccessor, Although my motherboard (socket 754) appears to be geared more towards the 64-bit Athlon.

---

### Post by Omegaxis on 2009-01-31
[[IMG]http://img204.imageshack.us/img204/6366/1002803vx9.th.jpg[/IMG]](http://img204.imageshack.us/my.php?image=1002803vx9.jpg)
This is what I see when the progress bar gets to 95%, notice the Ubuntu loading screen at the top "row"

[[IMG]http://img207.imageshack.us/img207/4039/1002804ad2.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=1002804ad2.jpg)
This is what I get when I pres CTRL+ALT+F1

[[IMG]http://img156.imageshack.us/img156/2446/1002805wt8.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=1002805wt8.jpg)
```
lshw -class display
```

[[IMG]http://img230.imageshack.us/img230/9823/1002806ta8.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=1002806ta8.jpg)
And the ultra-specific xorg.conf file. (from what I've heard this means nothing since X will go ahead and configure based on the questions you answered when it installed, and will just ignore all of this.)

Also please remember I've tried this with Two different video cards (Geforce 7600, Ati Radeon something or other). Three different video output types (VGA,Digital,S-video), Using three different displays (LCD monitor, CRT monitor, CRT HDTV). All removable hardware has been tested on other machines and is in working order.

---

### Post by Omegaxis on 2009-01-31
Can no one help me?
Should I just give up?

---

### Post by Omegaxis on 2009-01-31
bumpity bump bump

---

### Post by JoshuaRL on 2009-02-01
This is for Hardy, but the Xorg version is similar, so if you're wanting to edit xorg.conf this might be of help.

[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

### Post by Omegaxis on 2009-02-01
> **JoshuaRL said:**
> This is for Hardy, but the Xorg version is similar, so if you're wanting to edit xorg.conf this might be of help.

[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

Yeah, I've tried that. Every time I reboot and check it, I find that it has gone back to the original "Configured Video Device" and such.

---

### Post by Omegaxis on 2009-02-03
I found this.

```
/var/log/gdm/0.log.2

(EE)Vesa(0): V_bios address 0xf70 out of range
(EE)Vesa(0): Screens found, but none have usable configuration


no screens found
7951 7785
giving up.
```


My monitor btw is [here.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824009108#spec")
(AL2016WBbd)
I can't seem to any more detailed information though.

---

### Post by Liviu-Theodor on 2009-02-03
When installing, try to specify a resolution, even one lower than your monitor support.

After install, try to enter at boot time in the "Ubuntu Safe Mode" or whatever is called, and from there to do the necesarry settings.

---

### Post by Omegaxis on 2009-02-03
> **Liviu-Theodor said:**
> When installing, try to specify a resolution, even one lower than your monitor support.

After install, try to enter at boot time in the "Ubuntu Safe Mode" or whatever is called, and from there to do the necesarry settings.

When I install, it never asks me to assign a resolution, it automatically puts it in as VESA. (Also in /var/log/Xorg.log.0, it shows it trying a _lot_ of resolutions and refresh rates.) 

Also I've don't know how to boot into "Safe Mode" If it's an option in any of the boot menus, then I seem to be missing it. If you're talking about recovery mode, then I that numerous times with no success.

Just for the record, my monitor's native resolution is 1680x1050, however it will autoscale just about 
anything.

edit:Eerily similar forgotten [thread.]("http://ubuntuforums.org/showthread.php?t=666110")

---

### Post by Omegaxis on 2009-02-04
bump, we are close to solving this, I can feel it.

---

### Post by Omegaxis on 2009-02-04
I'm trying things on my own, and only posting if I find something that seems to be an error. If anyone could point me to somewhere that has basic commands for the command line (how to copy files to an external usb drive and such)I would be very grateful.

Speak of the devil.......


```
dmesg | less
.......skipped over stuff that appears to be working.........
Hpet not enabled in bios, you might try hpet=forceboot
option
 <I think this is related to my wireless card which is also not working, but I figured it
 couldn't hurt to put it here>
.......more working stuff....................................
[0.533162} ACPI warning (tbutils-0217) incorrect checksum in table
 [OEMB] -98, should be8A [2003069] 
<I don't even begin to have an idea about what this means>








/var/log/gdm/:0.log

X: Client 4 rejected from local host
(uid=0 gid=0 pid=5604)
(uid=1000 gid=1000 pid=5608)
(uid=1000 gid=1000 pid=5609)
(uid=1000 gid=1000 pid=5610)
```

---

### Post by Omegaxis on 2009-02-07
Bump

---

### Post by Omegaxis on 2009-02-09
Please help me.......

---

### Post by arjuntank on 2009-02-09
was this the problem when u first installed ubuntu?

---

### Post by Kevbert on 2009-02-09
It may be the you've installed from a corrupted CD. Also what are your computer specs ? (memory in particular). Even though the native mode of the monitor may be high, it should be possible to run lower resolutions (then again with that error maybe not).  If you have a TV monitor you may be able to use that instead (at least to get Ubuntu running) and to get the Nvidia restricted drivers installed. I'm using the driver 169.12 on my Hardy install and have been using 180.27 (but other problems) on my Jaunty install. I can't remember the actual make of 7600 card (but in could be PNY).

---

### Post by Omegaxis on 2009-02-10
> **Kevbert said:**
> It may be the you've installed from a corrupted CD. Also what are your computer specs ? (memory in particular). Even though the native mode of the monitor may be high, it should be possible to run lower resolutions (then again with that error maybe not).  If you have a TV monitor you may be able to use that instead (at least to get Ubuntu running) and to get the Nvidia restricted drivers installed. I'm using the driver 169.12 on my Hardy install and have been using 180.27 (but other problems) on my Jaunty install. I can't remember the actual make of 7600 card (but in could be PNY).

My computer consists of this  [mobo]("http://www.msicomputer.com/product/p_spec.asp?model=K8T_Neo-V").
 A [DVD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827151133") drive.
 Two GBs of [ram.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231031")
A [wireless]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833158017") adaptor.
 A video [card.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176") 
One [screen]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824009108")  via a DVI cable.  A sound [card.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829118105") 
And a 500gb [hard drive.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148377")

Things I've tried.
Using a different graphics [card.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161032")
Using a CRT screen and a VGA connection.
Using an HDTV with an S-video connection.
Reinstalling with another burned disk.
Modifying the xorg.conf file to use "vesa" drivers.


And now most recently I just today received the "official" ubuntu installation disk I put it in, booted, tried to install and got
[[IMG]http://img204.imageshack.us/img204/6366/1002803vx9.th.jpg[/IMG]](http://img204.imageshack.us/my.php?image=1002803vx9.jpg)
this screen again (see first post on page 4 for more). When I hit CTRL+ALT+F1 its says "Loading, please wait..." and hangs there.
I have never actually successfully started Ubuntu (again please see page 4) so I can't do anything through a graphic interface. Also on top of this my wireless card will not connect to my network, so I cannot use apt-get.
Also note I've tested every piece of hard ware on my Windows based system, and everything is in working order. Also the only disk that has worked so far installation wise is the Alternate install disk. I've also posted several logs that show errors throughout the thread (on pages 1, 2, 4, and 5.)

---

### Post by Kevbert on 2009-02-10
Have you run memtest ? as it's possible to run Windows with faulty memory and only get an occasional unexpected crash.
Do you know what chipset the MSI wireless card is based on ? It may be possible to just put the drivers in the /lib/firmware directory in order to get that to work.

---

### Post by bodhi.zazen on 2009-02-10
[Omegaxis]("http://ubuntuforums.org/member.php?u=744116") you are stuck in a catch 22 ... 

I believe, as I indicated in my previous post, you need to install the nvidia drivers to fix your problem with the graphical system.

But you wanted to fix your wireless first ...

I suggest you use a wire to plug into the internet, then fix X (graphical system), then fix your wireless. By refusing to use a wired network card you are stuck at a dead end and there is really not much we can do.

If you can not connect to the internet it will be quite difficult or impossible to fix your problem.

You only other option would be to use aptoncd or to download the necessary files and dependencies manually on windows and transfer them on a flash drive. This option is more difficult as you would need to solve dependencies manually.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Omegaxis on 2009-02-11
> **Kevbert said:**
> Have you run memtest ? 
I am getting some errors with this. Hopefully it is limited to one stick.


edit: yep that fixed it.

---

### Post by Kevbert on 2009-02-11
It could even be a bit of dust (conductive) or a poorly seated memory stick. It may be worth swapping the good memory stick for the suspected bad one and doing a rerun of memtest.
Once you have the computer up and running, go to terminal and post back the output of
```
lspci
```
and we'll try and get wireless working.

---

### Post by Omegaxis on 2009-02-11
I can finally login!
I'm still having video card issues. (I have since connected to my home network with a 300ft cable a remembered I had) I installed and ran envy which selected the NVIDIA 173 driver. That driver was _very_ unstable (hard freeze if I moved the mouse too quickly). So I slowly switched to the 177 driver. However I still have problems that will get in the way of doing much else. For instance
[[IMG]http://img13.imageshack.us/img13/2557/smallervi3.th.jpg[/IMG]](http://img13.imageshack.us/my.php?image=smallervi3.jpg)

A lot of windows show up like the ones pictured including terminal.
Also I'm not sure why the mouse pointer came out clear in the picture. I'm only have an 80x80 square of static for a pointer. And finally if I try to play any type of video (even the hardware test video) then the system hard freezes, and I have to manually restart.

Maybe I should start a separate thread for this since this one is getting kind of beefy and this is *technically* a different issue.

---

### Post by Kevbert on 2009-02-11
You shouldn't need to use Envy for this card.

---

### Post by JoshuaRL on 2009-02-11
Try going to System->Administration->Hardware Drivers and enabling the suggested driver.  Then you'll need to reboot to use it.

---

### Post by Omegaxis on 2009-02-11
> **JoshuaRL said:**
> Try going to System->Administration->Hardware Drivers and enabling the suggested driver.  Then you'll need to reboot to use it.

I have enabled the suggested driver (nvidia 177), The screenshot is from the 177.

> **Kevbert said:**
> You shouldn't need to use Envy for this card.

Without it I was getting the same results at the top of page 4.

---

### Post by Omegaxis on 2009-02-12
bump

---

### Post by bodhi.zazen on 2009-02-12
In terms of X I think we can determine you are having problems with your nvidia card.

You can either get a new card or perhaps post / search on the nvidia forums as the nvidia drivers are closed source.

Older (nvidia or ATI) cards compatible with Linux are not *that* expensive and deliver great performance.

The next issue would be wireless, but that is another topic.

---

### Post by Cammy on 2009-02-12
Have you tried manually installing the latest nVidia driver?

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

---

### Post by lswest on 2009-02-12
Before you try installing any new drivers can you tell us if you had envy remove the driver it installed?

Also try this:

hit alt+F2
type "metacity --replace" (without quotes)
hit enter
wait for metacity (window manager) to reload and see if it helps.

---

### Post by Omegaxis on 2009-02-13
> **Cammy said:**
> Have you tried manually installing the latest nVidia driver?

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

I have installed the latest (180) Nvidia driver, I now have a proper mouse pointer, however the rest of the screen is white. If I enter my login and password, I can tell that it logs me in, but all I see is my mouse pointer and a grey bar at the top. If I click where the firefox icon would be, then I can tell it loads because I can see a rectangular box where the google search bar would be on the home page.

---

### Post by lswest on 2009-02-13
> **Omegaxis said:**
> I have installed the latest (180) Nvidia driver, I now have a proper mouse pointer, however the rest of the screen is white. If I enter my login and password, I can tell that it logs me in, but all I see is my mouse pointer and a grey bar at the top. If I click where the firefox icon would be, then I can tell it loads because I can see a rectangular box where the google search bar would be on the home page.

I had something similar with a black screen, try doing what I suggested above (metacity --replace) which seems to fix it for me (not sure why you need to refresh the window manager after just logging in, but hey), if it does so for you I will post back with instructions on automating that process.

---

### Post by Omegaxis on 2009-02-13
> **lswest said:**
> I had something similar with a black screen, try doing what I suggested above (metacity --replace) which seems to fix it for me (not sure why you need to refresh the window manager after just logging in, but hey), if it does so for you I will post back with instructions on automating that process.

I did, and it made some windows in the background appear as white boxes.

Also in the Xorg.log it says it can't load the GLX module. the gdm log mentions this as well.

---

### Post by lswest on 2009-02-13
Can you please post the contents of your xorg.conf file? (found under /etc/X11/xorg.conf) so that we can determine whether or not xorg is actually trying to load the glx module.

Also, the output of ```
sudo aptitude search nvidia
``` would be useful.

---

### Post by Omegaxis on 2009-02-14
> **lswest said:**
> Can you please post the contents of your xorg.conf file? (found under /etc/X11/xorg.conf) so that we can determine whether or not xorg is actually trying to load the glx module.

Also, the output of ```
sudo aptitude search nvidia
``` would be useful.

This will take quite some time, because I cannot take screen shots. I will have to transcribe them and type them here. Would anyone happen to know a way to save a screen shot or text in terminal as a document?

---

### Post by egalvan on 2009-02-14
> **Omegaxis said:**
>  Would anyone happen to know a way to save a screen shot or text in terminal as a document?

To save TEXT as a document, from a terminal, just highlight with the mouse, right-click to save it, then paste it into whatever text editor you like.

There are also mouse commands that will do this,
I don't know  the terminal equivalents  to ctrl-c and ctrl-v

:P And I hope that bad stick of RAM taught you a lesson that I learned years ago....:P

[I]Just because Microsoft is happy with the hardware,
doesn't mean the hardware is happy with anything else...
[/I]
It's amazing how much defective hardware MS will ignore.:confused:

---

### Post by Omegaxis on 2009-02-14
> **egalvan said:**
> To save TEXT as a document, from a terminal, just highlight with the mouse, right-click to save it, then paste it into whatever text editor you like.

There are also mouse commands that will do this,
I don't know  the terminal equivalents  to ctrl-c and ctrl-v


If you'll read back a few pages, I can't operate terminal in the graphical environment. When Ubuntu loads its crashes, so I hit CTRL+ALT+F1 to get to the terminal login. So no mouse.

---

### Post by lswest on 2009-02-14
run the commands and add a ">> /path/to/file" and save it on a USB stick, then copy and paste the info into code tags here.

so e.g. ```
sudo aptitude search nvidia >> ~/Desktop/output\ nvidia.txt
```

and to copy it insert a USB stick and:
```
sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk
cp ~/Desktop/output\ nvidia.txt /media/disk
```

/dev/sdb1 might not be your actual usb stick, check it using ```
sudo fdisk -l
```

Feel free to ask for any more help if you require it, I've subscribed to the thread (however, I will be out with my girlfriend for valentine's day in roughly an hour and will not be back for a few hours, so I will need a while to reply).
Lswest

---

### Post by Omegaxis on 2009-02-18
> **lswest said:**
> run the commands and add a ">> /path/to/file" and save it on a USB stick, then copy and paste the info into code tags here.


The computer I'm posting from doesn't recognize the usb drive, and asks me to format it.

also the only place I can find my usb drive is 
```
/dev/disk/by-label/<my drive>
```

and my linux pc doesn't recognize fdisk -1 as a valid command.

---

### Post by lswest on 2009-02-18
That's because it's not a 1 but an "l" (lowercase "L").  Do you have anything important on the USB drive?  Otherwise try re-formatting it to fat16 or fat32, then trying it again.

Sorry I can't offer more helpful suggestions,
Lswest

---

### Post by Omegaxis on 2009-02-18
Ok, stay with me here. I noticed the gdm log said "unable to load glx module" so I ran an uninstall with envyng, reset my xorg.conf in recovery, then reinstalled the latest Nvidia driver. 

So as of now, I am logged in, typing this from the ubuntu pc. however I still have a bunch-o-pixels instead of a mouse, and still have trouble with windows that have any movement in them whatsoever. Also if I try to play video,or audio, everything locks up and I have to manually restart.

here is the info that was requested

```
p   nvidia-173-kernel-source        - NVIDIA binary kernel module source        
i   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-177-kernel-source        - NVIDIA binary kernel module source        
i   nvidia-177-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - NVIDIA binary kernel module source        
p   nvidia-180-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-71-kernel-source         - NVIDIA binary kernel module source        
i   nvidia-71-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-96-kernel-source         - NVIDIA binary kernel module source        
i   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit Installer               
i   nvidia-common                   - Find obsolete NVIDIA drivers              
v   nvidia-glx                      -                                           
c   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-173-dev              - NVIDIA binary Xorg driver development file
c   nvidia-glx-177                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-177-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-180                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-180-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-71                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-71-dev               - NVIDIA binary Xorg driver development file
p   nvidia-glx-96                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-96-dev               - NVIDIA binary Xorg driver development file
v   nvidia-glx-dev                  -                                           
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
v   nvidia-kernel-source            -                                           
idA nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool           
```


Also, the installer log:










```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Feb 17 23:42:07 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 180.29.
-> There appears to already be a driver installed on your system (version: 180.
   29).  As part of installing this driver (version: 180.29), the existing driv
   er will be uninstalled.  Are you sure you want to continue? ('no' will abort
   installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS
   =/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  
   -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/
   include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasi
   ng -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -
   mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtu
   ne=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-t
   ables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default 
   -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg
   -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz5866/NVIDIA-Lin
   ux-x86-180.29-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wform
   at -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -M
   D -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV
   _VERSION_STRING=\"180.29\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(
   s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvid
   ia)" -c -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_nv.o
   /tmp/selfgz5866/NVIDIA-Linux-x86-1
   80.29-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv.c:14:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -
   include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -W
   no-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 
   -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-fra
   me-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wn
   o-pointer-sign -I/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -W
   no-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"1
   80.29\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BA
   SENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz5
   866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNE
   L__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include 
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigrap
   hs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O
   2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bounda
   ry=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/
   asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optim
   ize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp
   /selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wn
   o-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL_
   _ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.29\" -UDEBUG -U_DEBUG -DNDEBUG -
   DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29
   -pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/
   usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-agp.c:24:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D_
   _KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/in
   clude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-ret
   urn -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -
   pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mn
   o-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-o
   mit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statem
   ent -Wno-pointer-sign -I/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src
   /nv -Wall
    -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses 
   -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wn
   o-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.29\" -UDEBUG 
   -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_ST
   R(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz586
   6/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz586
   6/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-interface.c:26:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__
   KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/inc
   lude -include include/linux/autoconf.h -Iubuntu/include  -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3
   -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic 
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-
   protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclarat
   ion-after-statement -Wno-pointer-sign -I/tmp/selfgz5866/NVIDIA-Linux-x86-180
   .29-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"180.29\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidi
   a)" -c -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_os-re
   gistry.o /tmp/selfgz5866/NVIDIA-Lin
   ux-x86-180.29-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-registry.c:15:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNE
   L__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include 
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -
   Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2
   -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-fra
   me-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -I/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv -W
   all -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenthes
   es -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual 
   -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.29\" -UDEB
   UG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz5866/N
   VIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz5866/NVIDIA-
   Linux-x86-180.29-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNE
   L__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include 
   -include include/linux/autoconf.
   h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-st
   rict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -ms
   oft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -marc
   h=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchrono
   us-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/ma
   ch-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-siblin
   g-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz586
   6/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Ws
   witch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multicha
   r -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE
   -DNVRM -DNV_VERSION_STRING=\"180.29\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)" -c -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/s
   rc/nv/.tmp_nvacpi.o /tmp/selfgz5866
   /NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1975: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nv-linux.h:113,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/sr
   c/nv/nvidia.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nv-ker
   nel.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nv.o /tmp/self
   gz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz5866/NVIDI
   A-Linux-x86-180.29-pkg1/usr/src/nv/os-agp.o /tmp/selfgz5866/NVIDIA-Linux-x86
   -180.29-pkg1/usr/src/nv/os-interface.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.
   29-pkg1/usr/src/nv/os-registry.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg
   1/usr/src/nv/nv-i2c.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/u
   sr/src/nv/nvidia.ko;) > /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src
   /nv/modules.order
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.27-11-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.27-11-generic/Modu
   le.symvers -I /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/Module
   .symvers  -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/Module.
   symvers -S -K /usr/src/linux-headers-2.6.27-11-generic/Module.markers -M /tm
   p/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/Module.markers -w  -s
   WARNING: could not find /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__K
   ERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/incl
   ude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-com
   mon -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 
   -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic 
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-
   protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclarat
   ion-after-statement -Wno-pointer-sign -I/tmp/selfgz5866/NVIDIA-Linux-x86-180
   .29-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"180.29\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMOD
   ULE -c -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nvidia.mod
   .o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/asm/cpufeature.h:123,
                    from include/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvidia.mod.c:1:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/n
   v/nvidia.mod.c:1:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-p
   kg1/usr/src/nv/nvidia.ko /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/sr
   c/nv/nvidia.o /tmp/selfgz5866/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/nvidia
   .mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [   23.990103] Bluetooth: L2CAP socket layer initialized
   [   24.005454] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
   [   24.005460] Bluetooth: BNEP filters: protocol multicast
   [   24.067359] Bridge firewalling registered
   [   24.080536] Bluetooth: SCO (Voice Link) ver 0.6
   [   24.080542] Bluetooth: SCO socket layer initialized
   [   24.115301] Bluetooth: RFCOMM socket layer initialized
   [   24.115903] Bluetooth: RFCOMM TTY layer initialized
   [   24.115908] Bluetooth: RFCOMM ver 1.10
   [   26.951333] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
   [   26.951350] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x
   mode
   [   26.951434] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
   [   28.224678] eth0: link down
   [   28.226760] firmware: requesting rt2561s.bin
   [   28.320074] Xorg[5074]: segfault at fffffffc ip b7f0a6de sp bfa1697c
   error 4 in ld-2.8.90.so[b7efd000+1a000]
   [   28.479105] NET: Registered protocol family 17
   [   31.545711] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
   [   31.545730] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x
   mode
   [   31.545814] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
   [   32.769816] Xorg[5263]: segfault at fffffffc ip b7fbf6de sp bfccc40c
   error 4 in ld-2.8.90.so[b7fb2000+1a000]
   [   35.973431] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
   [   35.973449] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x
   mode
   [   35.973534] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
   [   37.207123] Xorg[5278]: segfault at fffffffc ip b7f1e6de sp bfd2cc6c
   error 4 in ld-2.8.90.so[b7f11000+1a000]
   [  244.090945] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.29  Wed Feb 
   4 23:44:25 PST 2009
-> Installing both new and classic TLS OpenGL libraries.
-> Parsing log file:
-> done.
-> Validating previous installation:
-> Unable to access previously installed file
   '/usr/lib/xorg/modules/drivers/nvidia_drv.so' (No such file or directory).
-> Unable to access previously installed file
   '/usr/share/man/man1/nvidia-xconfig.1.gz' (No such file or directory).
-> The previously installed file '/usr/share/man/man1/nvidia-settings.1.gz' has
   a different checksum (2925112942) than when it was installed (2270128235). 
   /usr/share/man/man1/nvidia-settings.1.gz will not be uninstalled.
-> The previously installed file '/usr/bin/nvidia-settings' has a different
   checksum (111943898) than when it was installed (2302687036). 
   /usr/bin/nvidia-settings will not be uninstalled.
-> Unable to access previously installed file '/usr/bin/nvidia-xconfig' (No
   such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-bug-report.sh'
   (No such file or directory).
-> Unable to access previously installed file
   '/lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia.ko' (No such
   file or directory).
-> The previously installed file
   '/usr/share/applications/nvidia-settings.desktop' has a different checksum
   (2755870013) than when it was installed (2744848513). 
   /usr/share/applications/nvidia-settings.desktop will not be uninstalled.
-> Unable to access previously installed symlink '/usr/lib/libcuda.so' (No such
   file or directory).
-> Unable to access previously installed symlink '/usr/lib/libGL.so' (No such
   file or directory).
-> Unable to access previously installed symlink
   '/usr/lib/xorg/modules/extensions/libglx.so' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib/libvdpau.so' (No
   such file or directory).
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than nvidia-installer
         (such as your distribution's native package management system). 
         nvidia-installer will attempt to uninstall as best it can.  Please see
         the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-18029
   (180.29)):
ERROR: Unable to create '/usr/lib/nvidia/libGL.so.1.2.xlibmesa' for copying (No
       such file or directory)
WARNING: Unable to restore file '/usr/lib/nvidia/libGL.so.1.2.xlibmesa'.
ERROR: Unable to create '/usr/lib/nvidia/libnvidia-cfg.so.177.82' for copying
       (No such file or directory)
WARNING: Unable to restore file '/usr/lib/nvidia/libnvidia-cfg.so.177.82'.
-> Unable to restore symbolic link /usr/lib/nvidia/libGL.so.1.xlibmesa ->
   libGL.so.1.2 (No such file or directory).
ERROR: Unable to create '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for
       copying (No such file or directory)
WARNING: Unable to restore file '/usr/lib/nvidia/libglx.so.xserver-xorg-core'.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (180.29) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (180.29):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86 (version: 180.29) is
   now complete.
```

edit: sound crash was due to .mp3 being associated with video player, fixed that.

---

### Post by lswest on 2009-02-18
Okay, well from what I can see the nvidia driver is present and there are no conflicting ones installed.

Can you also post the result of ```
glxinfo
``` please?

---

### Post by Omegaxis on 2009-02-18
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_ARB_create_context, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/AGP/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 180.29
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_framebuffer_object, GL_ARB_imaging, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, 
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

120 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

179 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x99  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9a  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9b  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x9c  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x9d  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9e  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9f  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xa0  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xa1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa2  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa3  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa4  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa9  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xaa  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xab  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xac  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xad  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xae  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xaf  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xb0  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xb1  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb2  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb3  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb5  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb6  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb7  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xba  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xbb  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbd  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbe  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbf  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc1  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xc2  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xc3  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xc4  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xc5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xca  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xcb  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xcc  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xcd  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xce  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xcf  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd1  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xd2  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xd3  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xd4  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xd5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xd6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xd7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd9  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xda  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xdb  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xdc  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xdd  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xde  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xdf  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe0  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe1  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xe2  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xe3  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xe4  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xe5  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xe6  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xe7  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe8  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xea  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xeb  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xec  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xed  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xee  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xef  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xf0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xf1  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xf2  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xf3  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xf4  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xf5  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xf6  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xf7  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xf8  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xf9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xfa  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xfb  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xfc  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xfd  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xfe  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xff  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x100  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x101  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x102  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x103  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x104  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x105  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x106  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x107  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x108  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x109  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x10a  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x10b  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x10c  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x10d  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x10e  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x10f  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x110  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x111  0 sg  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x112  0 sg  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x113  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x118  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x119  0 sg  0  0  0 r  .  .  0  0  0  0  4 16  0 16 16 16 16  0 0 None
0x11a  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0x11b  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
0x11c  0 sg  0 32  0 r  .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11d  0 sg  0 32  0    .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11e  0 sg  0 32  0 r  y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11f  0 sg  0 32  0    y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x120  0 sg  0 32  0 r  .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x121  0 sg  0 32  0    .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x122  0 sg  0 32  0 r  y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x123  0 sg  0 32  0    y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x124  0 sg  0 64  0 r  .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x125  0 sg  0 64  0    .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x126  0 sg  0 64  0 r  y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x127  0 sg  0 64  0    y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x128  0 sg  0 128  0 r  .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x129  0 sg  0 128  0    .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12a  0 sg  0 128  0 r  y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12b  0 sg  0 128  0    y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12c  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12d  0 sg  0 32  0    .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12e  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12f  0 sg  0 32  0    y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x130  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x131  0 sg  0 32  0    .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x132  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x133  0 sg  0 32  0    y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x134  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x135  0 sg  0 32  0    .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x136  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x137  0 sg  0 32  0    y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x138  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x139  0 sg  0 32  0    .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13a  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13b  0 sg  0 32  0    y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13c  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13d  0 sg  0 64  0    .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13e  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13f  0 sg  0 64  0    y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x140  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x141  0 sg  0 64  0    .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x142  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x143  0 sg  0 64  0    y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x144  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x145  0 sg  0 128  0    .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x146  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x147  0 sg  0 128  0    y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x148  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x149  0 sg  0 128  0    .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x14a  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x14b  0 sg  0 128  0    y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None

```

I don't know if this helps, all the opengl screen savers run as smooth as ever.

---

### Post by lswest on 2009-02-18
Well...it just tells me your graphics card driver is running great...it's metacity that's having issues.

Couple of options:

1. run ```
metacity --replace
``` from a terminal and post and errors it returns.

2. run ```
compiz --replace
``` and do the same.

3. Try both.

---

### Post by Omegaxis on 2009-02-19
```
 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
```



And, it doesn't say anything for metacity. Althought when I <metacity --replace> all the title bars disappear, and the system freeze for ~10minutes

---

### Post by lswest on 2009-02-19
> **Omegaxis said:**
> 
And, it doesn't say anything for metacity. Althought when I <metacity --replace> all the title bars disappear, and the system freeze for ~10minutes

Well...compiz seems to be fine, yet metacity has serious issues.  I'm not sure what can cause that behaviour, since metacity is actually the fallback window manager when compiz fails, so there's no logical reason as to why it wouldn't work, if compiz does.  The only thing I have left to suggest is that you right-click the desktop and choose "change background", go to themes (far left tab), click on "properties" of the one you're using and try changing the mouse pointer theme (I think it's the far right tab in the properties menu).  Might be that it's set to a theme that doesn't exist.

Also, did you ensure the disk you used to install did not have errors? (Bottom option of the install CD's menu), and did you check the checksum of the ISO if you downloaded it?

---

### Post by Omegaxis on 2009-02-19
Back with my earlier problems, I reinstalled three times, twice with disks I've burnt, and once with disk that was shipped to me. as for the mouse, it stays exactly the same even when I switch pointers.

I tried installing and using sawfish, but when I login I just get a system speaker beep a orange and white gradient, and the same mouse problem, and it just stays like that. I can move the mouse so I don't think it's frozen.

For a reference on what is happening with the messed up windows, there is a picture at the top of page 6. Also the mouse in the picture is not the mouse that I see, I don't know why it renders correctly in the screenshot but to on my screen.

---

### Post by lswest on 2009-02-19
> **Omegaxis said:**
> Back with my earlier problems, I reinstalled three times twice with disks I've burnt, and once with disk that was shipped to me. as for the mouse, it stays exactly the same even when I switch pointers.

I tried installing and using sawfish, but when I login I just get a system speaker beep a orange and white gradient, and the same mouse problem, and I just sticks there. I can mover the mouse so I don't think it's frozen.

For a reference on what is happening with the messed up windows, there is a picture at the top of page 6. Also the mouse in the picture is not the mouse that I see, I don't know why it renders correctly in the screenshot but to on my screen.

Actually, I have it set to 20 posts per page, so that's on I think page 3, either way, I have looked at the screenshots.  I can't think of anything else to suggest.

I don't suppose you can post info about your motherboard and graphic card? If your graphic card has built-in graphics it might be interfering and you may have to disable that in the BIOS.  Just a thought.  Well, unless you'd like to install fluxbox or openbox or something (different window manager) and see if they render correctly.

---

### Post by Omegaxis on 2009-02-19
[Motherboard]("http://www.msicomputer.com/product/p_spec.asp?model=K8T_Neo-V")


[GPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176")

So sawfish works, however it has the exact same graphic glitches in the exact same windows, still freezes when  I try to play a video too.

I also tried and installed xfce, still exact same problem. certain windows glitch, video freeze, messed up mouse.

Is there I terminal command that shows the temp readings without a graphical interface. (shot in the dark about possible heat problems)k

---

### Post by lswest on 2009-02-19
yeah, from the terminal do this:
```
sudo apt-get install lm-sensors
sudo sensor-detect
sensors
```
should install a sensor program, the sensor-detect loads modules (just choose "yes" for any prompt, only need to run it once), then type sensors to see the temperatures.

Otherwise the motherboard and graphics card seem fine :/

Also, try opening your PC and ensuring that the graphics card is connected properly and securely, make sure any extra power plugs are connected (for the fan).

---

### Post by Omegaxis on 2009-02-19
Well core is at 36c and case is at 34c......
Everything is plugged in, and all the fans are running.

---

### Post by lswest on 2009-02-19
> **Omegaxis said:**
> Well core is at 36c and case is at 34c......
Everything is plugged in, and all the fans are running.

Then I'm out of ideas.  Maybe someone else will know?  Otherwise try a different distribution of linux if you want to see if the error is ubuntu-specific.

---

### Post by Omegaxis on 2009-02-19
> **lswest said:**
> Then I'm out of ideas.  Maybe someone else will know?  Otherwise try a different distribution of linux if you want to see if the error is ubuntu-specific.

Any suggestions, or maybe somewhere with a large list of distros?

---

### Post by lswest on 2009-02-19
Have a look here: [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/) (it's a quiz to suggest a distribution that's suitable for you)

or else a few others:
- OpenSuse
- OpenSolaris (more unix than linux, but not bad)
- ArchLinux (it's very CLI-oriented if that bothers you)
- Gentoo
- Fedora

OpenSuse, OpenSolaris, Fedora and Gentoo offer liveCDs, ArchLinux doesn't offer one in the true sense of the word (it offers a bootable and usable CLI system).

Maybe go through the quiz and see which one appeals to you?

Or else browse here: [http://distrowatch.com/](http://distrowatch.com/)

Sorry I couldn't fix your problem,
Lswest

---

### Post by Omegaxis on 2009-02-19
When I go to System>Administration>Hardware Drivers, it says that no proprietary video drivers are installed.

Also where could I find a log of what's happening when I play a video?

---

### Post by lswest on 2009-02-19
That's normal since you installed the proprietary drivers off nvidia.com  It's not an official package and so the hardware driver program can't "see" it since it wasn't installed with apt-get or dpkg.

---

### Post by Omegaxis on 2009-02-20
I fixed the video issue by installing vlc, and setting the video to X11 mode.

I still have the  and metacity issues.


edit: just solved the mouse issue by adding xorg.conf option:
```
"<video card>"
"Option"   "HWcursor"  "off"
```

---

### Post by JoshuaRL on 2009-02-21
> **Omegaxis said:**
> I fixed the video issue by installing vlc, and setting the video to X11 mode.

I still have the  and metacity issues.


edit: just solved the mouse issue by adding xorg.conf option:
```
"<video card>"
"Option"   "HWcursor"  "off"
```

Sweet dude.  What exactly is the metacity issue again?

---

### Post by JerichoKru on 2009-02-21
How old is the said video card?  It's kind of a remote possiblility that the GFX card is going bad.

---

### Post by piroko on 2009-02-21
Sorry to barge into your thread like this omega, but if anyone isnt too busy here, could you have a look at my thread please?

[http://ubuntuforums.org/showthread.php?t=1076187](http://ubuntuforums.org/showthread.php?t=1076187)

Thank you.

---

### Post by Omegaxis on 2009-02-21
> **JoshuaRL said:**
> Sweet dude.  What exactly is the metacity issue again?

I'm getting a weird rendering issue....
[[IMG]http://img13.imageshack.us/img13/2557/smallervi3.th.jpg[/IMG]](http://img13.imageshack.us/my.php?image=smallervi3.jpg)

What's really strange is the terminal window suddenly started working, but the system resources window stays like that.
If I run metacity --replace then the system becomes unstable and freezes. Also I'm not running any visual effects.

---

### Post by lswest on 2009-02-21
Hmm, I booted an old PC of mine into Ubuntu and I noticed I get the same rendering issue for a fraction of a second while the window loads.  Have you given the system time to load it properly? (leave it for 5-10 minutes and see if it loads).  If it does the issue lies with your graphic card or RAM.

Just a thought,
Lswest

---

### Post by Omegaxis on 2009-02-21
> **lswest said:**
> Hmm, I booted an old PC of mine into Ubuntu and I noticed I get the same rendering issue for a fraction of a second while the window loads.  Have you given the system time to load it properly? (leave it for 5-10 minutes and see if it loads).  If it does the issue lies with your graphic card or RAM.

Just a thought,
Lswest

Yeah, I left it for 6 hours while I was at work the other day, and there was no change.

---

### Post by lswest on 2009-02-21
> **Omegaxis said:**
> Yeah, I left it for 6 hours while I was at work the other day, and there was no change.

Hmm, have you tried changing screen resolutions?  It may seem really random, but it might fix the rendering if it renders the image at a lower size, or just re-loads it at the correct size.

Again, I'm just thinking out loud here,
Lswest

---

### Post by spliffeh on 2009-02-23
My problem is possibly related to this thread. I've replicated this twice:

On a fresh Ubuntu 8.10 install, I go to 'hardware drivers' and activate the "recommended" nvidia driver that is listed there (i use dual Geforce 7800 GTX). It asks me to reset. Upon reboot I get this (I didnt write down the long UUID's):

[B]19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/*"blah-blah-blah"*)= dev(8,4)
kinit: trying to resume from /dev/disk/by-uuid/*"blah-blah-blah"*
kinit: No resume image, doing normal boot[/B]

Then it drops me to a login prompt.... sigh... what the hell?

Between this and it frying my MBR/grub settings on the first install... I'm really unimpressed with Ubuntu lately. Is there a stable version of Ubuntu that is user friendly? Because 8.10 obviously isn't it.... sigh

Anyone got any suggestions? Why does picking the "recommended" drivers trash my GUI?

---

### Post by lswest on 2009-02-23
> 19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/"blah-blah-blah")= dev(8,4)
kinit: trying to resume from /dev/disk/by-uuid/"blah-blah-blah"
kinit: No resume image, doing normal boot

The above is perfectly normal, it's checking for any suspended images, which don't exist due to the fact that it wasn't hibernated.

Once you get to the login shell log in as your user, then type the following: ```
startx
``` and record any errors it gives you, then post it in a new thread.  This issue is not related to the one previously mentioned in the thread, and it would be best if you ask for help in your own thread with a descriptive title to get the best help possible.

If you want, PM me the link to the new thread once you make it.

Lswest

To the OP: Still no new ideas on what could be causing the issues.

---

### Post by Omegaxis on 2009-02-25
I've been tinkering with some settings and have come across this:
```
compiz --replace
```
which produces an unstable desktop (which can be fixed by setting visual effects to none) as well as the following error

[[IMG]http://img408.imageshack.us/img408/7717/screenshotomegabedroom.th.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshotomegabedroom.png)

Also I added 
```
[1680x1050+0+0]
``` 
into the config for compiz, this stabilizes the desktop somewhat (with normal visual effects setting) however as soon as I goto a menu or move a window I get visual corruption.

If anyone can chip in as to what that above error means I would be very appreciative.

---

### Post by lswest on 2009-02-25
The "error" is actually only a warning and doesn't affect your display in any way.  At least it seems to be the case in [this thread]("http://ubuntuforums.org/showthread.php?t=571645").  I basically just googled the last bit and found that.  I doubt it's the source of your problems nor is it worth worrying about.  I'm inclined to think your graphics card might be having issues.

---


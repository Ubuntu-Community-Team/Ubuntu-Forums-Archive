---
title: "HOWTO: Netgear RangeMax Dual Band Wireless-N 300 USB Adapter (WNDA3100)"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by msikma on 2008-08-10
I just finished installing my WNDA3100 USB network adapter with ndiswrapper. First time I ever used the Windows driver wrapper, and it seems to work just fine. The WNDA3100 is useful for those who want to connect to a 802.11n network that can operate at 5 GHz, for example the Airport Extreme.

In order for the driver to be usable, it first needs to be installed under Windows. This is unfortunate, and I'm unsure whether there's some way to avoid this. If there's anyone who can shed more light on this, that would be great.

First, install the driver under Windows. The adapter should be attached to your Windows computer for this purpose. I used Windows XP, which detected the new hardware automatically and asked to install the drivers. Simply point it to the installation CD when it asks (there's no need to follow the CD's autorun program) and, when finished, view the properties of your network adapter to see which driver file it installed (it should be WNDA31.sys, if you're using this exact model).

Now that you have the driver, copy it to a separate folder (it should be in C:\WINDOWS\system32\DRIVERS\WNDA31.sys). Also copy the contents of the directory containing the .inf file that was used during installation (which should be D:\bin\config\ndis5\, assuming your CD drive is D). Copy all of these files to your Ubuntu machine.

Now you should set up your Ubuntu machine. I used version 8.04. You should first get the **ndiswrapper-common** and **ndiswrapperutils-1.9** packages with your favorite package manager. For example, in a terminal:

[INDENT][FONT="monospace"]msikma@Chopper:~$ **sudo apt-get install ndiswrapper-common ndiswrapperutils-1.9**[/FONT][/INDENT]

To ease things, we'll also install a graphical interface, **ndisgtk**:

[INDENT][FONT="monospace"]msikma@Chopper:~$ **sudo apt-get install ndisgtk**[/FONT][/INDENT]

Now go to the System --> Administration menu. After installing ndisgtk, there should be a new item in there named *Windows Wireless Drivers*. Start it and enter your password.

Now you should tell it to install the driver you copied to your Ubuntu machine before. Make sure you choose the .inf file. At this rate, your WNDA3100 should be recognized and working normally! :)

If it isn't working, ensure you have the WNDA31.sys file. To see if your system recognizes the presence of the wireless adapter at all, you can type

[INDENT][FONT="monospace"]msikma@Chopper:~$ **lsusb**[/FONT][/INDENT]

in a terminal, which should return one entry that says "NetGear, Inc".

I hope this helps anyone!

---

### Post by bean1975 on 2008-09-25
Very nice, thanks. Could you please (maybe in private?) send me the WNDA31.sys file? I extracted the MSI from the download with wine, then extracted files from MSI with p7zip and then more from Data1.cab with cabextract. I can see it wants to copy WNDA31.sys and arusb_2k.sys (edit: I was wrong. it wants to copy arusb_??.sys to WNDA31.sys) and the latter I have but not the former. None of the sys files are called WNDA and none of them even contain this string :( it would seem that ISSetupFile.SetupFile3 contains this file but I can't get further than that.

I now got further by installing on a Windows machine and the arusb_xp.sys gets copied to wnda31.sys. So I tried to install and

[  863.359811] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'NlsMbCodePageTag'
[  863.360075] ndiswrapper (load_sys_files:210): couldn't prepare driver 'arusb_xp'
[  863.360980] ndiswrapper (load_wrap_driver:112): couldn't load driver arusb_xp; check system log for messages from 'loadndisdriver'

not that good :/ Even if I try the 2K driver, that does not work either.

However!!

If you decide to go back one driver version THAT works. I have zipped up the inf and the sys file and attached.

---

### Post by inxygnuu on 2008-10-11
can you give me a simpler way to do this? I really need to get online through wireless.:)

---

### Post by touristguy87 on 2008-10-30
> **bean1975 said:**
> Very nice, thanks. Could you please (maybe in private?) send me the WNDA31.sys file? I extracted the MSI from the download with wine, then extracted files from MSI with p7zip and then more from Data1.cab with cabextract. I can see it wants to copy WNDA31.sys and arusb_2k.sys (edit: I was wrong. it wants to copy arusb_??.sys to WNDA31.sys) and the latter I have but not the former. None of the sys files are called WNDA and none of them even contain this string :( it would seem that ISSetupFile.SetupFile3 contains this file but I can't get further than that.

I now got further by installing on a Windows machine and the arusb_xp.sys gets copied to wnda31.sys. So I tried to install and

[  863.359811] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'NlsMbCodePageTag'
[  863.360075] ndiswrapper (load_sys_files:210): couldn't prepare driver 'arusb_xp'
[  863.360980] ndiswrapper (load_wrap_driver:112): couldn't load driver arusb_xp; check system log for messages from 'loadndisdriver'

not that good :/ Even if I try the 2K driver, that does not work either.

However!!

If you decide to go back one driver version THAT works. I have zipped up the inf and the sys file and attached.


If you decide to go back one driver version THAT works. I have zipped up the inf and the sys file and attached.
Attached Files
File Type: zip 	ndis_wnda3100.zip (158.2 KB, 18 views)

it does indeed work, thank you. 

You have to remove and reinstall the adapter aftewards and I did get it to work on an XP machine first. 

but it's running right now on 804

thanks

---

### Post by mariusmeyer on 2009-05-11
Dear bean1975:
Where did you find those drivers that you posted? Did they come from Atheros directly, or from your adapter's vendor? I've found them to work with my NetGear WN111v2 USB adapter, even though (amazingly) the very drivers that came with the adapter, didn't. They are named the same; arusb_xp. ...

Cheers

---

### Post by flash63 on 2009-05-11
Hello,
i build a driver-package for atheros ar9170 based USB-Dongles.

See [http://ubuntuforums.org/showthread.php?t=1150835](http://ubuntuforums.org/showthread.php?t=1150835)
and
[http://ubuntuforums.org/showthread.php?t=1052619&page=2](http://ubuntuforums.org/showthread.php?t=1052619&page=2)
for details.

---

### Post by Habboblob on 2009-05-25
I've used Bean's driver for my WN111v2 and it worked perfectly but I can't seem to connect to my WPA2 Wireless network. Can someone please help me.

---

### Post by Habboblob on 2009-05-29
I can connect to my wireless network using another connection. But it doesn't always connect 100%.

Like now I just suddenly started working in 2 weeks. I hope it continue to works my WN111v2

---

### Post by ThreeFlight2005 on 2009-06-11
I'm using fedora 11 and the only drivers that work are on this page with this version of the xp drivers for some reason. The WN111v2 drivers that are shipped with the adapter are useless you have to use the ones on this page with ndiswrapper.

---

### Post by theberg5 on 2009-09-12
Hey bean thank you very much, it worked great!!!

---

### Post by cooldude3663 on 2009-09-25
Where do you paste the driver? I am confused, I am a total linux noob.

---

### Post by cooldude3663 on 2009-09-25
I am having issues trying to get my wn111 v2 dongle to work. I do not have ndwrapper and am a complete noob when it comes to Linux. I am using Ubuntu 9.04 any help would be greatful in trying to get this to work.

---

### Post by jfmherokiller on 2009-09-27
thanks this solution worked for me

---

### Post by Despell1 on 2009-10-28
> **Habboblob said:**
> I've used Bean's driver for my WN111v2 and it worked perfectly but I can't seem to connect to my WPA2 Wireless network. Can someone please help me.
I have the same problem. Help!

---

### Post by Limitlesschannels on 2009-12-08
Thanks, bean!
  I couldn't quite get bean1975's drivers to work for me, but by combining them with mine from a windows install, I was able to get my wireless recognized and working.  If anyone still can't seem to connect, I attached my drivers.
  For me to connect I had to install both this .inf (attached) and bean1975's .inf.

---

### Post by floatofmath on 2010-01-11
For this to work with my WNDA3100 stick I also needed the drivers provided by Limitlesschannels. However i can't seem to get 5G working. 

Any ideas?

---

### Post by frankida on 2010-03-04
So the wireless was working great until I installed ubuntu 32 bit.  I followed the steps and had it working and then when I restarted it crapped out.

I reinstalled ubuntu to see if I had messed something up but it still give me "unable to see if hardware present error"

I'm pretty stumped!

---

### Post by frankida on 2010-03-05
> **frankida said:**
> So the wireless was working great until I installed ubuntu 32 bit.  I followed the steps and had it working and then when I restarted it crapped out.

I reinstalled ubuntu to see if I had messed something up but it still give me "unable to see if hardware present error"

I'm pretty stumped!

I figured it out by looking at another thread.  I installed gnome network admin package and it worked.

SWEET!:p

---

### Post by lunanueva on 2010-04-21
Thank you for posting this fix so long ago.  It helped me get my wireless usb device working with ubuntu and i'm sure it is still helping people out today.

many many thx!!!

---

### Post by lunanueva on 2010-04-21
many thx to bean1975 too for attaching those drivers.  you guys are awesome!!

---

### Post by jakedaflake on 2010-07-14
I found out that my WNDA3100 is v2 with the Broadcom chipset. Atheros drivers do not work.
Installed on Winxp box then transfered the needed files to my laptop which is running 9.10.

---

### Post by Neosurfer on 2010-07-23
Can you send me those files?
Or tell me exactly which ones to transfer?
Thanks,

Neosurfer

---

### Post by yangerness on 2010-07-27
Thanks for all the files guys. My wireless seems to work. However it doesn't seem to connect to my specific network. It can connect to other unprotected ones just fine... but not mine. T_T Any one have any ideas?

---

### Post by mcanbolat on 2010-10-02
Hello
I tried both of the drivers provided here but my Ubuntu (10.04) was not able to detect the Wireless USB adapter. The .inf and .sys files that I extracted from the installation CD (which have the same names as LimitlessChannels' drivers) were recognized by ndiswrapper. But the problem is, my adapter does not seem to be working as there is no blue light present. Ndiswrapper indicates that there are drivers and hardware present, but there is no wlan0 listed. I disabled the eth0 port and I also tried to modify  ntoskernel_io.c in the Ndiswrapper package as suggested by another forum user, but that didn't give me any luck either. 
I guess I am giving up.
Cheers,

---

### Post by erixoltan on 2010-11-09
I have 64bit Maverick.  I used a Win7 64 bit .inf file and got the USB WNDA3100 v2 to detect, but wlan0 is not enabled no matter what I try.  I installed Win XP (32 bit) .inf file and it crashes when I try to load the driver.  I guess maybe I need a 64 bit WinXP driver (??) but I don't have a 64 bit WinXP machine so I'm out of luck unless anyone has helpful ideas??

---

### Post by poultond on 2010-11-12
> **Limitlesschannels said:**
> Thanks, bean!
  I couldn't quite get bean1975's drivers to work for me, but by combining them with mine from a windows install, I was able to get my wireless recognized and working.  If anyone still can't seem to connect, I attached my drivers.
  For me to connect I had to install both this .inf (attached) and bean1975's .inf.

This worked for me!!

Thanks!

---

### Post by erixoltan on 2011-01-19
> **erixoltan said:**
> I have 64bit Maverick.  I used a Win7 64 bit .inf file and got the USB WNDA3100 v2 to detect, but wlan0 is not enabled no matter what I try.  I installed Win XP (32 bit) .inf file and it crashes when I try to load the driver.  I guess maybe I need a 64 bit WinXP driver (??) but I don't have a 64 bit WinXP machine so I'm out of luck unless anyone has helpful ideas??Anyone have any ideas?

---

### Post by ShanaWithBlazingEyes on 2011-04-03
Thanks a lot.  Worked a dream, and not as complicated as with some of the other threads.

If you are lucky enough to have the synaptic package manager, which comes with the ubuntu netbook edition 10.04+ (at least), then you can install the ndis... packages from there simply by searching for them in the package manager, although you do have to install the ndisgtk and ndiswrapper-dkms as well to get the windows driver interface to install on ubuntu.

After that, simply make sure your wireless settings are right (at the time of this post, netgear/virgin media (my broadband providers) have not implemented IPV6, so enabling this will stop the connection between the router and wireless USB dongle.

---

### Post by rich_hemmings on 2011-09-10
> **erixoltan said:**
> Anyone have any ideas?


BUMP

Having the same problem, have tried Win7 and WinVista drivers (64Bit) as well as arusb_xp.inf(32Bit) and bcmwlhigh5.inf(32Bit) with varying results. 
Drivers install in Windows Wireless Drivers, but wlan0 is not enabled at boot.
:confused:

---

### Post by alias13e on 2011-11-06
Hello,
I just installed ubuntu linux on my computer.  I have zero experience using linux and I need some help installing the driver for my netgear wn111v2 wireless adapter.  Downloaded otus-WN111v2.zip and wpa_supplicant-0.4.8_otus.tar.bz2.  I don't know if these are what I need, but I can make no sense of their contents.  If someone would be kind enough to walk me through this I would be ever so grateful.  Thanks!

---

### Post by bowden7225 on 2011-11-29
I am new to the ubuntu os. I have been trying to use my wnda3100 adapter on an old gateway. I have followed the instructions posted (current version and back version)  on this thread to neither are working - (the exception is I never had success finding/loading the wnda31.sys file...the .sys file I have are bwcwlhigh*.sys).

In any event, the driver is successfully installed and the hardware is recognized.I have configured the wireless connection with my wep security.  However, I do not have a wireless network option under available networks just "wired" and vpn. Also when I unplug my ethernet there is no connectivity.

Please advise if there are any other approaches or something I am missing....MANY THANKS!

---

### Post by Sh4d3y on 2012-04-25
> **msikma said:**
> I just finished installing my WNDA3100 USB network adapter with ndiswrapper. First time I ever used the Windows driver wrapper, and it seems to work just fine. The WNDA3100 is useful for those who want to connect to a 802.11n network that can operate at 5 GHz, for example the Airport Extreme.

In order for the driver to be usable, it first needs to be installed under Windows. This is unfortunate, and I'm unsure whether there's some way to avoid this. If there's anyone who can shed more light on this, that would be great.

First, install the driver under Windows. The adapter should be attached to your Windows computer for this purpose. I used Windows XP, which detected the new hardware automatically and asked to install the drivers. Simply point it to the installation CD when it asks (there's no need to follow the CD's autorun program) and, when finished, view the properties of your network adapter to see which driver file it installed (it should be WNDA31.sys, if you're using this exact model).

Now that you have the driver, copy it to a separate folder (it should be in C:\WINDOWS\system32\DRIVERS\WNDA31.sys). Also copy the contents of the directory containing the .inf file that was used during installation (which should be D:\bin\config\ndis5\, assuming your CD drive is D). Copy all of these files to your Ubuntu machine.

Now you should set up your Ubuntu machine. I used version 8.04. You should first get the **ndiswrapper-common** and **ndiswrapperutils-1.9** packages with your favorite package manager. For example, in a terminal:
[INDENT][FONT=monospace]msikma@Chopper:~$ **sudo apt-get install ndiswrapper-common ndiswrapperutils-1.9**[/FONT][/INDENT]To ease things, we'll also install a graphical interface, **ndisgtk**:
[INDENT][FONT=monospace]msikma@Chopper:~$ **sudo apt-get install ndisgtk**[/FONT][/INDENT]Now go to the System --> Administration menu. After installing ndisgtk, there should be a new item in there named *Windows Wireless Drivers*. Start it and enter your password.

Now you should tell it to install the driver you copied to your Ubuntu machine before. Make sure you choose the .inf file. At this rate, your WNDA3100 should be recognized and working normally! :)

If it isn't working, ensure you have the WNDA31.sys file. To see if your system recognizes the presence of the wireless adapter at all, you can type
[INDENT][FONT=monospace]msikma@Chopper:~$ **lsusb**[/FONT][/INDENT]in a terminal, which should return one entry that says "NetGear, Inc".

I hope this helps anyone!


DEAR [msikma]("http://ubuntuforums.org/member.php?u=190049")

THANK YOU SO MUCH AFTER HOURS of scanning forums and trying to understand all the Jargon I found you and your instructions helped me get it working, Im a NOOB to Linux and was very close to giving up with it and going back to WINDOZE but you saved my LINUX's life <3 :D

---

### Post by eyuel on 2013-03-31
I was able to get my 12.04 machine to recognize the hardware by installing both bean1975's and Limitlesschannels' drivers, though I had to refer to these pages:
> 
[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)

since Windows Wireless Drivers couldn't find ndiswrapper and installing ndiswrapper-dkms caused an error.

Big thanks to msikma, bean1975, and Limitlesschannels!

---

### Post by wildmanne39 on 2013-03-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


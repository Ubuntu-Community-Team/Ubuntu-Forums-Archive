---
title: "Installing drivers and other packages."
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Valkyria on 2009-02-27
I just got Ubuntu today and installed it on my Acer Aspire 6930G and i have some drivers and other things i would like to install..but ima noob..ive never really used Ubuntu before, i dont know how to install anything.

---

### Post by perlluver on 2009-02-27
What drivers are you trying to install?  Please run ```
lspci
``` in a terminal, Applications>Accessories>Terminal and post the output back here.  That will give us a list of the hardware on your system.

---

### Post by Valkyria on 2009-02-27
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```

I know the for sure drivers i need are the Nvidia GPU driver (which i have already downloaded, but i just dont know how to install) and a driver for the wireless

---

### Post by Shazaam on 2009-02-27
Don't install those downloaded drivers just yet. Go to System>Administration>Hardware Drivers and check to see if there are any drivers that you can activate.

---

### Post by Valkyria on 2009-02-28
I just went to hardware drivers and the only one that is listed the Nvidia GPU Driver.  It listed me 2 options, version 173 and version 177 (this one is recommended). I went to the Nvidia website and downloaded latest which is version 180.29 (but i havent installed it yet.  Im not sure if this will make a difference in finding drivers, but im using the 64-bit Ubuntu.

---

### Post by Doug11 on 2009-02-28
> **Valkyria said:**
> I just went to hardware drivers and the only one that is listed the Nvidia GPU Driver.  It listed me 2 options, version 173 and version 177 (this one is recommended). I went to the Nvidia website and downloaded latest which is version 180.29 (but i havent installed it yet.  Im not sure if this will make a difference in finding drivers, but im using the 64-bit Ubuntu.
What version of 64 are you running? As a new user on 64bit,, you may want to have a look at this. Its a good read,,
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by Valkyria on 2009-02-28
Thanks for that link :). I am using Ubuntu 8.10 (i forgot whats its name is) and from the read i would have use for the 64 bit. I was planning on running F@H (Folding at Home) and also some graphics editing, and maybe some math stuff too. Im also still curious on how to install the drivers once i get them.  I read on how to install .tgz and .run file but i forgot how to do it

---

### Post by Valkyria on 2009-02-28
> **Doug11 said:**
> What version of 64 are you running? As a new user on 64bit,, you may want to have a look at this. Its a good read,,
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

Do you know of any programs for Linux that are good for graphics?

---

### Post by prout1357 on 2009-02-28
GIMP:popcorn:

---

### Post by marco123 on 2009-02-28
Gimp, Inkscape, Blender etc...

You should check out the package ubuntustudio-graphics in Synaptic package manager which installs all the graphics editing software from the Ubuntustudio distribution. 

As for the drivers just select the recommended one in Hardware drivers utility and click Activate.

Cheers, Marco

---

### Post by marco123 on 2009-02-28
Also you should probably install ubuntu-restricted-extras which will give you Flash, Java mp3 support wma/wmv support etc...

> sudo apt-get install ubuntu-restricted-extras

Also install the noscript and adblock plus plugins for Firefox.  You will then be really, really secure using Linux.:)

[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

Cheers, Marco.

Edit: Also check out this site it's awesome: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
Installing software in Linux: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Valkyria on 2009-02-28
Thanks a bunch for the Firefox addons and the links Marco :D.  I have a question regarding the nvidia drivers. I believe i said eariler, Hardware Drivers said it had version 177, and i currently have it activated, but i looked on the Nvidia website and downloaded the latest version which is 180.29. Is it ok to install the newer drivers.  If so how do i because i look at the readme Nvidia made and i did the command the readme said to do but it didnt work.

---

### Post by marco123 on 2009-02-28
There's really no need or benefit to installing the newer ones.  They might not work as well as the "proper" ones for this release, also they won't be automatically updated along with the rest of the system therefore you might encounter breakage when installing kernel or Xorg updates etc...  I've only ever used the built in ones for Nvidia and ATI cards and never had any problems.

Cheers, Marco.

---

### Post by Valkyria on 2009-02-28
Just a few minutes ago i was about to go to install Wine, i went to add/remove and when it was doing its little check i got a error and im not sre how i could have gotten it
[IMG]http://i228.photobucket.com/albums/ee259/epdrumman/firsterror.png[/IMG]
How can i fix this

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> There's really no need or benefit to installing the newer ones.  They might not work as well as the "proper" ones for this release, also they won't be automatically updated along with the rest of the system therefore you might encounter breakage when installing kernel or Xorg updates etc...  I've only ever used the built in ones for Nvidia and ATI cards and never had any problems.

Cheers, Marco.

Ok.  Would using an older driver affect games alot.

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> Ok.  Would using an older driver affect games alot.

No, not in Linux anyway.  Also those drivers are specifically optimized for Ubuntu.

Cheers, Marco.

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> Just a few minutes ago i was about to go to install Wine, i went to add/remove and when it was doing its little check i got a error and im not sre how i could have gotten it
[IMG]http://i228.photobucket.com/albums/ee259/epdrumman/firsterror.png[/IMG]
How can i fix this

First check in Synaptic,  System>Administration>Synaptic Package Manager for broken packages.  In the bottom left corner of Synaptic select Custom Filter, then select Broken above it.  

Then type the 2 commands given in the error message in to the terminal one at a time in order: sudo apt-get update     then      sudo apt-get install -f

I attached a screenshot of where to find "Broken" in Synaptic

Cheers, Marco

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> First check in Synaptic,  System>Administration>Synaptic Package Manager for broken packages.  In the bottom left corner of Synaptic select Custom Filter, then select Broken above it.  

Then type the 2 commands given in the error message in to the terminal one at a time in order: sudo apt-get update     then      sudo apt-get install -f

I attached a screenshot of where to find "Broken" in Synaptic

Cheers, Marco

Thanks:D..I got it fixed. Oh and just wondering. What desktop environment are you using, i like the look of it. Also how could i get it

---

### Post by Valkyria on 2009-02-28
I have another question :P..How can i get my wireless to work?

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> I have another question :P..How can i get my wireless to work?

Did you sort the package error?

I've connected my daughters Ubuntu laptop to our wireless network, if I remember correctly it was detected at install and has worked since.  If there is an available wireless network it should appear in the list when you left-click on the network manager in the notification area. (Top right.)  Then you just select your wireless connection and stick in the key.

Sorry I can't be of more help with this one, I haven't had much experience with wireless on Ubuntu.  I'm sure others will also be able to answer any specific questions/problems you encounter with wireless though.:)  (These forums are one of the best things about Ubuntu in my opinion.)

Cheers, Marco.

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> Did you sort the package error?

I've connected my daughters Ubuntu laptop to our wireless network, if I remember correctly it was detected at install and has worked since.  If there is an available wireless network it should appear in the list when you left-click on the network manager in the notification area. (Top right.)  Then you just select your wireless connection and stick in the key.

Sorry I can't be of more help with this one, I haven't had much experience with wireless on Ubuntu.  I'm sure others will also be able to answer any specific questions/problems you encounter with wireless though.:)  (These forums are one of the best things about Ubuntu in my opinion.)

Cheers, Marco.

I just remembered that on my laptop (Acer Aspire 6930G) it has buttons above the numeric pad (one of them to turn on and off wireless) and would i need some sort of driver to get that to work? I guess i could check the acer site.

Edit: I just searched on the Acer website..no drivers D:....so now i have no idea of how to enable wireless.

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> I just remembered that on my laptop (Acer Aspire 6930G) it has buttons above the numeric pad (one of them to turn on and off wireless) and would i need some sort of driver to get that to work? I guess i could check the acer site.


Try turning it on and see if any notifications appear.  If nothing try logging out then logging back in again and see if it recognizes it.  A lot of wireless drivers are already built into the Ubuntu kernel.

Cheers, Marco.

---

### Post by marco123 on 2009-02-28
If not an easy way is to install the ndiswrapper packages in synaptic, just search for "ndiswrapper" (see Screenie), and install the windows driver for your particular card, in this case Intel 5100: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=&lang=eng&strOSs=45&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=&lang=eng&strOSs=45&submit=Go)!

Cheers, Marco.

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> If not an easy way is to install the ndiswrapper packages in synaptic, just search for "ndiswrapper" (see Screenie), and install the windows driver for your particular card, in this case Intel 5100: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=&lang=eng&strOSs=45&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=&lang=eng&strOSs=45&submit=Go)!

Cheers, Marco.

I installed the ndiswrapper and downloaded the wireless driver. Then i searched for the driver i download. I clicked install and i got a error saying "Not a valid driver .inf file"

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> I installed the ndiswrapper and downloaded the wireless driver. Then i searched for the driver i download. I clicked install and i got a error saying "Not a valid driver .inf file"

I think you might have to install it in the the ndiswrapper gui.  After install it should be somewhere in your menus.

Cheers, Marco.

---

### Post by marco123 on 2009-02-28
Couple of links that might help:

[http://ubuntuforums.org/showthread.php?t=965516](http://ubuntuforums.org/showthread.php?t=965516)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Cheers, Marco.

---

### Post by marco123 on 2009-02-28
Just an idea, try booting the Live CD into the desktop with the ethernet cable disconnected and the wireless switch ON.

If this "sees" the wireless card and works you might as well reinstall Ubuntu on the same partition/partitions that you used last time.  It only takes half an hour and then just reinstall the updates, the drivers and ubuntu-restricted-extras package.  Wireless should then work with no problems.  It's a bit drastic I know, reinstalling a Unix based system, but sometimes it's a cure-all solution.

I'll be glad to help walk you through anything else I can help with. :)

Cheers, Marco.

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> Couple of links that might help:

[http://ubuntuforums.org/showthread.php?t=965516](http://ubuntuforums.org/showthread.php?t=965516)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Cheers, Marco.

I looked at the second link you listed and i kinda understand it but not completely.  I have the driver downloaded (its a zip if that matters, and i also installed cabextract and unshield) and it said to type ```
sudo ndiswrapper -i ~/drivers/drivername.inf
``` It talked about a drivers folder on the home directory, but i looked and didnt see one there so i made a folder. Is it right to make the folder and put the .zip file in the folder, or do i extract the file from the zip to the drivers folder i made?

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> I looked at the second link you listed and i kinda understand it but not completely.  I have the driver downloaded (its a zip if that matters, and i also installed cabextract and unshield) and it said to type ```
sudo ndiswrapper -i ~/drivers/drivername.inf
``` It talked about a drivers folder on the home directory, but i looked and didnt see one there so i made a folder. Is it right to make the folder and put the .zip file in the folder, or do i extract the file from the zip to the drivers folder i made?

Sorry, I can't help you with this one (got no experience with it) try starting a separate thread called something like "Getting Intel 5100 wireless to work with ndiswrapper" there's probably someone who's set it up or who has experience with ndiswrapper.

Did you try the live cd with only wireless enabled and no ethernet?  When I installed ubuntu on my daughters laptop it just worked straight away on the live cd and then on the install.  All I had to do was insert the wireless key (WPA Personal).

Cheers, Marco.

---

### Post by Valkyria on 2009-02-28
> **marco123 said:**
> Sorry, I can't help you with this one (got no experience with it) try starting a separate thread called something like "Getting Intel 5100 wireless to work with ndiswrapper" there's probably someone who's set it up or who has experience with ndiswrapper.

Did you try the live cd with only wireless enabled and no ethernet?  When I installed ubuntu on my daughters laptop it just worked straight away on the live cd and then on the install.  All I had to do was insert the wireless key (WPA Personal).

Cheers, Marco.

I had no ethernet pluged in and it still didnt make the wireless work. So i guess ill start a different thread. Thanks a bunch for your help :)

---

### Post by marco123 on 2009-02-28
> **Valkyria said:**
> I had no ethernet pluged in and it still didnt make the wireless work. So i guess ill start a different thread. Thanks a bunch for your help :)

No problem at all.  Enjoy Ubuntu.:)

Cheers, Marco.

---

### Post by bapoumba on 2009-02-28
Thread title edited. Please choose a descriptive title, thanks.
Happy birthday BTW :)

---

### Post by Valkyria on 2009-02-28
> **bapoumba said:**
> Thread title edited. Please choose a descriptive title, thanks.
Happy birthday BTW :)

OK my bad and thanks :D. My b-day was yesterday. Im now the ripe old age of 19 :P

---

### Post by bapoumba on 2009-02-28
> **Valkyria said:**
> OK my bad and thanks :D. My b-day was yesterday. Im now the ripe old age of 19 :P
Pff. Just wait and you'll know what ripe old age means :tongue:

---


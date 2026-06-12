---
title: "Newb alert. Wireless problems, icons, system lag."
date: 2011-02-08
forum: New to Ubuntu
---

### Post by yuri nator on 2011-02-08
Pardon my ignorance.

I'm a total newb to linux from Windows 7, so far I'm in partial hell.
Im using Kubuntu 10.10

Problem 1. Wireless.
My wireless doesn't work. The wireless option in KDE control module - network connections, can't be clicked. (it's not highlighted) 
I've got an intel 6300n  card. So far I've understood almost nothing I've read on trying to get it to work. 
I don't know if I need drivers, if it needs to be turned on somewhere or if I need to marry a squirrel. 


2.. Can  I put icons on the desktop, if yes, how?

3. Sometimes the system is laggy, a reboot fixes this but I'm curious for a solution if there is one.
 
4. Updates, is it wise to download all or analyze all and be selective?

As you can probably tell, I have no idea what I'm doing and I'm wondering if I should just go back to Windows as it's far simpler. 

Is anything simple in linux?

:redface:

---

### Post by Bucky Ball on 2011-02-08
Welcome. Try 10.04 LTS from the LiveCD (the install CD and option 'Try Ubuntu'). If everything works ok then install. You may have more luck and a smoother ride as is stable release. (Longer support also.) ;)

2/ Right-click and create shortcut (you can also drag from 'Applications' menu).

4/ No need to analyse. Install all as all from Ubuntu (trusted) repositories at this point. May also fix some of your problems and pick up your wireless card (automatically download appropriate firmware/software).

To get wireless up you may need to get the updates in fact.

---

### Post by sydbat on 2011-02-08
> **yuri nator said:**
> Pardon my ignorance.

I'm a total newb to linux from Windows 7, so far I'm in partial hell.
Im using Kubuntu 10.10

Problem 1. Wireless.
My wireless doesn't work. The wireless option in KDE control module - network connections, can't be clicked. (it's not highlighted) 
I've got an intel 6300n  card. So far I've understood almost nothing I've read on trying to get it to work. 
I don't know if I need drivers, if it needs to be turned on somewhere or if I need to marry a squirrel. 


2.. Can  I put icons on the desktop, if yes, how?

3. Sometimes the system is laggy, a reboot fixes this but I'm curious for a solution if there is one.
 
4. Updates, is it wise to download all or analyze all and be selective?

As you can probably tell, I have no idea what I'm doing and I'm wondering if I should just go back to Windows as it's far simpler. 

Is anything simple in linux?

:redface:Most things are simple in Linux!

As for your problems, can you tell us how you installed Ubuntu? Was it with wubi? If so, this could explain the lagginess and wireless issues.

Because wubi is a virtual machine running inside Windows and is reliant on the Windows file system, major corruption in your Ubuntu filesystem can occur if Windows was not properly defragmented before proceeding with a wubi install.

---

### Post by gordintoronto on 2011-02-08
You could also mention what kind of computer this is.

This message thread might help you with the wireless:
[http://ubuntuforums.org/showthread.php?t=1420901](http://ubuntuforums.org/showthread.php?t=1420901)

I found it by Googling: intel 6300n ubuntu

More people use Ubuntu than Kubuntu, so you might find it easier to get help with Ubuntu. Once you are feeling more confident, you could give Kubuntu a try.

---

### Post by yuri nator on 2011-02-09
> **Bucky Ball said:**
> Welcome. Try 10.04 LTS from the LiveCD (the install CD and option 'Try Ubuntu'). If everything works ok then install. You may have more luck and a smoother ride as is stable release. (Longer support also.) ;)

2/ Right-click and create shortcut (you can also drag from 'Applications' menu).

4/ No need to analyse. Install all as all from Ubuntu (trusted) repositories at this point. May also fix some of your problems and pick up your wireless card (automatically download appropriate firmware/software).

To get wireless up you may need to get the updates in fact.
Will 10.04 have a greater chance of the wireless working straight out of the box (or atleast with minor, easily fixed problems)?
Or will it be more of a lag fixer?

Shortcuts created! :guitar:

I updated and still no help for the wireless.

1/3, I'm a linux master! :p

---

### Post by yuri nator on 2011-02-09
> **sydbat said:**
> Most things are simple in Linux!

As for your problems, can you tell us how you installed Ubuntu? Was it with wubi? If so, this could explain the lagginess and wireless issues.

Because wubi is a virtual machine running inside Windows and is reliant on the Windows file system, major corruption in your Ubuntu filesystem can occur if Windows was not properly defragmented before proceeding with a wubi install.
I'm not exactly sure, it was straight from the cd. It's running side by side with win7, but not within as far as I understand. (On start up, it gives the options of which OS to boot)

---

### Post by yuri nator on 2011-02-09
> **gordintoronto said:**
> You could also mention what kind of computer this is.

This message thread might help you with the wireless:
[http://ubuntuforums.org/showthread.php?t=1420901](http://ubuntuforums.org/showthread.php?t=1420901)

I found it by Googling: intel 6300n ubuntu

More people use Ubuntu than Kubuntu, so you might find it easier to get help with Ubuntu. Once you are feeling more confident, you could give Kubuntu a try.
No luck with the link as I can't find * linux-backports-modules-karmic, *and I have no idea how to do what's said in the first post.

---

### Post by Paqman on 2011-02-09
> **yuri nator said:**
> Will 10.04 have a greater chance of the wireless working straight out of the box (or atleast with minor, easily fixed problems)?
Or will it be more of a lag fixer?


Neither really. Since it's an older version it's likely to have driver support that isn't as good as recent versions. Not much worse, because it's not that much older, but in general I don't think you're likely to gain anything by reinstalling an older version.

LTS versions of Ubuntu aren't any more or less stable, they're just supported for longer.

> 
I updated and still no help for the wireless.


Seems like some people have had trouble with that wifi card. Does it work at all, or are you getting slow speeds?

---

### Post by yuri nator on 2011-02-09
> **Paqman said:**
> Neither really. Since it's an older version it's likely to have driver support that isn't as good as recent versions. Not much worse, because it's not that much older, but in general I don't think you're likely to gain anything by reinstalling an older version.

LTS versions of Ubuntu aren't any more or less stable, they're just supported for longer.



Seems like some people have had trouble with that wifi card. Does it work at all, or are you getting slow speeds?
Thanks.

It doesn't work at all as far as I know.The computer knows it's there from doing a *sudo lshw -C network* , but no connection.

---

### Post by Paqman on 2011-02-09
> **yuri nator said:**
> No luck with the link as I can't find * linux-backports-modules-karmic, *and I have no idea how to do what's said in the first post.

The first guy is trying to fix it for Jaunty, which is an old version. The second guy was running Karmic, which is another old version. You're running Maverick, which is why your system didn't find the Karmic package (which you'll have in your system anyway, since it's a backport)

---

### Post by yuri nator on 2011-02-09
> **Paqman said:**
> The first guy is trying to fix it for Jaunty, which is an old version. The second guy was running Karmic, which is another old version. You're running Maverick, which is why your system didn't find the Karmic package (which you'll have in your system anyway, since it's a backport)
I see.

Should I be installing any of the wireless backport modules that I have found with KPackageKit?

---

### Post by Paqman on 2011-02-09
> **yuri nator said:**
> I see.

Should I be installing any of the wireless backport modules that I have found with KPackageKit?

Depends, what are they called?

---

### Post by yuri nator on 2011-02-09
> **Paqman said:**
> Depends, what are they called?
There are about 18, with name descriptions such as:
Wireless drivers for generic kernal image.
Compat wireless linux modules for version 2.6.35 on x86/64

---

### Post by Dutch70 on 2011-02-09
Have you tried clicking on the network manager icon on your panel?  

if not then left click on it, make sure "enable networking" & "enable wireless on the left are checked.

Click on "manage connections" > select the "wireless" tab. > click  on "add" on the right, Then under the wireless tab, click on "scan" it should say SSID in front of it. See if that finds your connection.

---

### Post by yuri nator on 2011-02-09
> **Dutch70 said:**
> Have you tried clicking on the network manager icon on your panel?  

if not then left click on it, make sure "enable networking" & "enable wireless on the left are checked.

Click on "manage connections" > select the "wireless" tab. > click  on "add" on the right, Then under the wireless tab, click on "scan" it should say SSID in front of it. See if that finds your connection.
Wireless is enabled under interfaces (one click on the panel).
Once I'm into "manage connections" wireless is not highlighted and I can;t click on it.   I try to "add", there is no option for wireless. There is only an add new ethernet connection,
with ethernet, IP Address, 802.1x security.

---

### Post by Dutch70 on 2011-02-09
Sorry, I wouldn't know then. Could it have something to do with your wireless security?

Maybe someone with more experience will be more help.
good luck

---

### Post by mastablasta on 2011-02-09
> **yuri nator said:**
> No luck with the link as I can't find *linux-backports-modules-karmic, *and I have no idea how to do what's said in the first post.
 
 
Did you download the firmware and extract it to the folder as it is written in the post?
 
as for second this th epackage will porbably something like *linux-backports-modules-maverick *or something similar.

---

### Post by yuri nator on 2011-02-09
> **mastablasta said:**
> Did you download the firmware and extract it to the folder as it is written in the post?
 
as for second this th epackage will porbably something like *linux-backports-modules-maverick *or something similar.
No I didn't as I don't know how to *"decompress it and copy the ucode in /lib/firmware.*" 

There are a few different versions; generic kernal image, server kernal image, modules wireless, modules compat wireless, 2.6.35.25.32,  2.6.35.22.12  etc
I have no idea what is what. 

:confused:

---

### Post by mastablasta on 2011-02-09
when you donwload the file it will appear in your downloads folder. then you just right click it and choose extract here or something like that. then it will extract and then you can copy as i see in instructions. i hope that is enough for it to work (as per the user that posted this solution). i am not sure if you need to reboot afterwards or no. 
 
i would try following instructions in that post. maybe you don't even need to add those modules.

---

### Post by yuri nator on 2011-02-09
> **mastablasta said:**
> when you donwload the file it will appear in your downloads folder. then you just right click it and choose extract here or something like that. then it will extract and then you can copy as i see in instructions. i hope that is enough for it to work (as per the user that posted this solution). i am not sure if you need to reboot afterwards or no. 
 
i would try following instructions in that post. maybe you don't even need to add those modules.
It says I have to find out if the support is enabled in the kernel. I don't know how to do anything in the install guidelines, nor understand what they're talkig about. 
Currently, the only things I know how to find in Kubuntu are the browser, anything easily seen in the Kickoff application launcher (Kubuntu version of a windows Start button) and what's on the taskbar. 


2. INSTALLATION

The iwlagn driver will look for the file iwlwifi-6000-4.ucode using the 
kernel's firmware_class infrastructure. More information can be found under
Documentation/firmware_class in kernel source. In order to function
correctly, you need to have this support enabled in your kernel.  When 
you configure the kernel, you can find this option in the following 
location:

        Device Drivers ->
                Generic Driver Options ->
                        Userspace firmware loading support


You can determine if your kernel currently has firmware loader support 
by looking for the CONFIG_FW_LOADER definition on your kernel's 
.config.

In addition to having the firmware_class support in your kernel, you
must also have a working udev and uevent infrastructure configured.
The steps for installing and configuring udev are very
distribution specific. 

Once you have the firmware loader in place (or if you aren't sure and 
you just want to try things to see if it works), you need to install 
the microcode file into the appropriate location.

Where that appropriate location is depends (again) on your system 
distribution.  You can typically find this location by looking in the 
udev scripts of your distro, the default is /lib/firmware.

Installation of the firmware is simply:

        % cp iwlwifi-6000-4.ucode /lib/firmware

You can now load the driver (see the INSTALL and README.iwlwifi provided with
the iwlwifi package for information on building and using that driver.)



:redface:

---

### Post by migs73 on 2011-02-09
A bit of long shot, but no one has asked as far as I could see;

Assuming you are using a laptop.

Is your wireless 'on'?
Is the light to tell you it is enabled lit up on your laptop? 
Is there a switch to switch it on (or a Fn+keystroke combo to enable it)?

---

### Post by Paqman on 2011-02-09
> **yuri nator said:**
> There are about 18, with name descriptions such as:
Wireless drivers for generic kernal image.
Compat wireless linux modules for version 2.6.35 on x86/64

Of those, the one I would install would be:
```
linux-backports-modules-wireless-maverick-generic 
```

This is a meta-package that will always depend on the latest wifi modules that are backported. Go ahead and install it and see if it makes any difference. It should do no harm at least, but Maverick is pretty recent, so i'm not terribly confident that you've had updated drivers backported yet.

Bit of a stab in the dark, i'm afraid. You might get more knowledgeable help in the networking forum instead of Absolute Beginners. That's where the experts will be hanging out.

A bit of background: normally the software in the repositories is kept pretty stable on any one version of Ubuntu. Sometimes however important updates are issued that Ubuntu wants to push out to all the old versions, instead of just what new version ois coming out. These updates are called backports. Obviously they're more useful if you're running an older version.

---

### Post by Bucky Ball on 2011-02-09
You need to be online with a cable and get updates. It may work out of the box then but you may have already tried that. I mentioned it posts ago. ;)

---

### Post by yuri nator on 2011-02-09
> **migs73 said:**
> A bit of long shot, but no one has asked as far as I could see;

Assuming you are using a laptop.

Is your wireless 'on'?
Is the light to tell you it is enabled lit up on your laptop? 
Is there a switch to switch it on (or a Fn+keystroke combo to enable it)?
It's not on, but the button to turn it on doesn't seem to work in kubuntu. It works in Windows, so I'm not sure what's going on there.

The bluetooth light will turn on via Fn+key, but wireless won't. I'm not even sure there is a wireless FN+key, there's an upside down triangle elevated on a "stick/line", but even that has no effect. :confused:

---

### Post by yuri nator on 2011-02-09
> **Paqman said:**
> Of those, the one I would install would be:
```
linux-backports-modules-wireless-maverick-generic 
```This is a meta-package that will always depend on the latest wifi modules that are backported. Go ahead and install it and see if it makes any difference. It should do no harm at least, but Maverick is pretty recent, so i'm not terribly confident that you've had updated drivers backported yet.

Bit of a stab in the dark, i'm afraid. You might get more knowledgeable help in the networking forum instead of Absolute Beginners. That's where the experts will be hanging out.

A bit of background: normally the software in the repositories is kept pretty stable on any one version of Ubuntu. Sometimes however important updates are issued that Ubuntu wants to push out to all the old versions, instead of just what new version ois coming out. These updates are called backports. Obviously they're more useful if you're running an older version.
I downloaded the package and still no effect. :(

I might give the networking forum a go, I just hope they're tolerant of a newb. :oops:

---

### Post by yuri nator on 2011-02-09
> **Bucky Ball said:**
> You need to be online with a cable and get updates. It may work out of the box then but you may have already tried that. I mentioned it posts ago. ;)
I think I've got all the recommended updates by Kubuntu, but I'm not sure which other updates I may need.
I got backport-wireless-generic update too, but I've got no idea of any other updates I my need. :confused:

---

### Post by Bucky Ball on 2011-02-10
Applications>Administration>Additional Drivers. Anything there?

---

### Post by yuri nator on 2011-02-10
> **Bucky Ball said:**
> Applications>Administration>Additional Drivers. Anything there?
I don't seem to have an administration option.
I'm using Kubuntu if that differs in this area from Ubuntu.

---

### Post by NightwishFan on 2011-02-10
Search "hardware" in the kde menu.

---

### Post by yuri nator on 2011-02-10
> **NightwishFan said:**
> Search "hardware" in the kde menu.
Thanks.
I've got Hardware Lister (labled as "lshw" in the program windows header) open.
Under a PCI Bridge then Network Controller  I can find the wireless card with the name of the card and a brief description; Product, Bus Version, Clock etc


I can't find anything about drivers though.

---

### Post by yuri nator on 2011-02-10
I found the additional drivers area, but no drivers to add. :sad:

---

### Post by Paqman on 2011-02-10
> **yuri nator said:**
> 
I might give the networking forum a go, I just hope they're tolerant of a newb. :oops:

You seem like a nice person, i'm sure you'll be fine :)

---


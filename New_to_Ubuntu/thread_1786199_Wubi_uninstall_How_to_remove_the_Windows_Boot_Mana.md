---
title: "Wubi uninstall: How to remove the Windows Boot Manager from showing up"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2011-06-19
Okay, I know this may sound ridiculous--I should know how to do this, but Iam failing all attempts to restore Windows Boot Manager to not show at all.

(1) I had Ubuntu in Windows installation using Wubi (11.04)
(2) I have uninstalled Ubuntu from Windows 7
(3) When I reboot, the Windows Boot Manager (WBM) still appears, but this time with only Windows as an entry--Ubuntu is removed. (See the screenshot--this is when Ubuntu was still installed)
(4) What I want is WBM to not appear at all when each time I boot. I have tried
(a) Using Windows disc and going to command prompt and typing > fixmbr or even fixboot; but this does not help; the WBM still appears with the Windows entry.
(b) I have checked C:/ for Wubi left overs, that drive is clean and no wubi debris in there.

Can anyone help me get past this point? I want Windows to boot directly without passing through the Windows Boot Manager. Please assist.

Thanks,
SWB:(

---

### Post by Frogs Hair on 2011-06-19
What you are experiencing may be due to a Windows registry key . Check out the removal section at the link.[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by shuttleworthwannabe on 2011-06-19
I tried that solution, but alas, I guess that is not it--anything else?

---

### Post by Sergio.G on 2011-06-19
Hope I can be any help, here it goes:

In Windows 7, click on start then write: msconfig
then in the system configuration window select the Boot tab
and select Windows 7 and click "set as default" button

I think by doing this, the WBM option will not show up at boot time again

Other Method:
(I suggest you try the method above first)
There is another method but with this you delete the unnecessary boot loader entries and boot up directly to Win7

Note:
You have to be careful if you you will mess up your windows boot loader, being said that, here we go:
(you should run the command line as Administrator)

Open up the command prompt and type: ```
bcdedit
```

It will display a list of the entries ( there you'll find the Ubuntu entry) and the Windows Boot Loader entry as well. 

Pay attention to the identifier which is the name of the entry you are searching for, 
by now I don't remember but I think it is identified as Ubuntu

Now, before anything else you should make a back up of your current Boot Manager config, type:

```
bcdedit /export
``` 

Now lets delete entry, type
```
bcdedit /delete {***_identifier_***} /f
```

Replace ***identifier*** with the ubuntu identifier 

Once the operation is completed, it should display a message notifying the success of it. 

Don't know how comfortable you are modifying this kind of files, if you like, post back a screenshot with the list retrieved by the bcedit command

Hope it helps
Cheers

---

### Post by Sergio.G on 2011-06-19
Double post...

---

### Post by shuttleworthwannabe on 2011-06-20
Thanks Sergio.G.

The msconfig approach is what I did to reduce the timeout--see screenshot, there is only Windows & listed in the menu; so what this (timeout set to 0) does is as soon as the BIOS screen screen disappears, the WBM appears but snaps away immediately (you can actually see the WBM for split second or so). This is annoying.

Anyway I hope that ago the wubi creator can come in here to help--I have searched almost everywhere, but to no avail.

Swb

---

### Post by Sergio.G on 2011-06-20
This happened to me also, once that Wubi/Ubuntu is removed from Windows for some reason the boot loader wasn't updated and yes it is annoying :)

Did you try the *bcdedit* command from within Windows?

Just display the list with the command and post back the screenshot 

Cheers

---

### Post by beew on 2011-06-20
So I really wonder what the hell is the advantage of WUBI. It even messes up windows while the whole point is that you can test Ubuntu with least disruption of your existing machine. Fact is it is buggy, it doesn't give a true picture of Linux performance and thus gives Ubuntu a bad name and even screws up Windows.

I am now typing from a test install of Xubuntu 11.04 in an 8 G usb flash drive. It is a full install (not a live usb with persistence) the kernel is upgraded to 2.6.39. It is not very fast due to the limitation of the usb drive but it is a lot better than WUBI and it won't mess up your internal OS, whatever it is (mine is Ubuntu)

---

### Post by Sergio.G on 2011-06-20
> **beew said:**
> So I really wonder what the hell is the advantage of WUBI. It even messes up windows while the whole point is that you can test Ubuntu with least disruption of your existing machine. Fact is it is buggy, it doesn't give a true picture of Linux performance and thus gives Ubuntu a bad name and even screws up Windows.

I am now typing from a test install of Xubuntu 11.04 in an 8 G usb flash drive. It is a full install (not a live usb with persistence) the kernel is upgraded to 2.6.39. It is not very fast due to the limitation of the usb drive but it is a lot better than WUBI and it won't mess up your internal OS, whatever it is (mine is Ubuntu)

I agree with you, it does not give Ubuntu a good reputation.

If someone asks me about if I would recommend WUBI as an alternative to test Ubuntu, I would say NO, better test Ubuntu setting up a Virtual Machine, that is my honest and humble opinion of course, maybe some other folks never had a problem with WUBI.

Technically speaking, I was intrigued and impressed maybe, with the fact of installing another OS inside Windows, I hadn't heard of that before and I just felt a little more geek haha! :)

I used WUBI when Ubuntu 10.04 was released, used it for about 2 months, but I was always afraid that something might break, a lot of people in the community was saying at that time, WUBI was not stable and not a good option for a long term usage. 

Until one day I updated Ubuntu using the update manager and  GRUB, GRUB-PC or GRUB common or a package like that messed up something, those were the only packages in my update list, then was not able to boot into Windows, had to use a restore disk to fix the MBR, it was really not a good option, don't know now if the new versions are improved. 

Despite this I didn't give up on Ubuntu, I liked what I tried using WUBI and now I couldn't be happier with my current setup.

Cheers

---

### Post by shuttleworthwannabe on 2011-06-20
Hi Sergio.G again,


> C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {c22c67ff-954c-11e0-a9de-d835e1912c85}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 0
displaybootmenu         Yes

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {c22c6801-954c-11e0-a9de-d835e1912c85}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {c22c67ff-954c-11e0-a9de-d835e1912c85}
nx                      OptIn
usefirmwarepcisettings  No

Does this help?

---

### Post by shuttleworthwannabe on 2011-06-20
My only reason to use WUBI is because my IT guys do not want me to mess with paritions on company harddrive--I use Ubuntu through Wubi-in the past removing Wubi was a breeze, adn WBM and Loader would restore itself immaculately; I have noticed since 10.04 this is a mission. and yes, using Ubuntu with partitioning is the best.

---

### Post by beew on 2011-06-20
> **shuttleworthwannabe said:**
> My only reason to use WUBI is because my IT guys do not want me to mess with paritions on company harddrive--I use Ubuntu through Wubi-in the past removing Wubi was a breeze, adn WBM and Loader would restore itself immaculately; I have noticed since 10.04 this is a mission. and yes, using Ubuntu with partitioning is the best.

Then install in an external hard drive, or even a 16G usb flash drive. WUBI installs something in Windows, and the method I recommend doesn't and you get a lot better performance too (if you use an external hard drive, with flash drive it can be a bit slow)

---

### Post by Sergio.G on 2011-06-20
Ok, was doing a little research and found something that might help, it is an utility named EasyBCD

The link to download the utility is at the bottom of the page, here is the link:

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

Found a forum where the original poster verified that the solution worked for him.

Here is the link of the forum:

[http://forums.whirlpool.net.au/archive/1033528]("http://forums.whirlpool.net.au/archive/1033528")


Once installed, run the application:
 
Click on the button Edit Boot Menu, 
Select the entry you want to delete and 
Click Delete button.

Cheers

---

### Post by shuttleworthwannabe on 2011-06-20
> **beew said:**
> Then install in an external hard drive, or even a 16G usb flash drive. WUBI installs something in Windows, and the method I recommend doesn't and you get a lot better performance too (if you use an external hard drive, with flash drive it can be a bit slow)

That would be ideal--but my attempts to install Ubuntu on an external hdd have resulted in a non-bootable hdd; and trouble shooting through that was a long story. I have yet to find a simple step-by-step guide to the the external hdd isntall that actually does work. Do you have a suggestion?

---

### Post by shuttleworthwannabe on 2011-06-20
> **Sergio.G said:**
> Ok, was doing a little research and found something that might help, it is an utility named EasyBCD

The link to download the utility is at the bottom of the page, here is the link:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Found a forum where the original poster verified that the solution worked for him.

Here is the link of the forum:

[http://forums.whirlpool.net.au/archive/1033528](http://forums.whirlpool.net.au/archive/1033528)


Once installed, run the application:
 
Click on the button Edit Boot Menu, 
Select the entry you want to delete and 
Click Delete button.

Cheers

I should have mentioned that I am using EasyBCD--it has helped me in the past; but this time the Wubi WBM/L just does not want to bugde!

Also I have check that forum out before--it is attempting to remove Ubuntu entry from the WBM/L--which is quite easy to do in EasyBCD--and I have done that; my problem now is that the WBM/L still shows up on bootup, even if I have timed out it to 0. That is what I want to get rid off; leaving no trace that Ubuntu wasever installed on this machine.

I may try this option:
(1) Insert Windows 7 DVD
(2) Repair
(3) select Os to repair
(4) cmd prompt> bootrec.exe /fixmbr

I will do this when I am at home with my dics later in the day.

---

### Post by unapendeza on 2011-06-20
> **shuttleworthwannabe said:**
> Okay, I know this may sound ridiculous--I should know how to do this, but Iam failing all attempts to restore Windows Boot Manager to not show at all.

(1) I had Ubuntu in Windows installation using Wubi (11.04)
(2) I have uninstalled Ubuntu from Windows 7
(3) When I reboot, the Windows Boot Manager (WBM) still appears, but this time with only Windows as an entry--Ubuntu is removed. (See the screenshot--this is when Ubuntu was still installed)
(4) What I want is WBM to not appear at all when each time I boot. I have tried
(a) Using Windows disc and going to command prompt and typing > fixmbr or even fixboot; but this does not help; the WBM still appears with the Windows entry.
(b) I have checked C:/ for Wubi left overs, that drive is clean and no wubi debris in there.

Can anyone help me get past this point? I want Windows to boot directly without passing through the Windows Boot Manager. Please assist.

Thanks,
SWB:(

When you first turn on your computer it should say "press F12 for boot manager" or something along the lines of that. Press that F key and change your settings so you automatically boot into Windows. 
Or you can always just reinstall Ubuntu from a USB.

---

### Post by bcbc on 2011-06-20
Click Start, enter "cmd", right click "cmd.exe" and Run as Administrator. Then:
```
bcdedit /set {bootmgr} displaybootmenu No
```

---

### Post by shuttleworthwannabe on 2011-06-20
> **bcbc said:**
> Click Start, enter "cmd", right click "cmd.exe" and Run as Administrator. Then:
```
bcdedit /set {bootmgr} displaybootmenu No
```

bcbc,

Man, you are my HERO!

It worked like a charm!

I am so relieved--I was about to do a clean Windows install just for this annoying problem.

Many thanks
swb

Thread [Solved]

---

### Post by jtarin on 2011-06-27
> **shuttleworthwannabe said:**
> Okay, I know this may sound ridiculous--I should know how to do this, but Iam failing all attempts to restore Windows Boot Manager to not show at all.

(1) I had Ubuntu in Windows installation using Wubi (11.04)
(2) I have uninstalled Ubuntu from Windows 7
(3) When I reboot, the Windows Boot Manager (WBM) still appears, but this time with only Windows as an entry--Ubuntu is removed. (See the screenshot--this is when Ubuntu was still installed)
(4) What I want is WBM to not appear at all when each time I boot. I have tried
(a) Using Windows disc and going to command prompt and typing > fixmbr or even fixboot; but this does not help; the WBM still appears with the Windows entry.
(b) I have checked C:/ for Wubi left overs, that drive is clean and no wubi debris in there.

Can anyone help me get past this point? I want Windows to boot directly without passing through the Windows Boot Manager. Please assist.

Thanks,
SWB:([http://www.howtogeek.com/howto/17903/remove-ubuntu-or-xp-from-the-windows-7-boot-menu/](http://www.howtogeek.com/howto/17903/remove-ubuntu-or-xp-from-the-windows-7-boot-menu/)

---

### Post by shuttleworthwannabe on 2011-06-27
If you look at the beginning of this thread, I tried [that]("http://www.howtogeek.com/howto/17903/remove-ubuntu-or-xp-from-the-windows-7-boot-menu/") solution, but only the one suggested by **bcbc** worked in getting rid of the interim windows boot loader screen.

---


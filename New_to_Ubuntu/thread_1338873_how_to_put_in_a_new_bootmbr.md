---
title: "how to put in a new bootmbr"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by nitstorm on 2009-11-26
i have a squeaky clean old HDD and i can install ubuntu on it ONLY with the pen drive, wen i try it, it says bootmbr missing, how do i put in a new BOOTMBR or the mbr of the system i am currently using onto that HDD...  
is there some way to do that by connecting the old HDD to the system and then putting in a new or some mbr ?

been breaking my head over this the past couple of days, please help guys...

---

### Post by nitstorm on 2009-11-27
if i use super grub disk will i be able to get a new mbr or something with the frugal install option? if yes, step-by-step procedure please..

also if i use unetbootin will i be able to install a new mbr along with the os on the old HDD by the frugal install option? if yes, step-by-step procedure for this too please...

---

### Post by nitstorm on 2009-11-27
bump?

---

### Post by nitstorm on 2009-11-27
hey guys this is really important for me. please do help....

---

### Post by nitstorm on 2009-11-28
anybody please????

---

### Post by nitstorm on 2009-11-29
bump?

---

### Post by bsharp on 2009-11-29
Boot up to a root shell from a livecd or your pendrive and mount the hdd you want to install grub to. Then use grub-install:

```
grub-install --root-install /path_to_mounted_drive /dev/your_hdd_here
```

---

### Post by nitstorm on 2009-11-29
i can only use a pendrive and wen i try to boot it jus says, unable to find bootmbr

---

### Post by mechro on 2009-11-29
We need some more information about your system.

I assume you have a computer with an internal Hard Drive from which you have a working Ubuntu?

You're trying to install another Ubuntu on to an external Hard Drive(old HDD?)?

Your computer may not be able to boot an external Hard Drive? If it can boot an external Hard Drive you might have to change the boot order in your BIOS.?

---

### Post by nitstorm on 2009-11-29
i have ubuntu 9.04 running on the comp i am running right now, the old hdd is from my old comp which i connect with my dvd drive's cable, wen i do that the dvd drive doesnt get detected only the hdd gets detected. i had wiped my old hdd clean using the windows disk management thing and now its squeaky clean. wen i try to install ubuntu on it, it says bootmgr missing. also tried changing the boot order. still the same issue

---

### Post by mechro on 2009-11-29
Connecting a hard drive with an optical drive cable is new to me but if it's SATA then it probably works. I have no idea.

I think bsharp gave you the answer but then you said you couldn't boot the pendrive?

---

### Post by nitstorm on 2009-11-29
yup even wen i insert the pendrive it says bootmbr missing

---

### Post by mechro on 2009-11-29
Ah, right! You're trying to fix your pendrive.

How and what did you install on your Pendrive? Have you got any links to show me what you did?

---

### Post by nitstorm on 2009-11-29
no no no!!! the pendrive is jus fine, its the hdd that has no bootmbr, i am wondering how i can put in a new bootmbr... 

and i jus used the usb startup disk creator program that comes by default...

---

### Post by mechro on 2009-11-29
I'm still not sure what you mean. You boot the pendrive and you ask it to boot old HDD but it says no bootmbr? What have you installed on old HDD? It won't have any sort of boot capability until you install something on it.

---

### Post by nitstorm on 2009-11-29
i mean the pendrive has the 9.10 for installation
i want to install it on the old hdd
there is nothing on the hdd
it says bootmbr missing

help please?

---

### Post by bsharp on 2009-11-29
Oh, I thought you had installed Ubuntu to the hdd, and tried to boot up when you got the no mbr message. You need to set your bios to boot from usb or use boot floppy to boot off the usb drive. Then you should be able to install.

---

### Post by mechro on 2009-11-29
What application are you using when you get the "bootmbr missing" message?
Is it a partition manager, the USB disk creator, what??

---

### Post by nitstorm on 2009-11-29
i was installing karmic from the pendrive if that's what u mean... and used the usb startup disk creator to burn the karmic image on the pendrive...

---

### Post by mechro on 2009-11-29
> **nitstorm said:**
> i was installing karmic from the pendrive if that's what u mean... 

Is that a boot menu option?

---

### Post by nitstorm on 2009-11-29
i dont understand... i mean i tried it for my friend, and it installs fine that way for him , not for me...

---

### Post by mechro on 2009-11-29
Sorry, got to go to work... night shift. I'll go and bang my head there. ;) If you're not solved by tomorrow, I'll look again.

Good Luck!

---

### Post by nitstorm on 2009-11-29
thanks man, i gotta go crash too. cheers! try solving this later please....

---

### Post by mechro on 2009-11-30
Right, as far as I can make out bootMBR or bootMgr is something to do with Windows. Are you sure your old HDD is "squeaky clean"? I can't figure out why doing an install is looking for a bootMBR. The whole point of doing an install is to load an operating system and configuring the boot (MBR - Master Boot Record) is one of the last things it does.

Anyway, when you boot your pendrive are you choosing the **Install Ubuntu** item from this menu?...

[IMG]https://help.ubuntu.com/community/LiveCD?action=AttachFile&do=get&target=804+Live+2+.png[/IMG]

Also can you keep all your drives plugged in and do the following... Open a Terminal from **Applications > Accessories > Terminal** and enter the following command...

```
sudo fdisk -l
```

If it asks for a password just press enter if you haven't set up a password. Post the results of the command here.

---

### Post by nitstorm on 2009-11-30
i dont even get that menu wen i boot, it jus boot with the old hdd and it tells me BOOTMBR missing, press ctrl+alt+del to restart, will boot with the old hdd and post the comment...

jus did it, but ubuntu won't detect the drive, gave me a message asking me to remove all disks and the press any key to restart...

n wen i did , it jus boots into ubuntu on my current hard-drive and doesn't detect the old one...
but wen i boot with windows, it detects the old hdd instead of the dvd drive which it does all the time on windows. is there something i can do on the old hdd with windows that'll help me install karmic on it. supergrubdisk or something like that will work?

---

### Post by presence1960 on 2009-11-30
> **nitstorm said:**
> i dont even get that menu wen i boot, it jus boot with the old hdd and it tells me BOOTMBR missing, press ctrl+alt+del to restart, will boot with the old hdd and post the comment...

jus did it, but ubuntu won't detect the drive, gave me a message asking me to remove all disks and the press any key to restart...

n wen i did , it jus boots into ubuntu on my current hard-drive and doesn't detect the old one...

Then one of two things is wrong. Either your machine can not or is not set to boot from USB or your USB (pendrive) has a faulty image on it and needs to be done over.

Check out the first option though. Go into BIOS and make sure your machine is set to boot from USB/Removable as first option. Is your pendive 4 GB or larger? On my BIOS any USB flash disk 4 GB or larger shows up under hard disk boot order in BIOS. Check your hard disk boot order in BIOS (with the pendrive plugged in of course) and see if it is listed there. if it is just move it to the top of the hard disk boot order. Save changes to CMOS and continue to boot.

---

### Post by nitstorm on 2009-11-30
hey jus another of my brainwaves here, what if i load the karmic or hardy heron image using daemon tools on windows and then run the wubi installer from windows and install it on the old hdd? will that work? if yes, will that wipe out both my drives???? the old hdd and the new one???

---

### Post by jrweiss on 2009-11-30
Can you boot from the pen drive on any other machine?  You have to have SOME bootable drive to install an OS, whether it is an HD, DVD/CD, or pen drive.

If you can boot from the pen drive on a different machine, but not the one with the "clean" HD, then you will have to set your BIOS to boot from USB.  Not all BIOS versions will allow that, so it may require a BIOS update first.  What kind of computer, BIOS version, configuration, HD, pen drive type, etc is the one at issue?

You might also try downloading the live CD version of GPartEd, and try formatting and partitioning the HD before attempting the install.  Once you boot from the GPartEd CD, you might also be able to get to the pen drive from there.  If there is no internal CD, borrow an external...

---

### Post by nitstorm on 2009-11-30
hey guys, i jus did a wubi install of hardy heron on the old hdd by mounting it on daemontools in windows. it installed well but i can only use the hardy heron only wen i go under windows from the boot menu first which then guides me to another boot menu and another one after that... i tried booting with old hdd alone and i got the following error:

Remove disks or other media.
Press any key to restart.
No bootable device-insert boot disk & press any key


@presence 1960 : i did that, the 4gb kingston pendrive shows up along with the other hdd
@jrweiss: i use a core2duo, 2 gb ram, no idea about the bios version, the old hdd is a seagate hdd, bought it about 6 and a half years ago along with the old comp, i connect it to the new comp(newer comp :P ) using the dvd drive's cable. 

jus try posting the solution guys, will check it in three days. got my semester exams going on. will be done by it then. thanks a lot for all u have done, and also for what u are going to do. please do post the solutions guys. cheers!

---

### Post by mechro on 2009-11-30
So earlier, when you stated that "the pendrive is jus fine" it turns out that it isn't.

Sorry, nitstorm, I don't wish to appear unhelpful or unfriendly but that is extremely bloody annoying! ;):D

---

### Post by nitstorm on 2009-12-03
actually, wen i was talking about it saying " no bootable device" i was doing it without a pendrive, and seems my friend has lost my pen drive, so should take me a while before i can install anything on that hdd....

---

### Post by nitstorm on 2009-12-31
i finally got it to work, after the wubi install of hardy heron on the old hdd, i jus put the old hdd onto the old cpu (which i had to buy some new parts for smps and stuff so that's why this post is so delayed ) and was able to install xubuntu, i have problems with the performance on running it on such a slow system , will start a new thread for it , thanks for all ur help guys and sorry for this thread being dormant for so long , cheers

THREAD SOLVED !!!

---


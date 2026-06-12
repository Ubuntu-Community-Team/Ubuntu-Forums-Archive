---
title: "Some quick questions"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by dk21 on 2008-12-29
Hi.

After several tries (and several distros), im thinking about installing 8.10 in my laptop. Before install, i have some questions:

- I'm currently using Vista. Is there any problem about boot loader?

- In my laptop (Toshiba A200-21T) I have an Ati Radeon HD2600. Is there any Howto install drivers (to enable compiz)?

- Anyone has a laptop like my one, or with the same graphics card? I would like to get some feedback...

- I'm running out of space... If I install ubuntu in a 5Gb partition, can I later resize it with no problems?

Thanks in advence, and sorry for my english. (I'm from Portugal)

---

### Post by gjoellee on 2008-12-29
> **dk21 said:**
> Hi.

After several tries (and several distros), im thinking about installing 8.10 in my laptop. Before install, i have some questions:

- I'm currently using Vista. Is there any problem about boot loader?

- In my laptop (Toshiba A200-21T) I have an Ati Radeon HD2600. Is there any Howto install drivers (to enable compiz)?

- Anyone has a laptop like my one, or with the same graphics card? I would like to get some feedback...

- I'm running out of space... If I install ubuntu in a 5Gb partition, can I later resize it with no problems?

Thanks in advence, and sorry for my english. (I'm from Portugal)

-Most distributions are using GRUB which Ubuntu does. The problems won't be differet if there are any... (though Vista might cause some)

-It is pretty easy. You can install drivers by going to System->Administration->Hardware Drivers (or something like that), it is done with a click on your mouse. 

You can install Compiz Fusion from "Synaptic", "Add/Remove", 

"APTURL" (one click install) go to the following link: [http://kshoster.net/node/14](http://kshoster.net/node/14) and find "Advenced Desktop Effect Settings (Compiz Fusion)" wait a few seconds and a window should pop-up. Click on "Install".

"Terminal" using this command: ```
sudo apt-get install compizconfig-settings-manager
```

to enable Compiz go to System->Prefrences->Sessions and add compiz to startup:
Name: Compiz
Command: compiz --replace
Comment: Eye Candy

-Ubuntu should install on a 5gb HDD, installing applications later may be a problem

-If I shoul be very correct you wrote "english" (with little "e") it should be a big "E". As well "advence" is "advance" i guess. Your English is not bad at all!

---

### Post by dk21 on 2008-12-29
Lots of people say that linux's big problem is lack of support... They still don't know this forum... Very quick, Thanks...

In others distros i've tryed before, I felt the big trouble in installing a ATI graphics card... It didn't worked at all...

As I know, there are two kinds of drivers: open source and proprietary... Witch one works better? Or can you explain me this?

Once again, Thanks a lot

PS: advance... I knew it... Thanks

---

### Post by dk21 on 2008-12-29
One more question. I have 3GB Ram. How big sould I create Swap partition?

I'm running out of space...

---

### Post by albinootje on 2008-12-29
> **dk21 said:**
>  - I'm running out of space... If I install ubuntu in a 5Gb partition, can I later resize it with no problems?


After installation the Linux partition probably will take less than 1.5 Gb, and the size of a swap partition can vary depending on what was offered during the installation.

Resizing can be done by using gparted.

Before you install Ubuntu, you can actually run a "live session" from the 8.10 installation cdrom.
Then you can already get an idea about how well Ubuntu will run, although running from a cdrom- or dvd-drive is slower than from a hard disk.

---

### Post by albinootje on 2008-12-29
> **dk21 said:**
> One more question. I have 3GB Ram. How big sould I create Swap partition? 
With 3 Gb of RAM you can actually skip the swap partition.
Later you can create a swapfile if you really would need swap.

---

### Post by dk21 on 2008-12-29
Thanks... And what about graphics... I'm realy concerned about how to install it, cause the last time (with 8.04), I really could'n...

---

### Post by mal_conductor on 2008-12-29
> **dk21 said:**
> 
As I know, there are two kinds of drivers: open source and proprietary... Witch one works better? Or can you explain me this?


Everything that comes on the Ubuntu (or any distro) CD has to be open source.  That means that the code of the programs has to be available to be seen.

Some companies do not like that.  i.e. the manufacturer of a piece of equipment may not want to show everone the code of their drivers.  So, these drivers do not get included in the distro CD.

Most likely manufacturers do not write drivers for Linux because the market share is not large enough yet.  Some manufacturers do write drivers for linux but they do not want to disclose the source; so, these drivers are not included in the distro CD's.  You have to go get these drivers from the manufacturer's website or from driver repositories maintained by friends of Linux.  You can use the driver for free, but because the owner does not want to disclose the code, these drivers are not included in the distro CD.

There are also projects, labs and generous developers who "write" drivers for Linux.  These are people who want to make Linux more widely used and write drivers to make it easier for you and me.  These are not "copies" of the drivers from the manufacturers.  These people take a piece of hardware and start playing with it until they figure out how to make it work and write a program to make it work on Linux.  These drivers are open source and likely included in the Distro CD.

So which drivers are better?  You may not have a choice.  The manufacturers either wrote a driver for Linux or they didn't.  If they did not write a driver for Linux be happy if one of these generous labs has taken the time to "create" a driver for you.  There are a few (very few now a days) pieces of equipment that do not have drivers for Linux.  Most consumer market equipment now HAS drivers for it to work on Linux.

Hope it helps.

---

### Post by albinootje on 2008-12-29
> **dk21 said:**
> Thanks... And what about graphics... I'm realy concerned about how to install it, cause the last time (with 8.04), I really could'n...

I've just searched for "ATI Radeon HD2600" ubuntu 8.04
and found this :
[http://www.mickinator.com/nucleus/index.php?catid=3&blogid=1&archive=2008-04](http://www.mickinator.com/nucleus/index.php?catid=3&blogid=1&archive=2008-04)

See section "04/04: ATI Radeon HD2600 on mintLinux"
It's looks very similar for the howto at the top of that webpage for Ubuntu on an ATI HD2400.

---

### Post by dk21 on 2008-12-30
I will start it today... Will be easy, I hope...

One more question I've forgotten... 8.10 comes with KDE4 or KDE3? KDE4, right?

Thank you all for helping me...

---

### Post by RomeReactor on 2008-12-30
Hi. Kubuntu 8.10 *does* come with KDE 4.

---

### Post by dk21 on 2008-12-30
So Ubuntu too, right?

Thanks

---

### Post by mangurt on 2008-12-30
Ubuntu is gnome based.  Kubuntu is KDE based.  If you want to run KDE, then you need to download Kubuntu.

---

### Post by albinootje on 2008-12-30
> **dk21 said:**
> I will start it today... Will be easy, I hope...

One more question I've forgotten... 8.10 comes with KDE4 or KDE3? KDE4, right?

Thank you all for helping me...

KDE4, I'm not sure, but here are instructions to get KDE-4.2-beta-2 on your Kubuntu 8.10 installation :
[http://www.kubuntu.org/news/kde-4.2-beta-2](http://www.kubuntu.org/news/kde-4.2-beta-2)

---

### Post by dk21 on 2009-01-02
I finally made it...

After installing, I was surprised by a windows asking me to install ATI drivers... Great... After rebooting my hd2600 was intalled...

So, three words: oh my god!!! Something has changed from 8.04 to 8.10... It's preety easy...

I would like too say thanks for all support from this forum... You are amazing...

Thanks to all.

---


---
title: "Installing Lubuntu 10.10 on Netbook"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Ahunt on 2010-12-07
I have a friend who reported this problem to me and we duplicated the problem here at our house as well.

We downloaded the Lubuntu 10.10 ISO and conducted an MD5 sum check on it. It checked as a good download. The ISO was burned to CD-Rs and CD-RWs and tested using the internal CD test function and all copies tested fine, no errors. The CDs have been used to do several successful installations of Lubuntu.

In using Ubuntu 10.04's  "Startup Disk Creator" to write the Lubuntu ISO to a USB stick the write seemed to go well, but in testing the stick using the same internal test it returned 115 errors. This was duplicated several times. In checking though Launchpad and here on the forums I couldn't find the problem listed, although the [Lubuntu 10.10 release notes]("https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat") do state, rather vaguely:

"**Installer may be unstable when installing with USB**
The installer could be unstable if you convert the iso to an usb bootable media. Especially, installation on eeePC seems problematic."

Other than booting the netbook from an external CD drive (which I don't have access to) is there another way to write the USB stick or any other alternative for installing Lubuntu on a netbook?

Any help is greatly appreciated.

---

### Post by beew on 2010-12-07
Lubuntu is buggy. I installed it for 2 days in an old machine, many things didn't work: it wouldn't find my drivers, drag and drop didn't work, quick search in Synaptic didn't work (because they took out the indexing module or whatever it is called, you have to reinstall it, it is cheating to make the distro looks "light" by removing essential parts which you have to later reinstall anyway) God knows what else was broken.

Instead I installed Maverick but used openbox instead of gnome. It was just as fast as Lubuntu except everything works!

---

### Post by amjjawad on 2010-12-07
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by amjjawad on 2010-12-07
> **beew said:**
> Lubuntu is buggy. I installed it for 2 days in an old machine, many things didn't work: it wouldn't find my drivers, drag and drop didn't work, quick search in Synaptic didn't work (because they took out the indexing module or whatever it is called, you have to reinstall it, it is cheating to make the distro looks "light" by removing essential parts which you have to later reinstall anyway) God knows what else was broken.

Instead I installed Maverick but used openbox instead of gnome. It was just as fast as Lubuntu except everything works!

You know that I have it installed on one of my PCs and I have no problem with it at all, neither during installation nor after that ;)

By the way, long time no see :D

---

### Post by Ahunt on 2010-12-07
> **amjjawad said:**
> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks for that link, I take it you have used it specifically on Lubuntu as that seems to be problematic compared to Ubuntu Netbook Remix which works fine from the Ubuntu "Startup Disk Creator"?

We too have had no serious problems with Lubuntu on the desktop, it runs fast and smoothly. The main thing was not trying to install the encrypted directory, which broke just about everything. Other than that it runs very well now that it has had some updates since its release in October, which have fixed a few minor glitches.

---

### Post by amjjawad on 2010-12-07
> **Ahunt said:**
> Thanks for that link, I take it you have used it specifically on Lubuntu as that seems to be problematic compared to Ubuntu Netbook Remix which works fine from the Ubuntu "Startup Disk Creator"?

You welcome :)
I installed Lubuntu on one of my PCs (check my signature) long time ago, perhaps 2 months now. I used the LiveCD but I'm using or I've used UNetbootin many times, only once was unsuccessful so I had to re-create the LiveUSB (using UNetbootin again). With Ubuntu's tool to create LiveUSB, it's just not my cup of tea :)

I recommended UNetbootin because it's very popular and I have personally used it to install Linux many times on my two PCs. You see I have Multi-Boot Systems so you can tell how many times I have used that :)


> We too have had no serious problems with Lubuntu on the desktop, it runs fast and smoothly. The main thing was not trying to install the encrypted directory, which broke just about everything. Other than that it runs very well now that it has had some updates since its release in October, which have fixed a few minor glitches.

No OS is perfect :)
Usually, updates fix some/many stuff.

---

### Post by Ahunt on 2010-12-07
Okay, thank you for that information. I'll give it a try and see what results we get and report back on this thread!

---

### Post by amjjawad on 2010-12-07
> **Ahunt said:**
> Okay, thank you for that information. I'll give it a try and see what results we get and report back on this thread!

You most welcome and wish you all the best :)

I see you're trying to convert people to Linux :D GOOD JOB!

---

### Post by Ahunt on 2010-12-07
Well I try not to be too preachy about Linux, but we distribute a lot of Ubuntu CDs that we make up though our not-for-profit ISP's office.

I have written up my Lubuntu experiences on [my website]("http://web.ncf.ca/adamandruth/ubuntu2.html"), with lots of links and details.

---

### Post by amjjawad on 2010-12-07
> **Ahunt said:**
> Well I try not to be too preachy about Linux, but we distribute a lot of Ubuntu CDs that we make up though our not-for-profit ISP's office.

I have written up my Lubuntu experiences on [my website]("http://web.ncf.ca/adamandruth/ubuntu2.html"), with lots of links and details.

That's the best we can do :)
One day, Linux will beat Windows for good :D hehehe.

Well, good luck mate and I really like what you do :)
I feel I didn't sleep for years (yes, I'm Linux Addicted) so it's time to ZzZz :D

Please let us know what will happen with you ;)

---

### Post by mcduck on 2010-12-07
You could also try installing Grub2 on the USB drive, and using that to boot the .iso image.

I'm using a multiboot USB setup done this way, and the Lubuntu installer seems to work just fine. (besides, it's much easier when I don't have to bother burning discs or creating new bootable USB drives for all the different Ubuntu versions, and can instead just drop the .iso files to the stick and add a few lines to grub.cfg to add them to the menu ;))

[http://ubuntuforums.org/showthread.php?t=1288604]("http://ubuntuforums.org/showthread.php?t=1288604")

---

### Post by Ahunt on 2010-12-07
Thank you for that suggestion, too!

---

### Post by amjjawad on 2010-12-08
> **mcduck said:**
> You could also try installing Grub2 on the USB drive, and using that to boot the .iso image.

[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Sounds promising :)
I'm going to give that a try :D

---

### Post by Ahunt on 2010-12-08
I wanted to report back on using UNetbootin - it worked perfectly and we now have Lubuntu installed on the netbook!

Just a couple of "lessons learned" notes:

1. Unetbootin can be downloaded from [the website]("http://unetbootin.sourceforge.net/") directly and used with the instructions on that page or it is also in the Ubuntu repositories. We did the former and it worked fine.

2. The PC it is used on must have 7zip installed or else it won't work.

Thank you everyone for your help on this issue!
:P

---

### Post by amjjawad on 2010-12-08
> **Ahunt said:**
> I wanted to report back on using UNetbootin - it worked perfectly and we now have Lubuntu installed on the netbook!


HOOHAA :)
Well done and I'm glad you managed to install it ;)

---

### Post by ohiomoto on 2010-12-30
I was able to successfully create a stable Live USB disc Lubuntu with Ubuntu's "startup disk creator".  I simply selected the "Discarded on shutdown unless you save them elsewhere" option before making the disk.  


[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/usb_ubuntu_04_medium.jpg[/IMG]


I LOVE lubuntu.  My CULV laptop is getting fantastic battery life and is really snappy on Lubuntu.  I've had just a few other minor issues that were easily overcome, but the results have been worth it.

---

### Post by I2k4 on 2010-12-30
Thanks for the experience reports AHunt - I've just today replaced Ubuntu 10.10 Desktop with Lubuntu 10.10 on my 2GB USBdrive (1GB persistence) for alternate access to an XP machine, and it seems to finally eliminate the "lag" I'd been experiencing from the USB drive - impressively fast so far though less intuitive for a Windows user (I'd be floundering around a bit if I hadn't been using the regular Ubuntu for some weeks.)

---


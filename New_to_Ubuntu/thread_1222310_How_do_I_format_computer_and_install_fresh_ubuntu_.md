---
title: "How do I format computer and install fresh ubuntu from download option"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Loysfour on 2009-07-24
I downloaded a copy of Ubuntu and I want to load it on my laptop that currently has a corrupted OS. How can I reformat and load ubuntu from CD that I've downloaded from the site?

I've tried changing the boot from CD in the Bios with no luck.

Any idea's? Be specific I'm a nominal tecky..

Thanks

---

### Post by philcamlin on 2009-07-24
hit f12 in the bios then try :)

or you could try the usb method :)

unetbootin thats what i use and its much faster then the cd :popcorn:

---

### Post by mapes12 on 2009-07-25
So, you just need to install Ubu onto your laptop and don't have a need for any other OS on the HDD. I did the same the other day on a Thinkpad T30 which had XP on the HDD. First thing I did was completely wipe the HDD by booting from a Live Killdisk CD: [http://www.killdisk.com/](http://www.killdisk.com/)

For some reason my laptop does'nt like the Ubu Live CD's so next I used an [alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") Ubu installation CD and just followed the on screen instructions/prompts. Personally, I like 8.04 for the Long Term Support but given that you have nothing critical on your machine it may be worth trying different versions to see which you like best.

At some point it's good practice to have your /home on a separate partition. If you need further help with this then post a new thread. Also, take a look at the link in my sig file for more help.

---

### Post by 3rdalbum on 2009-07-25
If the CD doesn't boot, then there are a couple of probable causes:

1. The BIOS is not set up correctly for CD booting
2. The CD drive is broken
3. The CD you burnt, was burnt at such a high speed that there are errors in the disc - try reburning it at 8x.
4. The disc image you downloaded was a corrupted download - try checking the md5sum to see if all the data in the file is correct. (If you downloaded with Bittorrent it has already checked this for you).
5. You might not have burnt the CD correctly. You must use the "Burn Image to Disc" or "Write ISO Image" function of your burning software.

---

### Post by lkraemer on 2009-07-25
Loysfour,
When you downloaded the Ubuntu ISO there was an MD5SUM file that
is associated with that specific version.  You can VERIFY the ISO
is correct by using the MD5SUM software (or K3B) to make sure the
download was correct.  Then just burn the ISO as Disk at Once (DAO)
and at the slowest speed (I use K3b).

You should now be able to boot the LiveCD in any machine where the
boot order has CDR before the hard Drive.

If your corrupt OS on the Hard Drive has data/files you want, I'd suggest
installing testdisk via Synaptic (from the running LiveCD) and searching
the hard drive for any files or data you want to save.  You can also use
photorec to recover lots of file types. (testdisk & photorec are run from
a Terminal Window similar to an old DOS or Command Window)

When your data and files have been recovered, and you don't need the
information on the corrupt drive any more, I'd use gparted from the
LiveCD to remove the partition.  Then just re-partition the drive as
needed (ext3) and format the new partition.  Follow this by an install
of Ubuntu. (just make sure the LiveCD boots and runs correctly first)

Shouldn't take more than 30-40 minutes.

Download and try CrunchBang 9.04.1 LiveCD, or PCLinuxOS 2009.2

lkraemer

---


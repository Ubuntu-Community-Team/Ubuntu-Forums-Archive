---
title: "grub error, can't boot from usb drive"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by ruther on 2009-07-21
Using GParted, I managed to setup a nice, complete partition scheme for my new netbook.  Unfortunately, wiping out everything on the HD was a poor idea, because now I receive Grub error 15 on bootup.
 
When I try to boot from USB with a liveCD image of any distribution, I get a black screen with a blinking cursor in the top left, which is unresponsive.
 
Is there some sort of way to force a command line during bootup?  Is there an easy way to just start from scratch (I was just trying out different distros, I have no personal files on the computer)?
 
Please be explicit - I've accumulated a lot of the language used on these forums but clearly have an incomplete understanding of its meaning.

---

### Post by jeppewinther on 2009-07-21
Well, you need to boot something to get a command line, usually this is accomplished by inserting some device you can boot from, be it a floppy, a CD or a USB stick.

When you say a LiveCD image, did you follow the instructions on [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ?

Or did you stick .iso images on there? Because this won't work.



Your have me slightly confused though. Where did you run GParted from?

---

### Post by LewRockwell on 2009-07-21
I've posted this before in other threads but it might help here. This was my response to Jordan's saga found here([http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious](http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious))

************************************

I wanted to let you know that I had an eerily similar experience with my
Acer Aspire One AOA-150-1864(seems many of the internals are the same as
your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom).

I picked the netbook up used "on the cheap" and at first I thought I had
been sold a piece of crap. It came with Windows XP Pro SP3 and the damn
thing gave me fits connecting to my home wireless(Motorola Surfboard
SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed
around with that netbook for several hours resetting this and that and
rebooting numerous times. Then I went into the router setting and
started banging around there also. The one thing I did that might have
cracked the nut was I switched from G-only to mixed(but after it started
connecting I switched it back and it's still connected flawlessly). Not
only that, but since then I've reflashed the router with DDWRT and it
didn't miss a tick.

So anyways, that whole saga was with windoze...

After getting the wireless working and installing my favorite stuff on
windoze(and using them to clean, spruce-up, and defrag windoze) I then
set about partitioning the 120GB hard drive using a LiveCD of Puppy
Linux(Gparted) via an internal cd-rom drive I had laying around and one
of these gadgets which, I must say, no tech or hobbyist should be
without([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)).

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

After the partitioning ritual(reducing the windoze partition in several
smaller steps with the obligatory reboot into windoze between each
reduction so checkdisk could do it's thing) I installed my beloved Puppy
Linux and was pleased that it worked very well from the get-go(Puppy
installation slipped the Grub bootloader in place also). Then it was off
to the races to install Ubuntu 9.04 Jaunty Jackalope (full version)
which also went without any problems at all. It took a minimal amount of
time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it
looking "just right" and a couple of reboots into each system, but I
must say that I am pleased with the performance and overall experience.
I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it
bothers my eyes more quickly than the bigger screens. I plugged it's VGA
output into a nice 17 inch monitor I have on the tech bench and it
looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a
wireless keyboard and mouse assisting, it being a reasonably
energy-efficient alternative to the regular desktop monsters consuming
hundreds of watts unnecessarily.

I don't normally buy anything computer related, opting instead to
recycle everyone else's cast-aways, but with this netbook I decided I
couldn't pass up the opportunity to experiment with the N270 and who can
pass up what was essentially a free GB of ram and a free 120GB hard drive?

Well, thank you for your valuable time! I just wanted to let you know
others were having similar experiences with netbooks.

---


---
title: "Need Help w/reinstalling Ubuntu!!"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by spaceboy3000 on 2010-03-01
Hi folks - 

I'm a tinkerer, and pretty persistent, but I definitely need some help from more knowledgeable computer people on this one...!

The situation:  I have a Gateway MX6959 laptop.  It came with Windows, but the hard drive crashed last year.  I replaced it, and was having trouble reinstalling Windows.  My friend gave me the Linux 9.04 install disk, and I was a convert.

I upgraded "online" to version 9.10 a little while ago, and things have been going downhill since.  Everything is slower, lots of programs are slow to work, if they do at all.  The computer also takes a lot longer to boot up.  The machine is limping along, somewhat usable, but something is clearly wrong.

I have all my important info burned onto CD's so I can start over with another install of Linux, which is what I am trying to do.  I downloaded and burned the 9.04 and 9.10 desktop Ubuntu versions onto CDs.  But that isn't quite working either.  I can get the 9.04 disk to boot up, and give me the initial menu - but no more.  I've tried as many of the options as I can think of, like "trying Ubuntu without changes to your hard drive", the second option, which is the "install ubuntu" choice, etc.  Nothing happens when I select these options.  My computer won't recognize the 9.10 disk as bootable at all (it just reverts to booting off the hard drive, as usual.

Any tests that I've run (through the installed ubuntu or off the ubuntu install disk) seem to say that there is no hardware problem that it can find (although I am not sure exactly which hardware it checks).  I also tried to make a bootable usb flash drive, but couldn't get that to work either.  

Unfortunately, I am just not familiar enough with all the architecture of my computer to know where else to look.  I even tried a "SuperGRUB" disk, but I am in WAY over my head.  I am guessing that it has something to do with the BIOS and/or boot settings or something in there.

I'm attaching a few (poorly done:D) screen shots that might help a bit.  Two are of the BIOS screens, one is of the hard drive (as far as the currently installed ubuntu sees it) and one shows the screen during bootup from the hard drive.  I don't know if any of this helps, but does anybody have any advice?  Is it possible that my CD/DVD drive is bad, and can't burn good enough CDs and/or not read them well enough?   Also, FWIW, the installed Ubuntu doesn't find any "propriety" hardware drivers, according to to System>Administration>Hardware Drivers.

Like I said, this is definitely WAY beyond my level of familiarity with most of this stuff.  If there are other obvious things to try, I could sure use some pointers.   Otherwise I can take the machine in to get looked at, but if I could I would like to sort it out at home - and maybe learn something along the way!!!

Thanks.

---

### Post by undecim on 2010-03-01
sounds to me like a bad burn or bad download.

Check the md5sum of the ISO you downloaded: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Make sure that you are buring the ISO as a disc image rather than a file. (though you seem to have this part down, since you got one of them to give you a menu)

And finally, burn a disc at a lower speed. It will take longer, but it will be less likely to have a bad burn.

If you are still having CD-related issues, try to check the cd for errors from the CD's boot menu.

And if you just can't seem to burn a working disc, perhaps your friend who gave you your first disc can help you get a 9.10 disc.

---

### Post by azagaros on 2010-03-01
First suggestion, test the media on another computer, including the Hard disk.  

Everything you point out may be a bad drive controller on the Motherboard but test everything on other computers first, and if possible install the system on the other computer and put the disk back in the laptop and see if it boots.

The computer has already trashed one hard disk, which might be the first clue. The other clues are the bad reads from cd-rom/dvd-rom which are controlled by the same chip.

I don't want to point you to any conclusion until you test the media on other computers.

---

### Post by switch10 on 2010-03-01
Hmm.  That is odd.  

I have a very similar Gateway laptop, with the exact same BIOS.  

When you installed Ubuntu to begin with, did you use the same 9.04 cd you are trying now?

How did you burn the 9.10 cd?  If you burned it as data, it won't boot.

What I would try is first re burn that 9.10 cd, by double clicking on the ISO file, which will bring up Brasero.  Burn the CD at the lowest possible speed.  If that still doesn't work, I would download the "alternate" cd and give that one a go.  

good luck

dave

---

### Post by ajgreeny on 2010-03-01
I also see from your second pic you have only 8MB of memory set aside for graphics.  I think it could help if you had more, perhaps 32, so change that in BIOS and see if it helps.  If not, nothing is lost.

---


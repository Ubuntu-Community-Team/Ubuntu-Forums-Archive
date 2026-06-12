---
title: "Remastersys not working in Karmic Koala"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by longtom on 2009-11-01
Remastersys is not working in Karmic Koala.

I did all I did with any other version of Ubuntu.  When I want to start installing from the dvd, the error message I do get is:

```

Could not find ramdisk image:  /casper/initrd.gz

```

And this file is indeed not created.  It is in a 8.04 install, which I happened to have handy and a look at.

And that's it.  

Might be connected to the following problem:

[http://ubuntuforums.org/showthread.php?t=1308984](http://ubuntuforums.org/showthread.php?t=1308984)

Any suggestions welcome

Edit:  Made an entry in the remastersys forum.  As it stands at present **remastersys is not usable with Ubuntu 9.10.**

---

### Post by lio_013 on 2009-11-01
[http://geekconnection.org/remastersys/forums/index.php?topic=320.0](http://geekconnection.org/remastersys/forums/index.php?topic=320.0)

---

### Post by panmoto on 2009-11-02
I did some simple work around to make remastersys .iso works, and it will boot just fine as a live usb but the problem is it can't install ubuntu. the installation process will crash on grub installation (94% of installation) therefore the installed system won't boot and neither other systems already installed.

But if live usb is what you need, this is what I did ( WARNING : do not install from this live usb. it may renders your system unusable)

- make a custom cd with remastersys
- make a live usb from it, with USB startup creator
- go to /boot and then copy initrd.img-xxxxxxxx
- paste it into the live usb on directory /casper/ and rename initrd.img-xxxxxxxx as initrd.gz
- boot with the live usb

of course it just an incomplete and temporary work around, we have to wait for the real fix, I hope soon.

again : do not install from this live usb

---

### Post by longtom on 2009-11-02
> **panmoto said:**
> I did some simple work around to make remastersys .iso works, and it will boot just fine as a live usb but the problem is it can't install ubuntu. the installation process will crash on grub installation (94% of installation) therefore the installed system won't boot and neither other systems already installed.

But if live usb is what you need, this is what I did ( WARNING : do not install from this live usb. it may renders your system unusable)

- make a custom cd with remastersys
- make a live usb from it, with USB startup creator
- go to /boot and then copy initrd.img-xxxxxxxx
- paste it into the live usb on directory /casper/ and rename initrd.img-xxxxxxxx as initrd.gz
- boot with the live usb

of course it just an incomplete and temporary work around, we have to wait for the real fix, I hope soon.

again : do not install from this live usb


No - live USB is not what I am after.  I give updated cds away to people with no or only dial-up connection.  Remastersys is the ideal tool for that.

The developers of remastersys are aware of the problem and have promised to look into it.  So all it takes is a bit of patience and hope.

---

### Post by Alacrity on 2009-11-04
> **panmoto said:**
> I did some simple work around to make remastersys .iso works, and it will boot just fine as a live usb but the problem is it can't install ubuntu. the installation process will crash on grub installation (94% of installation) therefore the installed system won't boot and neither other systems already installed.

But if live usb is what you need, this is what I did ( WARNING : do not install from this live usb. it may renders your system unusable)

- make a custom cd with remastersys
- make a live usb from it, with USB startup creator
- go to /boot and then copy initrd.img-xxxxxxxx
- paste it into the live usb on directory /casper/ and rename initrd.img-xxxxxxxx as initrd.gz
- boot with the live usb

of course it just an incomplete and temporary work around, we have to wait for the real fix, I hope soon.

again : do not install from this live usb



Panmoto,

You saved me with your suggestion!  Many thanks for sharing your solution on the forum.

Alacrity

---

### Post by Fragadelic on 2009-11-04
I just finished working on remastersys for Karmic.

Here is a link to my forum with info about it.

[http://geekconnection.org/remastersys/forums/index.php?topic=354.0](http://geekconnection.org/remastersys/forums/index.php?topic=354.0)

There were some big backend changes by the ubuntu folks which is why the older versions won't work.

If any of you have installed the older versions and let it remove grub2, you will have to put grub2 back as the installers in Karmic rely on grub2.

---

### Post by longtom on 2009-11-05
> **Fragadelic said:**
> I just finished working on remastersys for Karmic.

Here is a link to my forum with info about it.

[http://geekconnection.org/remastersys/forums/index.php?topic=354.0](http://geekconnection.org/remastersys/forums/index.php?topic=354.0)

There were some big backend changes by the ubuntu folks which is why the older versions won't work.

If any of you have installed the older versions and let it remove grub2, you will have to put grub2 back as the installers in Karmic rely on grub2.

Thank you very much for this prompt service!  I'll check it out right now.

---

### Post by kermiac on 2009-11-05
Thanks for the very quick release of this updated version for Karmic. I will look into it now as we cannot (easily) update the PC's & Desktops at my work without your awesome program.

---

### Post by Alacrity on 2009-11-06
> **Fragadelic said:**
> I just finished working on remastersys for Karmic.

Here is a link to my forum with info about it.

[http://geekconnection.org/remastersys/forums/index.php?topic=354.0](http://geekconnection.org/remastersys/forums/index.php?topic=354.0)

There were some big backend changes by the ubuntu folks which is why the older versions won't work.

If any of you have installed the older versions and let it remove grub2, you will have to put grub2 back as the installers in Karmic rely on grub2.


wow! I can visualize you working thru the night to complete that great effort!  Many thanks. I see now why everyone thinks you are a god. 

A

---

### Post by Fragadelic on 2009-11-06
lol - I'm no god for sure.

The initial work on remastersys in the beginning was difficult and I had to learn a lot about how ubuntu does their livecd stuff.  That meant a lot of reading through scripts and following 1 to another to get the whole picture.

These days they mostly just change some little things but sometimes those cause big issues.

The problem regarding the initrd.gz was one of these small things that caused a big problem.  The old casper-new-uuid tool would copy over the initrd.img to initrd.gz where you told it to.  The new one does no such thing and they changed the format of the .disk folder which is required for the usb creator tool.  This functionality is not back yet as I have to work through how to create some of those files manually and where to get the information.

All in all I spent only 1 evening updating it.

---

### Post by Alacrity on 2009-11-06
Too modest!

Everyone appreciates such a great tool and its creator.

By the way, I have confirmed that unetbootin also works well with the new remastersys to generate a usb live custom boot.

Thanks again.

A

---

### Post by Fragadelic on 2009-11-06
All the kudos need to go to the Ubuntu developers.  All I did was create a script to simplify remastering.  Didn't really reinvent any wheels but did have to figure out how to do a few things to make it work as desired.  If it wasn't for the casper scripts that the Ubuntu dev's created, remastersys would never have existed.

---

### Post by abdulkhaliq on 2009-11-18
> I did some simple work around to make remastersys .iso works, and it will boot just fine as a live usb but the problem is it can't install ubuntu. the installation process will crash on grub installation (94% of installation) therefore the installed system won't boot and neither other systems already installed.

Is there any solution?

---

### Post by switch10 on 2010-02-04
Just checking if this has been fixed..  Thanks

---

### Post by switch10 on 2010-02-04
I am having this same problem.  I went to the remastersys forums and found that there is a different repository for Grub2 and Karmic, I was using a different one.  Here is the new one:

```
deb http://www.geekconnection.org/remastersys/repository karmic/
```

i am running sudo remastersys dist right now...  I will post back if this works.

---

### Post by switch10 on 2010-02-04
Yes this works!!

just add the updated repository and reinstall!!

---


---
title: "I stuffed the install"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Craig-R on 2011-06-27
Hi 

When I installed ubuntu I wanted to dual boot with windows 7, I have 2 200 Gb drives for this and one had windows 7 on it. 

I got a bit click happy during the install and managed to install ubuntu over the top of my windows 7 , so it does not work anymore.

Is there anyway I can uninstall this and get windows back then reinstall it on the correct drive without too much damage to all my old windows files.

Any help will be greatly appreciated

Regards

Craig

---

### Post by Ozymandias_117 on 2011-06-27
First thing I would do, is disconnect the drive that you overwrote windows on.  Then install Ubuntu on the correct drive (This way as you're working, you won't continue overwriting more of the old files).  Then boot to the new Ubuntu installation, and try out a program called TestDisk.  Odds are you'll be able to recover some things, but I can't tell you how much.

Edit: When booting after plugging the second drive back in, MAKE SURE YOU BOOT TO THE CORRECT ONE. :) Also, make sure to recover the files to the second hard drive, not the one Windows was on.

---

### Post by Craig-R on 2011-06-28
Thanks I will give it a go

---

### Post by Rasa1111 on 2011-06-28
if you installed ubuntu over 7, (essentially overwriting the windows OS),
I don't imagine you'lll be able to recover much. if anything. 

good luck though

---

### Post by dFlyer on 2011-06-28
Do you have the window 7 disk, just in case you can't recovery your windows? If so I would recommend you download a free cloning program and after you reinstall windows 7 clone your OS. It's much easier to restore a clone than reinstall a whole windows system.

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

The above links is a free windows cloning software. I use this for my daughters computer to avoid OS reinstalls after she trashes her system.

Now as far as answering your question, I don't know of any program that will be able to restore your windows disk if you installed ubuntu over it. Hopefully testdisk that someone suggested above will work, but if not it's a good lesson learned. Always remember to clone or backup any important data before installing an OS. Just remember Murphy Law, if something can go wrong it will.

---

### Post by nzjethro on 2011-06-28
> **Craig-R said:**
> 
I got a bit click happy during the install and managed to install ubuntu over the top of my windows 7 , so it does not work anymore.


I did the same thing when I first installed Ubuntu. Did you heed the warnings and make full and tested backups of your system before mucking around with installing OSes? If yes, there is no problem, simply reinstall Win 7, and apply your backups. If you didn't (like me), then welcome to full time use of Ubuntu. :p

Seriously though, if you have a Windows install key, you could reinstall Windows (this won't recover your files though, so I truly hope you didn't have anything too irreplaceable on there). Otherwise, you can request one from your laptop manufacturer, or just go with the flow and get used to Ubuntu. :D

---

### Post by Ozymandias_117 on 2011-06-28
Just wanted to make sure I was clear after reading other replies.  My solution is really only to recover important data that you lost; you won't get EVERYTHING back, so you can't just start running Windows again without reinstalling.

---

### Post by Jagoly on 2011-06-28
Most likely. Although, if you windows install wasn't too fragmented, you should be able to get a fair bit of your recent stuff back.

U=ubuntu
W=windows recoverable
D=Windows dead

Before
WWWWWWWWWWWWW

After
UUUUDDDWDWDWW

Testdisk isn't an easy to use program though.

---

### Post by Craig-R on 2011-06-28
I have the windows disk so that is no problem, its just the stuff that windows may have put under its documents and photos, I have most on separate drives but I am hoping i didn't have any there.

No I did not follow any warnings of backing up ( I thought it was going to be simple) :P

well at least I have it installed on the right drive now


now to figure out test disk ( at least this is teaching me how to use linux :) 

Thanks

Craig

---

### Post by crispy_420 on 2011-06-28
There are programs like photorec and foremost that may help you recover some stuff but some will also be lost too. Do you have a third drive? Your best bet would be to image the messed up drive with dd to an img file to third drive and recover with image and not real drive. The more you use the drive the more that will be lost for good.

---

### Post by Craig-R on 2011-06-28
I have 5 drives with plenty of space

---

### Post by Ozymandias_117 on 2011-06-28
As long as you don't write to it, reading from it won't lose any more data.  Photorec is pretty good (It's from the same people as testdisk) but when it recovers things, it doesn't recover the original filename, which can suck because it usually recovers a LOT. Testdisk is more complicated, but it can generally recover filenames, and you get more control over EXACTLY what is recovered.

---

### Post by Craig-R on 2011-06-28
I tried everything and gave up, i am now trying to reinstall windows 7 on my original drive and it wont let me, I have deleted the partition and tried to reformat in ntfs but my windows disk wont let me install it again

---

### Post by Jagoly on 2011-06-28
Is the windows disk an upgrade disk or fresh intall disk? Or OEM disk?

---


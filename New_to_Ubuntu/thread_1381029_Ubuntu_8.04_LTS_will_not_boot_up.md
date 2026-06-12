---
title: "Ubuntu 8.04 LTS will not boot up"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by suomalainen on 2010-01-14
Ubunteros,

MY Ubuntu 8.04 LTS will not boot up anymore. A few days ago I had a similar issue but it appeared that running fsck manually when prompted fixed everything.

Now all I end up with after the PC goes through Grub, the Ubuntu Splash screen, and then minutes of scrolling text on a black background is a stalled computer with a little red star in the middle left side of the display and nothing happens.

I don't know what the problem is or how to tackle a resolution. If somebody can lend a hand that would be great!!!

Also, I would like to know where I need to look on the hard drive to find all me email. Is it possible to still salvage my email?

Thank you!!!!

---

### Post by maddog39 on 2010-01-14
Well it sounds like a kernel panic to be honest. Ideally, you'll want to get off that old version at some point. But, when the GRUB menu comes up, did you try selecting a different kernel to load? Perhaps try booting from an older kernel.

---

### Post by kansasnoob on 2010-01-14
> **suomalainen said:**
> Ubunteros,

MY Ubuntu 8.04 LTS will not boot up anymore. A few days ago I had a similar issue but it appeared that running fsck manually when prompted fixed everything.

Now all I end up with after the PB goes through Grub, the Ubuntu Splash screen, and then minutes of scrolling text on a black background is a stalled computer with a little red star in the middle left side of the display and nothing happens.

I don't know what the problem is or how to tackle a resolution. If somebody can lend a hand that would be great!!!

Also, I would like to know where I need to look on the hard drive to find all me email. Is it possible to still salvage my email?

Thank you!!!!

Are you running the Live CD right now?

If so post the output of:

```
sudo fdisk -l
```

What email program do you use?

---

### Post by suomalainen on 2010-01-14
Thank you everyone for replying!!!! I hope I can get back up and running shortly.

Knasasnoob attached is a pic of the data you requested. Thank You!!

maddog39, I don't see any option to use an older kernel. How am I suppose to force this??? Thank You.

---

### Post by Merk42 on 2010-01-14
> **suomalainen said:**
> Thank you everyone for replying!!!! I hope I can get back up and running shortly.

Knasasnoob attached is a pic of the data you requested. Thank You!!

maddog39, I don't see any option to use an older kernel. How am I suppose to force this??? Thank You.

the command is ```
fdisk -l
```

l as in L, not 1 as in one

---

### Post by suomalainen on 2010-01-14
All,

Attached is the new data I obtained.

I would like to note the following. Internally my PC has 1 HDD which is 500GB. Then I have another exact same HDD mounted in a mobile rack in which I installed Ubuntu 8.04LTS. Thus, this hdd contains the o/s and all the programs I use while the internal HDD is a dumping ground for the data I collect and generate.

Therefore, I'm not sure from which HDD the data I just produced using fdisk -l came from. Was it the internal drive? Or the external drive?

Kansasnoob, I use evolution as my email client. Thanks.

Thank you.

---

### Post by kansasnoob on 2010-01-14
It would be good if you learn to copy-n-paste:

[http://www.ehow.com/how_5737593_use-copy-paste-computers.html](http://www.ehow.com/how_5737593_use-copy-paste-computers.html)

I'm not being a smarty pants but to resolve this might require copy-n-pasting commands from here to the terminal.

Anyway, since you're good at posting screenshots just go to System > Administration > Partition Editor and post a screenshot here. That will fairly well answer my disc/partition space question.

BTW that ouput shows both drives, sda is the Ubuntu drive and sdb is the data drive.

About booting into an older kernel, since Ubuntu is your only OS you don't see a boot menu at startup, but as you restart right after the system screen passes if you press the Esc key you should see a list of kernels and a recovery mode for each. The default "boot" kernel is at the top so you can use the arrow keys to scroll down to the next older kernel and try that.

---

### Post by suomalainen on 2010-01-14
Kansasnoob,

Attached is the info you requested. I'd like to note that this is the internal drive where I dump my data and not the drive that contains my Ubuntu o/s.

I'll give it a shot now to see if I can boot using the older kernel as you instructed.

Thank You Again!!!

---

### Post by kansasnoob on 2010-01-14
Since you use Evolution, while in the Live desktop if you go to Places > Computer you should be able to see your Ubuntu there. In it's Home folder you should see a folder with your user name (or folders with user names).

If you open that folder you should see Documents, Pictures, etc, etc. Go to View and click on show hidden files. You should see a folder named .evolution. That is your Evolution mail folder.

The same goes for any folder in there. When I do a rescue I usually just save each <user name> folder by right clicking it then selecting Copy and then pasting it into its new destination.

---

### Post by kansasnoob on 2010-01-14
> **suomalainen said:**
> Kansasnoob,

Attached is the info you requested. I'd like to note that this is the internal drive where I dump my data and not the drive that contains my Ubuntu o/s.

I'll give it a shot now to see if I can boot using the older kernel as you instructed.

Thank You Again!!!

Well that does me no good whatsoever. I wanted to see how much free space is on the Ubuntu drive.

---

### Post by suomalainen on 2010-01-14
Kansannoob

> Well that does me no good whatsoever. I wanted to see how much free space is on the Ubuntu drive.

I followed your instructions precisely and to the "T" and this was the data that was generated. Would you like I do something different????

---

### Post by suomalainen on 2010-01-14
Kansasnoob,

I think I have found what you are looking for. But I'm also confused. The first go around we got data for my internal drive sdb but now on this second try we get for only sba and not both! So I'm kinda confused what's going on here?

Your help is appreciated You know!

Thank you!

---

### Post by kansasnoob on 2010-01-14
So did you get booted? I see all partitions are mounted.

---


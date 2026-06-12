---
title: "Could somebody help me renaming a partition?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-07
Hello,


I've got a partition which I want to rename. The current name is "Media van 698,2 GB" (my Ubuntu is in Dutch). I had a look [here]("https://help.ubuntu.com/community/RenameUSBDrive"), and started by running "sudo fdisk -l". However, I don't think that that partition is showing..

I'm kinda lost now.. Could anybody help me a bit further maybe?

---

### Post by Elfy on 2009-05-07
If you're not sure whether the drive is showing up - run fdisk -l with it unplugged and then again with it plugged in and mounted, if you are still unsure post the before and after here.

Then the community page you linked to should do the trick.

---

### Post by kramer65 on 2009-05-07
Ah, that is a good tip. I first unmounted the partition and got this:

```
myname@mypc-desktop:~$ sudo fdisk -l

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x0006601a

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       36473   195310237+  83  Linux
/dev/sda3           36474       36716     1951897+  82  Linux wisselgeheugen
/dev/sda4           36717      121601   681838762+  83  Linux

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000000

Schijf /dev/sdb bevat geen geldige partitietabel

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x44fdfe06

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1               1       60801   488384001   83  Linux
```

And then I remounted the partition again and I got this:

```
myname@mypc-desktop:~$ sudo fdisk -l

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x0006601a

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       36473   195310237+  83  Linux
/dev/sda3           36474       36716     1951897+  82  Linux wisselgeheugen
/dev/sda4           36717      121601   681838762+  83  Linux

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000000

Schijf /dev/sdb bevat geen geldige partitietabel

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x44fdfe06

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1               1       60801   488384001   83  Linux

```

I saw in nautilus however, that the address of the partition is this: /media/disk
Maybe that helps as well..?

---

### Post by Elfy on 2009-05-07
it would appear to be sdb you can check, run 

```
df -h
```

Look for /media/disk see what /dev/ it is

Then you can use the link you gave in your first post

---

### Post by geirha on 2009-05-07
If you run ```
export LANG=
``` in a terminal, all subsequent commands in that terminal will be untranslated (thus output written in english). I'm not so good with dutch :)

---

### Post by Elfy on 2009-05-07
> **geirha said:**
> If you run ```
export LANG=
``` in a terminal, all subsequent commands in that terminal will be untranslated (thus output written in english). I'm not so good with dutch :)

I have searched and searched for a long time for that - I saw it once and thought cool that'll be useful - then promptly forgot to write it down.

Thank you geirha :D

---

### Post by Didius Falco on 2009-05-07
Thanks from me, too geirha.

I wish I'd known that one a few days ago - a gentleman from Japan was looking for help and that command would have been very handy.

Already added to my Useful.Commands file...

Regards,

Didius

---

### Post by kramer65 on 2009-05-07
> **forestpixie said:**
> it would appear to be sdb you can check, run 

```
df -h
```

Look for /media/disk see what /dev/ it is

Then you can use the link you gave in your first post


Alright, When I run that I get some output which contains this:

```
/dev/sda4             646G  198M  613G   1% /media/disk
```

So I guess it is /dev/sda4. However, when I paste "/dev/sda4" in a nautilus address bar it can't be displayed because the location is not a folder.

Can I use /dev/sda4 with the e2label program now to rename it?

---

### Post by geirha on 2009-05-07
/dev/sda4 is the device node. The df output also lists where it is mounted, which is /media/disk. Type that in nautilus to make sure it is the correct one.

Make sure to unmount it before changing the label (when it is unmounted, df will no longer list it, so check the output of df -h), then run ```
sudo e2label /dev/sda4 "The_volume_name"
```

EDIT: You might need to restart udev for the label to show in nautilus, so you could try ```
sudo /etc/init.d/udev restart
``` if that is the case. Restarting Ubuntu is of course another way.

EDIT2: Oh and it seems /dev/sdb is a 1 TB disk that is entirely unused ...

---

### Post by kramer65 on 2009-05-07
Alright Geirha! I've got it renamed now and it works like a charm. Thank you!

One more thing. How can I make sure it mounts automatically everytime I start up the pc?

[edit] I know indeed about the 1TB harddisk which I am not using at all. I first wanted to rename this one (which I just did), and I now want to use the 1TB hard drive as a backup with sBackup...

---

### Post by Elfy on 2009-05-07
You need to add the drive to fstab - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

In effect make a folder with mkdir then add the line to fstab

---

### Post by kramer65 on 2009-05-07
Alright thanks for that tip. I must say it all looks pretty technical. Since I was already pretty happy that I was able to rename this partition I will leave this next thing for the coming month. (as I also did with this renaming thing..)

One more question. I am using Ubuntu 8.04 now (for the stability). Has this renaming of partitions and automatic mounting become a bit easier in the newer Ubuntu versions? I think that this is one of these things that scares people away from linux. It is at least one of those simple things that my friends who I could recommend Ubuntu too are just very reluctant to (and so am I... :-)  )

Anyway. Thanks for all the help!

---

### Post by Elfy on 2009-05-09
It isn't as bad as it looks :)

There is a GUI tool [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Have a look at that you might find it useful.

---

### Post by kramer65 on 2009-05-11
@ Forestpixie
Thanks for that tip. I just installed it and I want to auto-mount my sda4 or "Opslag" partition. But in the list in the Storage Device Manager it only shows sda1 and sda2. sda3 is the swap I think, but sda4 should be showing as well right?

Does anybody know how I can make sda4 appear in the Storage Device Manager?

---


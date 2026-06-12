---
title: "Newbie... help with partitions"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by agquintero on 2009-11-05
Ok... i have a few problems. I recently made the jump to Ubuntu because my friends will not stop raving about it. Unfortunately, when I installed it to dual boot with Windows I didn't give it enough hard drive space. Is there any way to increase the partition size? BTW I'm installing the netbook edition (remix) of Ubuntu.... just thought i'd let you know. Thank you!

---

### Post by KIAaze on 2009-11-05
1)**Backup important data first!**
2)Boot into the Ubuntu Live-CD (or Live-USB?) and then run GParted (System->Administration->Partition editor) to resize the partitions.

---

### Post by agquintero on 2009-11-05
> **KIAaze said:**
> 1)**Backup important data first!**
2)Boot into the Ubuntu Live-CD (or Live-USB?) and then run GParted (System->Administration->Partition editor) to resize the partitions.

am I going to do this from Windows or from Ubuntu? And the cd that i'm using... i'm not sure if it is the live CD....it's the one I downloaded from ubuntu.com which is netbook remix. Is that the disk you are referring to?

---

### Post by kyuubi777 on 2009-11-05
yes, that is called the live cd.. and you will be using it.. when u boot it it gives you a "live" temporary set of features... as KIA said, run GParted in the live window

---

### Post by kyuubi777 on 2009-11-05
make sure you choose "try ubuntu w/out installing" from the selection list when u start the comp. with the cd in
this will get you into the live session

---

### Post by jimmy the saint on 2009-11-05
I would also add that you should DEFINITELY back up everything before you start messing with the partitions.  I usually make an image of the drive if I am going to something like that.  Clonezilla is a great free tool for that.  Everything will probably go well if you are careful, but its easy to frag a HD when messing with partitions and that is just a miserable way to spend and evening!

---

### Post by agquintero on 2009-11-05
> **kyuubi777 said:**
> make sure you choose "try ubuntu w/out installing" from the selection list when u start the comp. with the cd in

thank you very much... i didn't see anything that said live...i thought i had the wrong thing.... my understanding is that with this live version my hardware would be recognized and i would be able to log on to the internet... however it is not connecting to the net... a box comes up saying that i have some hardware updates to perform... i click on that and the "Hardware Drivers" box comes up and has listed Broadcom B43 wireless driver and it also gives me information about the driver... at the bottom it says that it's not activated. However when i hit activate using an ethernet cable it downloads and installs the driver, however, when i try to search for my internet connection it states that my wireless device is not ready.... any ideas as to what is going on?

---

### Post by KIAaze on 2009-11-05
Mmh, you don't need an internet connection to resize partitions.
GParted should already be available on the Live-CD.

Are you sure you booted from the CD and not the hard disk?

Also, you cannot resize the partitions if they are mounted (which is also why you have to do it from the CD).

---

### Post by agquintero on 2009-11-05
> **KIAaze said:**
> Mmh, you don't need an internet connection to resize partitions.
GParted should already be available on the Live-CD.

Are you sure you booted from the CD and not the hard disk?

Also, you cannot resize the partitions if they are mounted (which is also why you have to do it from the CD).


oO... sorry..it's a bit off-topic,  it's a completely different issue... it has to do with me not being able to connect to the internet wirelessly through ubuntu.... thanks

---

### Post by KIAaze on 2009-11-05
Could you please post the output of?:
```
lspci -vvnn
```
(Read [this]("https://help.ubuntu.com/community/UsingTheTerminal") if you don't understand what I said. ;) )

Some first google results which might help:
[http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html](http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html)
[http://ubuntuforums.org/showthread.php?p=8203365](http://ubuntuforums.org/showthread.php?p=8203365)
[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)

P.S.: And it would be a better idea to create a new topic for another problem. :mad:

---

### Post by agquintero on 2009-11-05
> **KIAaze said:**
> Could you please post the output of?:
```
lspci -vvnn
```(Read [this]("https://help.ubuntu.com/community/UsingTheTerminal") if you don't understand what I said. ;) )

Some first google results which might help:
[http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html](http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html)
[http://ubuntuforums.org/showthread.php?p=8203365](http://ubuntuforums.org/showthread.php?p=8203365)
[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)

P.S.: And it would be a better idea to create a new topic for another problem. :mad:

you're right! new topic under "Newbie... help connecting to wireless network" :oops:

---

### Post by texla on 2009-11-05
> **agquintero said:**
> thank you very much... i didn't see anytstatementhing that said live...i thought i had the wrong thing.... my understanding is that with this live version my hardware would be recognized and i would be able to log on to the internet... however it is not connecting to the net... a box comes up saying that i have some hardware updates to perform... i click on that and the "Hardware Drivers" box comes up and has listed Broadcom B43 wireless driver and it also gives me information about the driver... at the bottom it says that it's not activated. However when i hit activate using an ethernet cable it downloads and installs the driver, however, when i try to search for my internet connection it states that my wireless device is not ready.... any ideas as to what is going on?

I realize this thread is probably dead but I just wanted to say his exact problem happened to me when trying the Xubuntu 9.10 live CD on an older laptop (Avaratec).  It was strange because it worked great as a usb install on a new netbook - Asus 1000Ha - but the usb install wouldn't go anywhere on the old Avaratec.  And when I tried the Live CD it did just what the other user said above. 

My fix for now was that I went to the live CD of the normal 9.04 Jaunty for the Avaratec and it works sweet.  Not sure why the Xubuntu Karmic won't.  I'm going to try the basic Karmic install on it later and see if it works.

---


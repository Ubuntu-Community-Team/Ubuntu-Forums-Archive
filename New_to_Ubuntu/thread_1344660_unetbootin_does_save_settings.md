---
title: "unetbootin does save settings"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by fchartier on 2009-12-03
Hi all,

I have started using ubuntu through unetbootin. first i downloaded the iso and then used unetbootin.
i am not sure why but everytime i turn on my computer, choose unetbootin etc.
i have to reset the wireless network key.. if i had a file, the next time i launch its not there.. 
is it because unetbootin is just a one trial version? or maybe i  am not doing something right. 

cheers and thanks

---

### Post by yeats on 2009-12-03
Your USB drive is apparently not set to be persistent.  Take a look here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing%20Ubuntu%20on%20USB%20drive%20using%20Windows](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing%20Ubuntu%20on%20USB%20drive%20using%20Windows)

---

### Post by fchartier on 2009-12-03
thanks, 

I think its because i am installing on the hard disk. I am using an external disk but its full of data and i dont want to format it to loose everything.  I thought that it would work that way:
there is a possibility to install ubuntu final once i have booted with unetbootin by 'ubuntu install', my partitioning is not correct, how can i change this to have the dual boot?
I have tried with Wubi, but there is an error before it ends the install
cheers and thanks again

---

### Post by yeats on 2009-12-03
You'll need to provide a little more information...

> I think its because i am installing on the hard disk. I am using an external disk but its full of data and i dont want to format it to loose everything.

Does that mean you have 2 hard disks - one internal and one external?

> there is a possibility to install ubuntu final once i have booted with unetbootin by 'ubuntu install', my partitioning is not correct, how can i change this to have the dual boot?

Yes, you can install from the USB, which will allow you to dual boot.  Which version of Windows are you running?  (XP and Vista/Win7 work differently as far as changing their partition sizes).  

You'll probably want to clear out enough space (minimum 20GB, I'd say) on one of your drives.  The Ubuntu partitioning step during installation will allow to create/edit partitions, but you have to have enough free space to start with.

---

### Post by fchartier on 2009-12-03
Hi

i am using windows xp 2002 home edition
concerning disks, i am using one disk, but have an external disk as backup and for storage. I have read that if i use a usb install, meaning for me, that i would use my external disk to load the iso file and then use it to install ubuntu, this would necessitate my external disk to be formatted; ie loose all my data.

For the ubuntu install once i have started my computer in unetbootin 'mode', there is an icon on the desktop = ubuntu install. if i clic on this, i enter the ubuntu install menu, choose language, country etc. then disk partioning, thats where i face a problem as my disk is normally partitioned into = 60 GB and 200 MB (i dont know why but its not relevant perhaps) 
there is a message above this saying that i cant install ubuntu as the install file is on the same media.. if i remember 100% correctly. 

Correct me if i am wrong, perhaps the simplest thing to do is perhaps, 
a) to install the iso file on my external disk if it means not loosing my data or use another flash disk of at least 1 GB 
b) install the traditional way, and ubuntu will do the partitioning itself.

Thanks for ur help

---

### Post by yeats on 2009-12-03
> I have read that if i use a usb install, meaning for me, that i would use my external disk to load the iso file and then use it to install ubuntu, this would necessitate my external disk to be formatted; ie loose all my data.


That's not true.  You can simply unplug the external drive during Ubuntu installation - you'll be able to use it afterwards.

> 
For the ubuntu install once i have started my computer in unetbootin 'mode', there is an icon on the desktop = ubuntu install. if i clic on this, i enter the ubuntu install menu, choose language, country etc. then disk partioning, thats where i face a problem as my disk is normally partitioned into = 60 GB and 200 MB (i dont know why but its not relevant perhaps) there is a message above this saying that i cant install ubuntu as the install file is on the same media.. if i remember 100% correctly.

You'll need to make room for the Ubuntu install from the 60 GB (assuming that's from your internal hard disk, not the external disk).  You should be able to do this from the Ubuntu installation disc, probably under System -> Administration... look for something like "Partition Editor" - otherwise you should be able to do it from a terminal - Applications -> Accessories -> Terminal - and type 

```
sudo gparted
```

You'll probably want to clean up and defrag your Windows installation before doing this, as Windows spreads its programs all over the disk and you risk overwriting something important.

---

### Post by yeats on 2009-12-03
Wait a minute!  I just re-read this:

> that i would use my external disk to load the iso file and then use it to install ubuntu

You're booting from your external drive?  I would definitely choose an alternative way of doing this, either a thumb drive or CD...

---

### Post by fchartier on 2009-12-03
ok thanks 
yes thats what i think about the external disk, its not a good idea.
i will try to partition with gparted and see where it goes.
then use a usb flash disk 

i will keep u posted thanks!

---

### Post by fchartier on 2009-12-03
i have got windows defraged etc. controled disk error
well gparted would work but is going to erase all my C drive.

---

### Post by yeats on 2009-12-03
> i have got windows defraged etc. 

Great.

> controled disk error

At what point did you receive the error?  What was the exact text of the error?


> well gparted would work but is going to erase all my C drive. 

You definitely don't want that. :-)  Gparted should allow you to resize your Windows partition to be smaller.  See here:

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

(that's part of a larger tutorial you might want to peruse before proceeding...)

---


---
title: "No Partition Side By Side?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Phantomhive on 2010-01-21
I was told there was a side by side option in the partition selection when installing Ubuntu, but I do not see any! I'm trying to install it through a 9.10 LiveCD; too much of a wimp to actually partition it manually for now, as I don't know enough in all honesty.

The partitioner says I am running several operating systems, which I find as... What? It also shows/lists the following. 

Windows 7 (loader)(/dev/sda1) 199MB
Windows 7 (loader)(/dev/sda2) 452.4GB
Windows Vista (loader)(/dev)(/sda3) 13.1GB
/dev/sda4 103MB

All of which are also NTFS except the /dev/sda4 which is FAT32 - if that helps at all. 

Could the reason it says seven OS' be because of a previous Wubi installation? If that's the case, I already uninstalled Wubi so I can't understand why then.

---

### Post by cenzorrll on 2010-01-21
the problem you're having is that there are already 4 primary partitions.

if you want to have more, then you need to do some partitioning and make an extended partition to hold any more partitions. unfortunately windows needs to be on a primary partition to boot, so all three windows partitions need to be primary (i suspect that windows 7 makes that second smaller partition just to be a pain in the new linux users butt)

from what i get from your partition layout i see that you have windows 7 installed along with vista, with another partition just chilling out not being used and too small to really do anything with.

so if you want to use ubuntu you'll need to delete something if you don't want to install using wubi.

---

### Post by garvinrick4 on 2010-01-21
Boot in sda1
Windows 7 OS sda2
Vista=Recovery for Windows 7 (Linux see's recovery for 7 as Vista, Microsoft thing that is the way it is.
103 meg sda4 = have no idea what that is, Can be used as 4th primary but make it a extended
and use some of Windows 7 452 gigabytes. Make it a 100 or so as extended so in future if
you want to throw another version in for 3rd boot can stick in the extended parttion also.. 

Windows 7 does take up three primarys. With. SYSTEM/OS/Vista=Recovery for 7

---

### Post by cenzorrll on 2010-01-22
> **garvinrick4 said:**
> Windows 7 does take up three primarys. With. SYSTEM/OS/Vista=Recovery for 7

wow, now I know how microsoft is going to keep it's market from linux, make it near impossible for potential new linuxers to dual boot.

---

### Post by garvinrick4 on 2010-01-22
If you boot from your Ubuntu Live CD and pick to install answer questions and
when it gets to gparted to partition the drive there is an option the first one I believe
where it will do its partition for you and show you what it will look like in a graph then
tell you later what it is going to be. As long as you do not pick (take up whole drive) or (manual) it is really not to hard. I am by far no Linux Geek and I could not make a mistake
on my first load of Ubuntu if I stayed focused on what I was doing. A bit of reading if you want to understand. Good luck Partner, nothing good comes really easy now does it.

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?skyline=true&s=i](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?skyline=true&s=i)

---

### Post by steveneddy on 2010-01-22
Just set Ubuntu up in a Virtual Machine line VirtualBox.

It's much easier than partitioning.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Phantomhive on 2010-01-22
> **cenzorrll said:**
> the problem you're having is that there are already 4 primary partitions.

if you want to have more, then you need to do some partitioning and make an extended partition to hold any more partitions. unfortunately windows needs to be on a primary partition to boot, so all three windows partitions need to be primary (i suspect that windows 7 makes that second smaller partition just to be a pain in the new linux users butt)

from what i get from your partition layout i see that you have windows 7 installed along with vista, with another partition just chilling out not being used and too small to really do anything with.

so if you want to use ubuntu you'll need to delete something if you don't want to install using wubi.

I don't understand why Vista is there for one. It's not like I ever installed it.

As for virtual box, isn't that just less efficient? Similar to how Wubi would be less efficient?

---

### Post by teward on 2010-01-22
I'm glad I have a stack of WinXP Pro OEM discs lying around with valid keys :P.

Nevertheless, my gf's computer (a Netbook) has Vista w/ XP downgrade, and they list "Windows Vista (loader)" there as well.  Pain in the ***, huh?

---

### Post by Phantomhive on 2010-01-22
Heh. Can't seem to get Ubuntu working in VirtaulBox anyway.

64 Bit Operating system xD

---

### Post by Phantomhive on 2010-01-23
BUMP.

I am getting confused here. I don't even know why it says I have SEVEN OS's... How do I remove unnecessary ones?

---

### Post by cenzorrll on 2010-01-23
it doesn't say you have seven OS's, you have "Windows 7", microsoft's newest OS.

unless you're looking at something you haven't posted for us yet?

---

### Post by Phantomhive on 2010-01-24
[IMG]http://img12.imageshack.us/img12/8344/screenshotovq.png[/IMG]

Same thing appears on 9.4 and Linux Mint. I think the 13.1 GB "Windows Vista Loader" is my recovery drive because it's also 13.1 GB. HP Pavilion's have those recovery drives specifically I believe.

---

### Post by J V on 2010-01-24
seven is the name of the operating system wiseguy...

As said before, the 103 can be wiped at will, as also said, the vista is actually 7 recovery, and yes, virtualbox is very slow (Besides you will be using ubuntu as your main OS in no-time anyway), but no, wubi isn't (unless you used it for a year in which case it could be fragmented)

It can't "One click" install ubuntu next to windows because windows (quite cleverly) stuck small partitions on both sides of the main partition (which is needed for the space)

Go to specify manually, shrink the main partition, move the third one, and install ubuntu at the end.

---


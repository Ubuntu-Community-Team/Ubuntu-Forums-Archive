---
title: "How do I revert Linux to Windows OS"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by iLeet on 2009-02-06
Title says it all when I try to install say Vista or XP its apperently has problems. And my PC is 100% Ubuntu

So how do I switch back?

---

### Post by yeats on 2009-02-06
So are you trying to dual boot, or just wipe Ubuntu and go completely back to Windows?  Do you have the Windows Installation disk?  What sorts of problems are you having?

---

### Post by bobbob1016 on 2009-02-06
What errors are you getting from the Windows installer?  There should be no problem installing Windows over Linux (I'd say there is, but that's just me).  If you want to save your data from Linux, you have to copy it off to another drive, one that is Windows formatted.

Also, strictly speaking, there is no "revert back".  Linux is not Windows in any way, it's like the engine in your car.  Linux is not an add-on to Windows, you can't remove the Linux parts and get back to Windows, which is what "revert back" reads as to me.

---

### Post by HereInOz on 2009-02-06
It sounds like you have Linux installed on your machine, and you are now trying to remove it and install Windows XP.  If this is correct, read on.

There is a problem with the Windows XP installer where if your HDD is formatted as ext3, (and probably a few other formats but I haven't tested it), the Windows installer will not recognise the HDD, and tell you that there isn't one there.

The ways around this are:

Put a Windows 2000 CD in and start the install of that.  It will see the HDD.  Format the HDD as NTFS and then cancel out of the install, or just let it finish.  Then run the XP install and it will see the HDD.  Reformat the HDD during the install.

Use a partitioner - Partition Magic; GParted, or similar, and delete the ext3 partition and then create your NTFS partition.  Run the XP installer and re-format the NTFS partition during the install.

I apologise on behalf of Microsoft who were dumb enough to let this happen.

---

### Post by punx45 on 2009-02-06
> **HereInOz said:**
> 
I apologise on behalf of Microsoft who were dumb enough to let this happen.

they probably assumed anyone getting a taste of the *nix wasn't coming back  :lolflag:

---

### Post by cariboo on 2009-02-06
Win XP SP2  will recognize that there is a partition there, it just says it is an unknown type. You can delete the partiton and then repartition and let the windows installer do it's thing. I've done it a least a dozen times.

Jim

---

### Post by iLeet on 2009-03-19
I used GParter and made it so it say allocated now I change it to NTFS and its name is: /dev/sha1/
When I put my XP or Vista CD in it sats ITs not able to boot from it please insert System disk

I put in the Ubuntu Disk and it works same with FreeBSD
But not the Windows Versions

Why?

---

### Post by dwasifar on 2009-03-19
If your goal is to start fresh with a new installation of Windows (and not preserve your Ubuntu installation) then you don't need to create an NTFS partition with Gparted. 

Just choose Device>Create Partition Table in Gparted.  This wipes out the drive's existing partition table.  Then reboot from the Windows install disc and let it format and partition the drive for you.

---

### Post by mocoloco on 2009-03-19
> **iLeet said:**
> ...When I put my XP or Vista CD in it sats ITs not able to boot from it please insert System disk...

Are you sure you're describing the problem correctly?  From what you said, it's telling you that it cannot boot from your Windows CD, which has nothing to do with your HD.  Or perhaps it's trying to boot from the HD and finds no OS, in which case your BIOS is saying it has nothing to boot.
Make sure your BIOS is set to boot from CD/DVD. Also most Windows discs ask you to press a key to boot from the dics, otherwise it will revert to booting from the HD.

---

### Post by iLeet on 2009-03-19
> **dwasifar said:**
> If your goal is to start fresh with a new installation of Windows (and not preserve your Ubuntu installation) then you don't need to create an NTFS partition with Gparted. 

Just choose Device>Create Partition Table in Gparted.  This wipes out the drive's existing partition table.  Then reboot from the Windows install disc and let it format and partition the drive for you.
I did this, didn't work

> **mocoloco said:**
> Are you sure you're describing the problem correctly?  From what you said, it's telling you that it cannot boot from your Windows CD, which has nothing to do with your HD.  Or perhaps it's trying to boot from the HD and finds no OS, in which case your BIOS is saying it has nothing to boot.
Make sure your BIOS is set to boot from CD/DVD. Also most Windows discs ask you to press a key to boot from the dics, otherwise it will revert to booting from the HD.
I booted from it before I used Unix systems and it worked

---


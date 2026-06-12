---
title: "disk errors when dual-booting"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by languedoctor on 2011-05-14
Note: this problem is not specific to ubuntu/natty - I also experienced it when trying out the new build of OpenSuse with Gnome 3. I noticed a fairly extreme performance advantage using ubuntu (boot times: ubuntu < Windows 7 < OpenSuse/Gnome 3), so count me in the ubuntu camp. Since I've decided to go with ubuntu moving forward, I'll post it here.

Twice, I've set up dual booting on my laptop (with Windows 7). Both times, I have experienced disk error problems when subsequently booting to Windows. I've scheduled a chkdisk with repair, and that will clear up the problem. Once. As soon as I boot Linux (either ubuntu or OpenSuse) then go back to Windows, the disk error warnings return.

These warnings only started once I installed Linux dual boot. They only recur after I boot Linux (it's a nonissue running W7 only).

If I were in a position to drop W7 entirely, it would be no great issue, as I don't receive error messages on consecutive Linux boots, either. But that's not an option. It's going to take time to make the transition, and I can't justify making the leap without the ability to dual boot for some time, leading up to dropping Windows (eventually).

Does anyone know if these problems are common? Since it happened with both distros, is there a chance that I just need to do something differently when installing Linux?

Hard drive, btw, is an Intel X25-M G2. Not sure if it makes any difference that it's an SSD, but I'll mention it FYI

---

### Post by corrytonapple on 2011-05-14
The same thing happened to me after I installed Ubuntu.  IDK how long you have been using Ubuntu, but on my first reboot I had some issues, and had to use the recovery CDs (The full copy with 7 on it for a full install) to fix it.  If it is the second or so time, then just try again and see if it comes up again.  If it has been there after four-six times, then I would begin wondering what Ubuntu/OpenSUSE may be doing to the Windows partition.  If you are messing with the Windows filesystem while in Ubuntu, it will do that.

---

### Post by languedoctor on 2011-05-14
Oh, I'm definitely messing with the Windows file system :)

I've mounted the Windows partition to access files to test out software, test drive the linux version of Stata (still learning R), etc.

I wonder -- maybe if I use something like dropbox to share files between OSes, this won't happen. I'll give it a shot.

The only alternative I can think of is to wait until August, when I'll be getting a new laptop. Maybe I'm easily scared, but I need the laptop for work. I can't afford to have problems. That would probably be the safest way of all to make the transition - have separate machines for a while.

---

### Post by corrytonapple on 2011-05-14
IDK where you live, but if you can afford a $40 machine, go on to craigslist.org and see what you can pick up to mess with.  All those machines have XP right on them, all you have to do is install and Ubuntu and see what happens!
If you are just going on the Windows partition for documents, like going through the users to get to the documents, then that should not mess anything up.  Now, if you plan on keeping Windows, you could do what I do.  To briefly sum it up, you use a Live CD/USB to create a partition for Windows at a fixed size, create a Ubuntu partition at a fixed size, and then the rest goes to your data partition.  I already had Windows and Ubuntu installed, and I have a 250GB HDD.  My Windows partition is 60GB, and my Ubuntu partition is 30 or 40GB, IDK.  The rest, besides the partition for Windows recovery, and then the bootloader, all that, is for the data partition.  I got out about 119GB for it.  Make sure if you do, I will give you a thread to where you can read up on how to do it.  Both Windows and Ubuntu can access it for as long as it is formatted as NTFS.  I would recommend it for any dual booter, so you do not have files in Ubuntu that you cannot get in Windows, and you are not messing with Windows in any way.

---

### Post by languedoctor on 2011-05-14
Thanks - if you have a link to that thread handy, I'd absolutely be interested to read it.

---

### Post by corrytonapple on 2011-05-14
Okay, glad to help. :)  Here it is:
[http://ubuntuforums.org/showpost.php?p=10243553](http://ubuntuforums.org/showpost.php?p=10243553)
I get smart in post 16 and finally realize what I want to do.  Keep in mind I was reinstalling Ubuntu, and I am doing this all via Live CD.  You can do this without reinstalling Ubuntu or Windows.

---

### Post by duke.tim on 2011-05-14
I also dual boot using an NTFS for Windows, EXT4 for Ubuntu, and a NTFS partition for data.
If it is for work getting a cheap machine like @corrytonapple said is a great idea.

I dual boot without a problem. Maybe your hardrive has bad sectors? Chkdisk should have told you if you had bad sectors though.

It also might help if you posted what types of file systems you are using (i'm guessing NTFS, and EXT4)

This will show your partitions and file systems:
```
sudo fdisk -l
```

Here are some reading links about dual booting :)

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by wildmanne39 on 2011-05-14
> **corrytonapple said:**
> Okay, glad to help. :)  Here it is:
[http://ubuntuforums.org/showpost.php?p=10243553](http://ubuntuforums.org/showpost.php?p=10243553)
I get smart in post 16 and finally realize what I want to do.  Keep in mind I was reinstalling Ubuntu, and I am doing this all via Live CD.  You can do this without reinstalling Ubuntu or Windows.

Hi, that is a nice link full of useful information. Thanks for posting it.:D

---


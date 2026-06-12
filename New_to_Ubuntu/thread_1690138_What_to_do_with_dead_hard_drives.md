---
title: "What to do with dead hard drives?"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by jinba.ittai on 2011-02-17
Since my 750Gb Hdd died with windows on it, ive been permanently on ubuntu. 

But now i have 2 dead hard drives, a 1tb drive, and a 750gb drive. There is tuns of data id love to recover, but Im never gona send it to some one to recover themselves. 


It really sux to be stuck with two 320gb drives. Its a good amount of memory, but not enough for my needs. I know hard drives are cheap right now, but Im more worried about the drives i have. Maybe next paycheck ill get a 1tb drive from new egg, but i still want my data =[


And Since i have 2 320gb drives connected right now, is it possible in ubuntu 10.10 64 bit to run them in raid config?

---

### Post by oldsoundguy on 2011-02-17
I have lost 3 drives in 20 years of computing.  Two because of a power brown out and one where track zero went bad.

You should check your power source very carefully.

---

### Post by frotzed on 2011-02-17
As for your old drives and getting data off them: If the drives will still spin (and the controller card works) you can purchase a [universal drive adapter]("http://www.amazon.com/USB-2-0-Universal-Drive-Adapter/dp/B0012TOG08") and use it to get your data off them to another computer.  If you hook that up to your HDD and then to your computer and your computer can't mount the HDD it probably means the drive is completely dead and the data would have to be gleaned by a data recovery professional.  In my experience you're looking in the realm of $500+ for basic data recovery from a completely dead drive.

As for the future, what you're experiencing is precisely why data redundancy is vital.  A RAID is a good option, and it's one I personally like.  But a simpler option would be to simply have an external HDD that you make regular backups to.  All drives will fail, it's not a matter of "if". 

Also, I agree, suspect your power supply.

---

### Post by M0use on 2011-02-17
check the drive with the file system check, if the drive is mounted unmount it before running the command or it could result in data corruption


```
 fsck /devicetobechecked

```

---

### Post by jinba.ittai on 2011-02-17
Since ive lost the drives, ive upgraded from a 450 watt OEM PSU to a Cooler Master GX 650w. 



I put the 450w psu in another system but havent used it much, maybe best to throw it out and order another one of these Gx 650s as i was trying to build a home server. 



As for the hard disks, they both spin up, they both dont click or make any akward sounds, But they both are not detected by my operating system nor Bios. 

Well, the 1tb is detected, but Its unable to read/write and gives me i/o errors. Maybe the board for that one is a bit angry? This drive was never used in a desktop, but was in a portable enclosure. So maybe ill start looking for the board.

Got any ideas what to look for?

---

### Post by jinba.ittai on 2011-02-17
@Mouse



I just ordered a usb to sata set, so ill do that when it comes in. Im not in the mood for taking apart my pc to switch out hard drives all night.

---

### Post by Paqman on 2011-02-17
> As for the hard disks, they both spin up, they both dont click or make any akward sounds, But they both are not detected by my operating system nor Bios. 

You might be in luck then. If it's just the drive electronics that have gone, you may be able to repair them. If you swap the electronics for ones of the *exact* same model, you may be able to get them working. Have a look on eBay, and make sure you're getting identical parts.

---

### Post by jwcalla on 2011-02-18
If you're looking into a new HDD, sign up for the newegg e-mail deals.  They have hard drive sales all the time for good prices.  The 2TB green drives from WD or Samsung tend to go $70-$80 after MIR.  Even some of the externals are that cheap.

---

### Post by frotzed on 2011-02-18
> **Paqman said:**
> You might be in luck then. If it's just the drive electronics that have gone, you may be able to repair them. If you swap the electronics for ones of the *exact* same model, you may be able to get them working. Have a look on eBay, and make sure you're getting identical parts.

^This.  If I understand correctly the above process is actually one that data recovery companies will often try. Though I admit I've never tried it.

---

### Post by PunkLV on 2011-02-19
You might want to try out **testdisk**. It manages partitions, MBRs and can recover data to some extent, if mechanical parts are intact of course.

---


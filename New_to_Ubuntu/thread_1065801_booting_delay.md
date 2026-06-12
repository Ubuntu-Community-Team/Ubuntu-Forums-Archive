---
title: "booting delay"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by anoopsnm on 2009-02-10
error_request:I/O error,dev sr0 sector 1431040
Buffer I/O error on device sr0,logical block 357760

i get this message repeatedly before ubuntu is loaded.plz tell me how can i overcome this problem?bcoz of this,its now taking a few time get booting complete and reach the desktop.

---

### Post by LowSky on 2009-02-10
looks like a bad USB device or your running 64Bit edition of Ubuntu?

---

### Post by vikramaditya on 2009-02-10
PC is trying to boot from CD drive - is your live disc still in that bad boy?  might just want to go into your bios and change 1st boot device to whichever hdd ubuntu is installed on.

---

### Post by anoopsnm on 2009-02-10
the boot device is ok.actually i didnt have this problem earlier.is this due to any bad block?am using xp and ubuntu8.10 in dual boot.i had a power failure & i dont have a UPS.but at that time i was using xp.

---

### Post by supersonicdarky on 2009-02-10
if you want to test the boot drive for errors
1) sudo shutdown -rF now (restarts and forces fsck on reboot)
2) sudo e2fsck -c /dev/*drive* (checks for bad blocks and adds them to the fs to not be used)

I'm not sure if you can do 2 while using the partition/drive. Might need to be done from the live cd.

More info: man e2fsck

---

### Post by anoopsnm on 2009-02-10
~$ fsck
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.


i have installed ubuntu on /dev/sda3.if i unmount it,and then run fsck,will it create problems?

---

### Post by Lerxst51 on 2009-02-10
As long as the partition is unmounted your okay.

---

### Post by anoopsnm on 2009-02-11
sudo umount /
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


what to do next?

---

### Post by skymera on 2009-02-11
Boot in a LiveCD and run from there

---

### Post by avaxdownload on 2009-02-11
Great!

---

### Post by anoopsnm on 2009-02-12
what about the following command?

sudo umount -l  /
or
sudo umount -l /dev/sda3/

sda3 is where i installed ubuntu.

i think it does unmount the drive.after running that command i run fsck command.then the system appeared to be hanged.
how long does the fsck command to complete its operation?i waited for almost 3 hrs,but no response.i saw somewhere that it takes long time(8 or 10 hrs) to complete.isn that true?
will running fsck command overcome the problem i said at the beginning of the thread?

---

### Post by supersonicdarky on 2009-02-13
um... unmounting root? it shouldn't even allow it. But it seems like you hung up your system with that action. While fsck does take some time (perhaps 10-15 min on a tb disk), but not 3 hours =/

try what I suggested earlier: **sudo shutdown -rF now** to force it to reboot and fsck then

---

### Post by anoopsnm on 2009-02-13
i tried **sudo shutdown -rF now**.it says its clean.
but still my problem persists,which is,

[COLOR="Red"]error_request:I/O error,dev sr0 sector 1431040
Buffer I/O error on device sr0,logical block 357760[/COLOR]
this comes repeatedly while booting.

is it bcoz of any bad blocks which occured due to sudden power failure.

---

### Post by supersonicdarky on 2009-02-13
[s]well try booting from a live cd and scanning for bad blocks using e2fsck

or it could be that its a device that doesn't get fsck'd by default (such as an external hdd) is acting up[/s]

Just noticed its /dev/sr0 thats acting up. That's generally your cd/dvd drive. Do you have any disks in there? Possibly scratched ones?

just in case post output of **df -h**

---

### Post by anoopsnm on 2009-02-14
ya...i had a cd in my cd drive.and that cd was in my cd drive when the power failure occurred.now i have removed it  and  everything has become fine.now there is no problem while booting.

@ supersonicdarky,

can u plz tell me in detail what was it all about?y did that happen since my first boot device was hdd.?

---

### Post by supersonicdarky on 2009-02-15
The blackout caused the options to be changed in bios perhaps? I had my boot order change once when I reset the pc while it was booting. Took me months to figure out why it wasn't detecting an os (had to use supergrub disk each time I booted) >_>

So yeah, take a look at the boot order in the bios.

---

### Post by anoopsnm on 2009-02-16
thank you for all who responded to my queries.

---


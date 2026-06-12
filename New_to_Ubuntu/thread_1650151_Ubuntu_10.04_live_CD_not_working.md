---
title: "Ubuntu 10.04 live CD not working"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Worsel on 2010-12-21
I have a problem running the Ubuntu 10.04 live CD on my Vostro 1000. When the CD boots up I get vertical red and blue lines and nothing else. The specs for the vostro 1000 are as follows:

AMD Athlon 64 X2 TK-53 1.7 GHz
ATI Radeon Xpress 1150
2gb RAM

I think it might be a graphics card problem as I have had driver problems with Windows 7. Hence wanting to switch to Ubuntu. Any help would be much appreciated. :)

---

### Post by mastablasta on 2010-12-21
I think these vostros came preinstalled with ubuntu in some cases. Are you using porprietary drivers?

---

### Post by Worsel on 2010-12-21
I'm using the ATI drivers.

---

### Post by mastablasta on 2010-12-21
Sorry i just saw you have tried a live session (which would use opensource drivers). Xpress series is not supported anymore by ATI so opensource driver is the best you can get in linux. try 10.10 it might have a newer version of the driver. 
 
Another option is to update later with another drivers (testing version i believe), but i haven't played arround with this...

---

### Post by Worsel on 2010-12-22
I have tried the Linux Mint 10.10 live cd and that has the same problem. Not sure what to do.

---

### Post by Scott. on 2011-01-30
I also have a Vostro 1000.  I also have the same problem with Ubuntu 10.04, 10.04LTS, 10.1, Alpha 11.04.  It appears I will be stuck using 9.1 forever.  This is disappointing.   Especially since I've found some Terminal command line solutions.  However, I can't type them in because I can't view anything on my screen except vertical lines.  Is there a way to install say ver. 10.1 and then make changes to the OS?  Or...could I make the changes in 9.1 that might carry into an update to 10.1?

---

### Post by kansasnoob on 2011-01-30
Try the "nomodeset" option under F6 during boot:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If that works with the Live CD you may need to do likewise with grub2 after installing:

[http://ubuntuforums.org/showthread.php?t=1626862](http://ubuntuforums.org/showthread.php?t=1626862)

---

### Post by Scott. on 2011-02-06
Thanks for the links.  I've made some progress.  I can get the Live CD to work properly.  However, I'm having trouble changing the actual GRUB file on my HD after installing ver. 10.10 64bit.  It's a Read Only file.  Because I've booted from the CD it took a while to find the right file.  After I did, I couldn't get around the READ ONLY attribute.  I finally managed to get around it with a 9.1 USB stick.  The only thing left was to update-grub.  I couldn't manage this on the proper disk.  After several hours, I had to use Clonezilla to reinstall 9.1 into the EXT4 partition.  I'm so close.  Any ideas?

---

### Post by Worsel on 2011-03-31
> **kansasnoob said:**
> Try the "nomodeset" option under F6 during boot:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If that works with the Live CD you may need to do likewise with grub2 after installing:

[http://ubuntuforums.org/showthread.php?t=1626862](http://ubuntuforums.org/showthread.php?t=1626862)

The problem is I can't even get as far as the livecd boot.

---

### Post by Worsel on 2011-04-03
> **Worsel said:**
> The problem is I can't even get as far as the livecd boot.

Everything is solved now. I'm running ubuntu 10.10. Thanks for the help people.:D

---


---
title: "How &amp; when to use fsck?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by jkb609gi8 on 2010-02-01
I am using a Dell 600m And Have been running Ubuntu 9.04, OK for a couple months.
 When I booted up the other day ago; I get a scan happening; 

“Unclean shutdown, checking drives:
 

    *************************
 And then it goes to like this;
 

 Checking drive /dev/sda1: 68% (stage 1/5, 429/436)
 Error reading block 14057477 (attempt to read block from filesystem resulted in short read) while getting next inode from scan.
 

 /dev/sd1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
             (i.e., without -a or -p options)
 fsck died with exit status 4
 [RIGHT][fail][/RIGHT]
  * An automatic file system check (fsck) of boot filesystem failed.
 A manual fsck must be performed, then the system restarted.
 The fsck should be performed in maintenance mode with theroot file filesystem mounted in read-only mode.
   *The root filesystem is currently mounted in read-only mode.
 A maintenance shell will now be started.
 After performing system maintenance, press Control-D
 to terminate the maintance shell and restart the system.
 bash: no job control in this shell
 root@bread-laptop:~#
 

    **********************
 

 Ok, so I press Control-D and the computer restarts and does the same thing over, and over....... over and over

 

    **********************
 Next I reboot, hit f2 and head into the bios and make sure the system will start of the the CD driver.
 Next I reboot, hit f12 and head into the boot menu and chose Diagnostics.
 This scan is called a "Pre-boot System Assessment Build 3012"
 Device: Hard Drive
 Test: Start DST Short Test
 Status: Error detected!
    ***
 Test Results : Fail
 Error Code : 1000-0146
 Msg: Unit 0:DST LOG contians presious error(s).
    **********************
  Next I insert the Ubuntu 9.04 DC and reboot, and the system boots into the 

Ubuntu 9.04 on disk.
 I boot onto the CD and try to re-install 9.04.
 I have no such lucky.
 ***

So next I go into the live feature of the CD.
 And I open the terminal.
 The Terminal is called ubuntu@ubuntu
 Read the info on sudo, and then reset clear.
 Then I try and type in [sudo fsck] at ubuntu@ubuntu
 

 I get ubuntu@ubuntu:~$ sudo fsck
 fsck 1.41.4 (27-Jan2009)
 ubuntu@ubuntu:~$  
 

 I have never used command lines before, not that I am aware of.
 I have been searching the ubuntu form looking for "How to use fsck"
 Even if I did manage to get the "file system Checker" fsck working, I would not know how to repair the bad sectors.
 

 Does anyone know how to re-install the 9.04 O/S or repair the errors on the current o/s....???

---

### Post by bruno9779 on 2010-02-01
Status 4 in fsck means "detected but not repaired".

Try booting with live CD and run:

```
sudo fsck -r /dev/sda
```

With the flag -r it will repair automatically, but only after asking for confirmation (it is better this way, so you can have an idea of how bad the situation is)

Please post the output you get

---

### Post by bruno9779 on 2010-02-01
On the other end, 

```
Error Code : 1000-0146
```

means your HDD is on his way out...
Google it, there are a lot of Dell user with this issue.

---

### Post by jkb609gi8 on 2010-02-01
Here is what I get when I enter ubuntu@ubuntu:~$ sudo fsck -r /dev/sda

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ububtu@ubuntu:~$

(I don't have anything open other than the desktop.)

---

### Post by 3rdalbum on 2010-02-01
> **jkb609gi8 said:**
> Here is what I get when I enter ubuntu@ubuntu:~$ sudo fsck -r /dev/sda

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ububtu@ubuntu:~$

(I don't have anything open other than the desktop.)

Which desktop? The desktop that is running off the disk that you're trying to check? If so, then you can't do it this way - boot from a live CD and run that command, making sure that the disk is unmounted (if it appears on the desktop, then right-click it and choose Unmount).

If you can still get into the maintanence mode prompt, then you can run 'sudo fsck /dev/sda' (or sudo fsck /dev/sda1) there and it will work.

---

### Post by jkb609gi8 on 2010-02-01
Yes I see what you mean about the Error Code 1000-0146

I had a similar problem with an Acer, except it lost part of the grub, however it behaved the similar to this problem. It was a used lap-top and someone had password protected the Bios feature that allowed one to boot from a CD ........ so it went into the junk box.......!

I would purchase a desktop however they use to much power, here were I live we are off the grid, have a solar power system and have to conserve energy. These laptops seem to heat up so much, and perhaps they are cooking out........

---

### Post by jkb609gi8 on 2010-02-01
YES The desktop that is running off the CD disk. I will try what you say here.

---

### Post by jkb609gi8 on 2010-02-01
The desktop must be off the live cd because there is only "install" and "Examples" icons present. If it was the hard drive, I think my desktop would be as I had it set up.

---

### Post by jkb609gi8 on 2010-02-01
I can go into my Computer-File Browser, and mount the hard-drive then unmount it, so the hard-drive must be unmounted. The hard drive is unmounted.

---

### Post by jkb609gi8 on 2010-02-01
I cannot seem to find an application called Maintenance Mode. I see instructions for Maintenance Mode in Ubuntu form posted by [ jlyn sept 19th 2007 [B]Re: Getting to Maintenance Mode ]
**however I cannot see how one could access it from the grub.**

[/B]

---

### Post by jkb609gi8 on 2010-02-01
I am going to put this lap-top aside, FOR THE TIME BEING. IF Anyone else out there who wants to make suggestions on how to fix these problems, feel free....  
Please ad to this string at any time in the future.
Something tells me this will not be the last computer with these sorts of booting problems.....

---

### Post by philinux on 2010-02-01
Boot the laptop with the livecd. 

Use it and a usb stick to copy any files you need from the hard drive.

Buy a new harddrive and reinstall.

[http://forums.techguy.org/windows-xp/546422-please-help-dst-short-test.html](http://forums.techguy.org/windows-xp/546422-please-help-dst-short-test.html)

---

### Post by bruno9779 on 2010-02-01
> **philinux said:**
> boot the laptop with the livecd. 

Use it and a usb stick to copy any files you need from the hard drive.

Buy a new harddrive and reinstall.

[http://forums.techguy.org/windows-xp/546422-please-help-dst-short-test.html](http://forums.techguy.org/windows-xp/546422-please-help-dst-short-test.html)

+1

you can get one for about 60$

[http://www.google.com/products?q=Dell+600m+hdd&scoring=pd&show=dd&sa=N&start=100](http://www.google.com/products?q=Dell+600m+hdd&scoring=pd&show=dd&sa=N&start=100)

---


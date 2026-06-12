---
title: "KleanSweep DISASTER"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Crossbow on 2010-02-11
I just tried to use KleanSweep. I thought I was being safe because I archived everything. Now I can't open a single file, even the ones I just archived. I can't add or delete any applications. I really screwed myself over. 

So then I come here and search "KleanSweep" and discover it will destroy your system. I'm such an IDIOT for not looking here first! 

Okay, so, how do I fix this? I really don't want to just do a reinstall because I had so much stuff that I'd like to recover. Plus I'm not sure I can still burn a disc after what I've done. 

PLEASE HELP!

**PS.** On the thread where I learned KleanSweep is a bad idea, there was discussion of what to do **instead** but not what to do if you've already done it. The thread was from back in August.

**ETA:** Fantastic. I thought I could boot from my old 7.10 disc and then burn a new one of 9.10 but I can't. There's not room on the disc, obviously. Is there ANYTHING I can do? Are all the photos on my hard drive lost forever now? I can't boot up from my hard drive at all. I'm booting from the 7.10 disc right now. I can burn a 9.10 CD at a friend's house or something, but I still just don't want to lose everything if I can get around it.

---

### Post by ankspo71 on 2010-02-11
Hi,
I'm not sure of what system files it would have removed, but running the command
```
sudo apt-get install --reinstall ubuntu-desktop
```
usually helps. 

If you can't open a terminal or Synaptic Package Manager, then try pressing Ctrl + Alt + F2 first, then login at the prompt, then run the above code.

If you have a linux live cd somewhere (any version of *ubuntu should do) You can boot into that (live session) and recover your files by placing those files on a separate partition, or on a usb drive.
Hope this helps.

---

### Post by Crossbow on 2010-02-11
> **ankspo71 said:**
> Hi,
I'm not sure of what system files it would have removed, but running the command
```
sudo apt-get install --reinstall ubuntu-desktop
```
usually helps. 

If you can't open a terminal or Synaptic Package Manager, then try pressing Ctrl + Alt + F2 first, then login at the prompt, then run the above code.

If you have a linux live cd somewhere (any version of *ubuntu should do) You can boot into that (live session) and recover your files by placing those files on a separate partition, or on a usb drive.
Hope this helps.

Thanks for replying!

I can't boot up from my hard drive at all. I get a log in option if I do it in safe mode - should I go there? (Assuming I can remember how to do that.)

I'm on a live CD now, but I didn't think you could access your hard drive files from it. How do I do that? 

Apparently KleanSweep deletes a LOT of system files by default and shouldn't be used by amateurs like me, even with archiving.

---

### Post by ankspo71 on 2010-02-11
Hi,
If you didn't change your boot order since you have installed ubuntu, or encrpt any directories, then you should still be able to access your files by live cd.

Click on the places menu to see which filesysytems you have available. If you dual boot with windows, then you should see the filesystem for windows there. If you have a usb mounted drive you should be able to see it there too.

Now go to the terminal of your live cd and type in gksudo nautilus

Now that nautilus is running in sudo mode, you will have access to the files on all partitions. 

All you need to do now is navigate to your files, right click and select copy. Go back and open the location that you want to save the files in and right click and select paste.
Your files will start transferring over.

I am uploading a screenshot where you can see where to choose between partitions in nautilus, just like in the places menu.

Hope this helps.

---

### Post by Crossbow on 2010-02-11
Okay, I've got nautilus running in sudo mode, but the "places" options are: 
root
desktop
file system
trash

The "home" option in the file system only takes me to the empty folders on the CD.

EDIT: Oh my gosh, wait. After sitting here staring at it for 10 minutes, suddenly a "disk" option popped up. All my stuff is there. THANK YOU.

ETA: I can't look at some of the folders. I wonder if I can still copy them.
ETA: No, I can't. I can't copy any of it.

---

### Post by Crossbow on 2010-02-11
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 23.5kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main ubuntu-desktop 1.79
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop --fix missing
E: Command line option --fix is not understood
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 23.5kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main ubuntu-desktop 1.79
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Internal Error, ordering was unable to handle the media swap
ubuntu@ubuntu:~$

---

### Post by ankspo71 on 2010-02-11
> **Crossbow said:**
> ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 23.5kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main ubuntu-desktop 1.79
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop --fix missing
E: Command line option --fix is not understood
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 23.5kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main ubuntu-desktop 1.79
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.79_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Internal Error, ordering was unable to handle the media swap
ubuntu@ubuntu:~$

Hi,
you're getting that error because I think you tried it from your gutsy live cd, which happens to be no longer supported by Ubuntu. If you can do the same from your 8.04 installation, I think it might fix the problem be reinstalling any system files or folders that were removed by Kleansweep.

I'm a dual booter so I had to go look this next part up...
[http://unixlab.blogspot.com/2009/08/exploring-ubuntu-recovery-mode.html](http://unixlab.blogspot.com/2009/08/exploring-ubuntu-recovery-mode.html)
This explains how to get to the recovery menu in 9.04 (8.04 should be similar).
I would choose netroot menu option to run the command 
```
sudo apt-get install --reinstall ubuntu-desktop
```
but the other menu options might help as well.

I'm surprised nobody else here has came to help with this by now. :-s

---

### Post by Crossbow on 2010-02-11
The forums haven't been as helpful this time as they were when I first started using Ubuntu in 2007. 

I finally went ahead and just installed 9.10. I think everything important is saved somewhere else - my resumes are on a thumb drive (I hope!) and my artwork is on CDs somewhere - and the photographer who took shot my portfolio has them on his hard drive anyway - and unlike me, he knows computers and wouldn't lose things like this. 

Thanks for all your help. I'm glad at least one person jumped in!

---


---
title: "Errors in installing wubi - Ubuntu 9.10"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Spantiznik on 2010-01-09
I have been attempting to dual boot on my computer which has Win7 installed on it. I want to be able have ubuntu 9.10 installed on a different HD/Partition. 

I have a second HD that I have partitioned and have setup a 50gig Partition to install Ubuntu, I keep getting the the following in th wubi-9.10ubuntu1-rev160.log file.

Debug Distro: Checking whether D:\ is a valid ubuntu CD
Debug Distro: does not contain D:\casper\Filessystem.squashfs

The install processes gets about 40% of the first step of initializing, then I get a popup window that tells me to check the wubi-9.10ubuntu1-rev160.log file.

I get this popup window that says Ubuntu Installer. "an error occurred: Invalid argument" and then it states to check the log file.

Any idea's ?

Thanks
Randy

---

### Post by darkod on 2010-01-09
> **Spantiznik said:**
> I have been attempting to dual boot on my computer which has Win7 installed on it. I want to be able have ubuntu 9.10 installed on a different HD/Partition. 

I have a second HD that I have partitioned and have setup a 50gig Partition to install Ubuntu, I keep getting the the following in th wubi-9.10ubuntu1-rev160.log file.

Debug Distro: Checking whether D:\ is a valid ubuntu CD
Debug Distro: does not contain D:\casper\Filessystem.squashfs

The install processes gets about 40% of the first step of initializing, then I get a popup window that tells me to check the wubi-9.10ubuntu1-rev160.log file.

Any idea's ?

Thanks
Randy

First of all, you have a different kind of problem, so you should open your own thread, easier that way.
Second, installing wubi is NOT dual boot, not in the real meaning. Wubi is just virtual ubuntu working inside windows, without its own partition and filesystem, and without grub at all (only virtual grub that you see).
As long as you are trying to install it through windows and on ntfs partition, I don't know why it would give an error. I don't use wubi personally and don't know much about it.

---

### Post by Spantiznik on 2010-01-09
Here is the last couple of lines of the log file that was created.


	 	 	 	 	  IOError: [Errno 22] Invalid argument
 01-09 15:14 DEBUG  CommonBackend: Searching for local ISO
 01-09 15:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
 01-09 15:14 DEBUG  TaskList: New task get_metalink
 01-09 15:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
 Traceback (most recent call last):
   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
   File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
   File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
 Exception: Cannot download the metalink and therefore the ISO
 01-09 15:14 DEBUG  TaskList: # Cancelling tasklist
 01-09 15:14 DEBUG  TaskList: # Finished tasklist


Thanks

---

### Post by darkod on 2010-01-09
As you can see yourself, it's complaining about not being able to download the ISO. I really have no clue why. Internet access working fine I guess?
Another option is to download the ISO yourself first. Then if you put wubi.exe and the ISO (packed as it is, not extracted) in the same folder, it will use the local ISO, but only if it can find it in the same folder.
Also they have to match, be of the same version. wubi.exe is inside the ISO too so you can use some program to extract just wubi.exe from the ISO and then put it in same folder with the ISO file and start the install like that.

---

### Post by Elfy on 2010-01-09
please do not hijack current threads - what might appear to you to be the saem sort of issue could be something completely different, thank you.

If you were unsure how to start a thread - [http://ubuntuforums.org/showpost.php?p=4527023&postcount=3](http://ubuntuforums.org/showpost.php?p=4527023&postcount=3)

---

### Post by Spantiznik on 2010-01-10
ForestPixie, Sorry about not starting my own thread.

Darkod, Internet connection is working. Even connected the PC directly to the Modem so I wasn't going through my router. It is very strange.

I attempted the install from Boot up off the Ubuntu cd and to install it that way on to the partition I setup just for it. no go, Just sits there at the ubuntu symbol. And it doesn't move, waited a good hour to see if it was going to do anything.

---

### Post by sandyd on 2010-01-10
two words: verify CD.

---

### Post by Spantiznik on 2010-01-10
Have done that already carlee !!

---


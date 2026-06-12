---
title: "My Computer is Having a Restart-gasm"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by DocDubs on 2010-03-14
I'm very, very new to Ubuntu and to this forum, so I apologize right now for my what is surely a question that's already been dealt with elsewhere.  But I'm kind of freaking out ...

I just purchased an Acer Aspire One yesterday and, being a long-time hater of Windows, I loaded Ubuntu onto it.  When I did, I had Ubuntu partition my hard drive.  And everything worked swimmingly.  I set up everything in Ubuntu and Windows, and was happily moving back and forth between operating systems.  

This morning, I was fiddling around in Ubuntu, figuring out the OS and the sorts of things I could do with it.  And some automatic updates came up, which I immediately loaded.  The system asked me to restart, which I did after everything had finished.  After the restart, I actually went into Windows to get some work done--I teach, and I needed to add some grades into the Excel gradebook.  After an hour or so of grading and emailing, I shut down my system and went to lunch.

When I came back, I turned the laptop back on to play with Ubuntu some more, and what I discovered was a computer that would turn on, get to a screen that said "LOAD GRUB" or some such, and then restart ...

Over and over and over again.

I'm now running Ubuntu off of a flash drive, and flipping out a little bit.  Here are my questions:

1)  How do I make the restart-gasm stop?
2)  Why can't I get to either OS?
3)  And what is the easiest solution to this problem?

Thanks in advance for your help!  And I apologize for what is probably my own idiocy and oversight.

---

### Post by J V on 2010-03-14
Not sure what exactly the problem is, but reinstalling grub should do the trick...

> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by PPPilot on 2010-03-14
Sounds like your grub.cfg file may be bad. Go ahead boot from your flash drive then open a terminal. Enter ```
sudo update-grub
```Enter your password at the prompt.

You should get output something along these lines. 
```
john@john-desktop:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdc5
done
```You can see my last two Ubuntu versions and a version of Open SUSE that I have on a seperate drive. You, of course, would see your windows OS. When you are done, reboot from your hard drive. Hopefully all will be well.

---

### Post by DocDubs on 2010-03-14
Thanks for the advice, fellaz.  But I realized pretty quickly that I was a noob in terminal hell.  In both cases, GRUB didn't exist at all.  So I installed it, but that didn't necessarily help.  
 
So ... I fell on my sword, and punted.  I deleted the previous Ubuntu partition and reinstalled the program.  And everything seems to be peas and carrots again.
 
I'm terrified about the update, though.  Should I just not update any of the grub files?
 
Thanks again, even though I'm a terrible, impatient student.

---

### Post by J V on 2010-03-15
Keep updating, its not that hard btw...

If you installed ubuntu on hard drive 1 partition 1 on a sata, its ID is sda1(sata disc A, partition 1)

Then turn the A into a 0 (drive 0) and the 1 into a 0 (Grub counts from 0 up) and voila, do the things on that list and it will be fixed... if you run into the problem again, thats only good news! You see, everyone needs to learn this sometime...

---

### Post by themusicalduck on 2010-03-15
You could try and do updates, but uncheck any updates that are called grub-pc or anything with grub in the name..

That's if the problem was with grub and not something else. But at least you can re-install it if you need to. So feel free to test things.

---

### Post by presence1960 on 2010-03-15
oops double post somehow.

---

### Post by presence1960 on 2010-03-15
Lot of guessing going on about whether you have grub legacy or grub 2. No one can tell until we get more info from you about your setup & boot process. I prefer to see exactly what you have before making suggestion(s).

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by audiomick on 2010-03-15
Have a look here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
It is the same thing as prescence1960 has recommended, but there is a bit of an explanation of what is in the results.txt file that is produced. It might help you understand it a bit.

---

### Post by presence1960 on 2010-03-15
> **audiomick said:**
> Have a look here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
It is the same thing as prescence1960 has recommended, but there is a bit of an explanation of what is in the results.txt file that is produced. It might help you understand it a bit.

Yep audiomick the boot info script is a great troubleshooting tool for boot problems. It gives important accurate info on one's set up & boot process. I almost always request it's use before giving advice because experience has shown that people whether intentionally or not do not give accurate info about their setup or the steps they have taken prior to asking us for help. The boot info script eliminates that as it reports exactly on the setup and boot process.

---

### Post by audiomick on 2010-03-15
> **presence1960 said:**
>  I almost always request it's use before giving advice ...
I know, I've noticed...;) I can't read the results.txt very well, but am often surprised at how much I can get out of it. meirfra did the world a favour by writing it.

---

### Post by presence1960 on 2010-03-15
> **audiomick said:**
> I know, I've noticed...;) I can't read the results.txt very well, but am often surprised at how much I can get out of it. meirfra did the world a favour by writing it.

Yes, meierfra does a lot of good things in here. He is also knowledgeable about Windows as well. What I really like about him is his ability to critique without ruffling feathers, something I am deficient at doing. But Rome was not built in a day. I am aware of that deficiency or defect and am willing to change. Hopefully I will progress towards that goal. Only time will tell.

---


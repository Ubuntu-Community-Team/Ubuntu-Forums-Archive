---
title: "Ubuntu questions and such."
date: 2010-02-25
forum: New to Ubuntu
---

### Post by JackOfBlades on 2010-02-25
Hello, I'm Jack. I'm new to Ubuntu and I have a HP Pavilion dv6990la laptop. I got to intall Ubuntu just today after weeks of fighting against my laptop until I finally won. The last error I had last time I was trying to install was the blinking tty login screen. I installed it again, one last time and well, lucky me, it worked. But now I need suggestions of what to do now and I have a couple of questions, if you guys would be so kind to help me:

[LIST=1]
[*]My video card is a nVidia GeForce 7150M, how do I enable it? It's important to notice that the proprietary hardware thingie doesn't recognize any proprietary hardware.
[*]Why can't I download from the Ubuntu Software Center? I wanted to download TuxGuitar and it says that it's not available from the data, if I recall correctly; and I can't get my facts straight about that last thing since the USC won't open up now.
[/LIST]
That's all for now. Thanks for your help and your time. And if anyone wants to give me terminal advice, I read the terminal tutorials but I'm still a neophyte in that area. So bear with me, please. D:

---

### Post by gallifrey on 2010-02-25
Well i can't answer the question about your NVidia card, but for the software centre, you need to enable the *partner* repositories. To do this, go to System -> Administration -> Software Sources. When you have the Software Sources window open, click on the 'Other Software' tab, and check the boxes for the partner repositories. Click 'Close', let it reload, then try downloading your software from the Software Centre.

---

### Post by mikeyphi on 2010-02-25
Your video card is supported - so should be working OK.

Open System/Admin/Synaptic
Do a search for 'tuxguitar'
if it's there - download
if  it's missing, on Synaptic, select settings/repositories
make sure that the first 4 boxes are ticked.
Then reload (blue arrow) and search again.

---

### Post by themusicalduck on 2010-02-25
I think the problem is that you haven't loaded your sources yet.

Go to System > Administration > Software Sources and check all of the boxes except for "Source code".

Close that window and open a terminal (Applications > Accessories > Terminal) and type in ```
sudo apt-get update
``` enter your password and let it do its thing.

Once it's done, try your drivers again and the software centre should work too.

---

### Post by JackOfBlades on 2010-02-25
Thank you for your fast answers! Also, I don't know why bu when I suspend, the darn thing won't come back from its sleep! (I'm being literal, but yes, it won't go back to normal :S) And after I turned it off so I could restart, the GRUB loaded, the little white Ubuntu logo appeared for a little while, then this message: 

fsck from util-linux ng 2.16
/dev/sda1: clean, 131693/14712832 files, 1530674/58828014 blocks

What did I do this time?

---

### Post by 2hot6ft2 on 2010-02-25
For the graphics card if it's not showing anything for it in
System > Administration > Hardware drivers
you could go to nvidia.com and under download drivers search for your cards drivers and download them and install them following the instructions on their site. I just looked it up and for 32 bit linux it has:
> Linux Display Driver - x86
 Version: 190.53 Certified


---

### Post by BrandonBan6 on 2010-02-25
> **JackOfBlades said:**
> Thank you for your fast answers! Also, I don't know why bu when I suspend, the darn thing won't come back from its sleep! (I'm being literal, but yes, it won't go back to normal :S) And after I turned it off so I could restart, the GRUB loaded, the little white Ubuntu logo appeared for a little while, then this message: 

fsck from util-linux ng 2.16
/dev/sda1: clean, 131693/14712832 files, 1530674/58828014 blocks

What did I do this time?

Doing a hard reboot on Ubuntu is a little rough going on the system. 
Follow this guide to reboot next time: [http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

To fix the file system check, try running a fsck from recovery root. 
1.) Reboot (try the guide posted above)
2.) after your BIOS splash screen, you'll see a blinking cursor and "Grub Loading", hit the escape key. 
3.) If you timed the step above just right, you will see a menu of kernel options, usually the second from the top ends in (recovery console), choose this one. 
4.) From the new menu that shows up, arrow down to root shell. 
5.) type: fsck -y /dev/sda1
6.) after that completes, type: shutdown -r now

---

### Post by quadproc on 2010-02-25
I just wanted to supply a little illumination: the line regarding fsck (which is the command that does a File System ChecK) indicates that the file system was satisfactorily fixed up by fsck; you need not take any special action on account of this.  The reason why fsck had to fix the file system was the sudden and unexpected stoppage of the computer; a UNIX or Linux system keeps certain information regarding the system in a special place on disk, and when the system is shut down normally this information is organized and stored for the shutdown so that the next startup will occur with things in a proper state.  But the sudden stoppage prevented the system from organizing the special place so, when the system was next restarted, the startup software detected this and went in to fix things.  This time, it succeeded.

To be a little more verbose about why things need to be organized, consider that you may have been creating a file with some application program such as an editor or an email program when the system was stopped.  There would have been no opportunity for the system to update the open file that you were creating and the data needed to figure out where to put the next character into the file would have been lost.  This would mean that the file was now inconsistent and was damaged, you might say in a state of limbo.  The system cannot work with damaged files, and it knew that there was a possibility of damaged files so it ran fsck to find out.  In your case, it was able to fix things this time but it sometimes may not be able to.  If it cannot then quite a bit of work can be involved, and you may lose one or more files; generally, that's a bad situation.  It is a really good idea to do a normal shutdown if at all possible.

I hope that this sheds some light on the subject.

quadproc

---

### Post by BrandonBan6 on 2010-02-25
> **quadproc said:**
> I just wanted to supply a little illumination: the line regarding fsck (which is the command that does a File System ChecK) indicates that the file system was satisfactorily fixed up by fsck; you need not take any special action on account of this.  The reason why fsck had to fix the file system was the sudden and unexpected stoppage of the computer; a UNIX or Linux system keeps certain information regarding the system in a special place on disk, and when the system is shut down normally this information is organized and stored for the shutdown so that the next startup will occur with things in a proper state.  But the sudden stoppage prevented the system from organizing the special place so, when the system was next restarted, the startup software detected this and went in to fix things.  This time, it succeeded.

To be a little more verbose about why things need to be organized, consider that you may have been creating a file with some application program such as an editor or an email program when the system was stopped.  There would have been no opportunity for the system to update the open file that you were creating and the data needed to figure out where to put the next character into the file would have been lost.  This would mean that the file was now inconsistent and was damaged, you might say in a state of limbo.  The system cannot work with damaged files, and it knew that there was a possibility of damaged files so it ran fsck to find out.  In your case, it was able to fix things this time but it sometimes may not be able to.  If it cannot then quite a bit of work can be involved, and you may lose one or more files; generally, that's a bad situation.  It is a really good idea to do a normal shutdown if at all possible.

I hope that this sheds some light on the subject.

quadproc

Excellent!! Thanks quadproc.

---

### Post by LintonHanes on 2010-02-25
Hello Jack,
Welcome to the forums,

I'm curious about what sagas you've had with your lappy over the last few weeks?
...and are you dual-booting?

---

### Post by JackOfBlades on 2010-02-25
Well, thanks guys for your feedback, much appreciated. 
@Linton, nope, I'm not dual-booting, I don't like the idea.
And the saga behind my laptop is a long one, so hear one, hear all, for this is the history of my laptop (nice rhyme, huh?): A long time ago, I was content with Windows Vista Home Premium, it wasn't the next best thing, but meh, it was alright. I started to notice my laptop overheating and glitching, glitching like a N64 cartridge that was moved. The usage I gave it was like a normal desktop replacement, and yes, I know while my laptop IS NOT a desktop replacement, I thought it would be fine. I was wrong. I used to download games on uTorrent, days on end, never turning it off, only suspending it and once a week I turned it off. Well, one day, my laptop started to shut off by itself. And well, then it went to repair.
Repair... ha! Repair my balls, that's right. And so, it went, from hand to hand, to stupid techie to gold-digger techie, in search of much needed "repair". 
I decided to be drastic and searched for Ubuntu. I did tried to install the last version of Ubuntu, prior to 9.10, but using a LiveCD, to no avail. This week, I tried using a bootable USB with 9.10, and after a few tries, FINALLY, TODAY, hours before I went to this forums, it "worked", partially, but it did. Now it has no problems like before, only the ones I mentioned here. And probably, some others will pop out before I finally learn how to tame this wild and cute koala xD.

EDIT: I did the recovery thing, but it stops with the same message :S
What do I do now? Reboot using the LiveCD?

---

### Post by JackOfBlades on 2010-02-25
I don't mean to bump the thread. But, I need help. Went to the IRC Channel to no avail, there's no one there; everyone's idling.

EDIT: Tried the LiveCD thing, from a terminal there, just as it was written, but it did nothing.

---

### Post by mikeyphi on 2010-02-26
> **JackOfBlades said:**
> I don't mean to bump the thread. But, I need help. Went to the IRC Channel to no avail, there's no one there; everyone's idling.

EDIT: Tried the LiveCD thing, from a terminal there, just as it was written, but it did nothing.

I've lost it!!  Please start again with one problem, that you think is most serious. Give as much info as possible and we'll go from there.

---

### Post by JackOfBlades on 2010-02-26
Ok, I've got the same problem with the 

fsck from util-linux ng 2.16
/dev/sda1: clean, 131693/14712832 files, 1530674/58828014 blocks

thing that appears on screen. Even though I get in recovery mode it gives me that same message. Here's what I do:I turn on the laptop.
[LIST=1]
[*]The BIOS loads.
[*]The "GRUB Loading" appears.
[*]I press the ECS key.
[*]I choose the option that says "recovery mode".
[*]I watch a bunch of command lines appear and, well, as a manner of speaking, load.
[*]Then, it gives me that same message and it stops and it gets stuck.
[/LIST]
What should I do?

---

### Post by mikeyphi on 2010-02-26
Questions:
1. does it stick on that '/dev/sda1' message OR on a '>'

2. How long did it stick - before you took action?

3. How many partitions on your system? 

4. Tell us again - why you're using Recovery mode?

---

### Post by mikechant on 2010-02-26
Given you seem to be getting some rather erratic behaviour, it's worth running 'memtest' to check for bad RAM - it should be another option on the grub menu where you selected 'recovery mode'. It's not that it's a highly likely cause, but if it is the cause you could spend weeks chasing your tail looking at other things. It's probably best to set it going and leave it overnight.

---

### Post by JackOfBlades on 2010-02-26
> **mikeyphi said:**
> Questions:
1. does it stick on that '/dev/sda1' message OR on a '>'

2. How long did it stick - before you took action?

3. How many partitions on your system? 

4. Tell us again - why you're using Recovery mode?

1. No, it doesn't. It gets stuck in that message I spoke of earlier.
2. Um, you mean stuck? Well, a long time, probably more than ten minutes waiting to see if that damn "fsck" message would go away. 
3. Only one, with Ubuntu 9.10.
4. Because someone, specifically BrandonBan6 gave me that suggestion.

Again, thanks. But please, somebody tell me what to do, I'm not really that saavy using LINUX or Ubuntu and I researched on the internet and what to, and I ended with in the same place where I began. Have some mercy, please D:  [-o<

---

### Post by Mustard on 2010-02-26
Did you try the Memtest option from the grub menu?

Did it return errors?

---

### Post by JackOfBlades on 2010-02-26
I'll do the memtest thing before I go to sleep and I'll give you the reports first thing in the morning. Any other suggestions in the meantime?

---

### Post by LintonHanes on 2010-02-26
> I believe that graphics card would use the nvidia-glx-new. Have you tried the restricted drivers located under system, administration, Drivers manager?

your laptop: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01470147&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3753783](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01470147&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3753783)

seems to have a book written about it: [http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)

of note was: " to suspend proper, have a swap partition 'as big if not larger than your ram"

"but yoda, he may have to reinstall everything"

---

### Post by JackOfBlades on 2010-03-07
Well, after a fresh re-install I've got everything working right, for now. Thank you for your help, I really appreciated it.

SOLUTION: Re-installed Ubuntu 9.10

---


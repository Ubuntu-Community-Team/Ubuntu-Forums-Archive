---
title: "ubuntu starts but ..."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by emmwee on 2009-02-10
I created my installlation disk, I controlled everything (it should be perfect), and I was happy to try out finally Ubuntu! My laptop (Sony Vaio VGN-SR11M) executed the booting and everything seemed to go in the right way but ... when I thought that the desktop should display (I even heard the music) my monitor became black and the computer seemed to fall into an immediate sleep.
After 10 minutes or something like this I pressed the on/off-button: the computer "woke up", I pressed the backslace, the monitor showed me the Ubuntu logo e letters asking me to remove the disc, close the tray and press ENTER.
I tried it twice ...
What happened? What can I do?
I really want to enter definitely into the open source community ... Who can help me?

---

### Post by pytheas22 on 2009-02-10
According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615"), this is a known issue with your particular laptop model.  It's been fixed and simply applying Ubuntu updates should solve the problem, but obviously you need to be able to install Ubuntu before you can update it.

So what I'd recommend is that you download and burn the [alternate install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") for Ubuntu 8.10 (Intrepid), which uses a text-based installer that should work.  Use it to install Ubuntu.

After you've completed the installation, rebooted into Ubuntu and are at the black screen, press control-alt-F2.  This will bring you to a command prompt.  Log in there, then type these commands (make sure you're plugged into the Internet):
```

sudo ifconfig eth0 up
sudo dhclient eth0
sudo apt-get update
sudo apt-get upgrade
```

This will manually download and install all Ubuntu updates for you (it may take a while depending on the speed of your Internet connection).  When you're done, reboot the computer by typing 'sudo reboot', and in principle your problem should be fixed, allowing you to boot into the graphical desktop as normal.

Note that these instructions assume that you have a wired ethernet connection available.  If that's completely impossible for you, let me know and we can work around it...but it would much simpler just to connect using the wire for this process.

---

### Post by emmwee on 2009-02-11
> **pytheas22 said:**
>  [...] a known issue with your particular laptop model
That's what I feared to hear!
> **pytheas22 said:**
>  [...] simply applying Ubuntu updates should solve the problem 
"should" ... I'm quite courageous, but I have no idea about hardware and software ... even if I learn very quickly ;-) ... and everybody in my surroundings tells me not to change to Linux! So I have nobody here who would help me. But I'm obstinate, too.
> **pytheas22 said:**
>  [...] install Ubuntu before you can update it
That means I can't **try** it before, I have to install it definitively. So my questions (sorry for my ignorance):
1) Installing Ubuntu on my harddisk, Windows Vista disappears completely?
2) If I continue to have too many problemes with Linux, can I disinstall it without problems? And re-install Windows Vista (I created the ricovery disks, 3 DVDs, as recommended by Vaio)
3)Who helps me if I should have trouble and decide to go back to Windows????
[Yes, I feel very alone in this step, but knowing that there are so many people all around the world who share not only Ubuntu but also another kind of vision of the world is tranquilizing. By the way, I went to your personal homepage ...]

> **pytheas22 said:**
>  make sure you're plugged into the Internet
Am I plugged to the internet if the internet connection wire (ADSL) is "put" (excuse my English, too) into the laptop?

I'm waitung for your answer, if you encourage me I will go on.
At any rate thanks for your helpfullness.

---

### Post by mkvnmtr on 2009-02-11
It sounds like you will be best served by a dual boot system. That way you should not loose your windows system but just add a Ubuntu system. The advise of the other poster on how to get an install is very good. First you should back up your windows install on another hard drive. It is very rare to lose anything except through user error but we all do silly stuff sometimes. Then I would make the windows partition smaller to give you space to put Ubuntu. Vista has tools to do this. In your case it is probably best to do this before you boot the Ubuntu disk even though you can do it from the disk. As an example about 10Gb is good for the Ubuntu system. Your home can take up a lot more space but on your first install the total you need is about 15GB. Size your windows to leave you about 15GB of free space. Then procceed with th install otlined by the other poster. If at anytime you are not sure about something you can back off and come to the forums to ask questions. When you get to the partition step if you have lest free space it will be easier for a first time installer to choose to install in the largest free space. That way th disk will form the partitions you need for root and swap with out touching your windows. Good luck and enjoy Ubuntu

---

### Post by pytheas22 on 2009-02-11
> Installing Ubuntu on my harddisk, Windows Vista disappears completely?

No, you can easily have both operating systems installed at the same time, and choose which one to use when you turn on your computer.
> 
If I continue to have too many problemes with Linux, can I disinstall it without problems? And re-install Windows Vista (I created the ricovery disks, 3 DVDs, as recommended by Vaio)

Of course, you can remove Ubuntu and reinstall Vista anytime.
> 
Who helps me if I should have trouble and decide to go back to Windows????

There are always thousands of people on this website who will help you if you have trouble.
> 
Am I plugged to the internet if the internet connection wire (ADSL) is "put" (excuse my English, too) into the laptop?

Yes, that should be sufficient to get connected, I think.

You may also want to consider installing Ubuntu using [wubi]("http://wubi-installer.org/") rather than the CD.  wubi allows you to install Ubuntu from inside Windows in a few clicks, doesn't require partitioning and makes it very easy to remove Ubuntu later if you choose--you just use 'Add/Remove Programs' in Windows.

If you use wubi, you will probably have the same problem with the black screen when you first boot to Ubuntu.  But the same instructions will apply: press control-alt-F2 to get to a command line and run those commands from my last post, then reboot.

You can still use the alternate CD if you like, but I'd recommend wubi given the concerns you express.  So if you're willing, please give it a try, follow the instructions for fixing the black-screen problem, and we'll take it from there.

---

### Post by emmwee on 2009-02-12
Thanks for helping me. Ubuntu works, I tried all I had to try. So I feel confirmed that it was the right choice to live with Ubuntu (and Open Source in general) and say goodbye to Bill Gates & Co.!

Now, thanks to Wubi, I can switch back to Windows if necessary (there is f. e. a CD that does not work with Linux).

My last important questions: Now I have to migrate all my stuff from my old laptop (XP) to the new one. The best solution is, I suppose, to send everything to Ubuntu (and not to Windows), isn't it???

But: On Ubuntu I've 9,6 GB free place, while my XP "documents - administrator" seem to be 22,5 GB! Switching to Vista, Vista tells me that on the local disk there are 181 GB disponible (from 223 GB).

Before migrating I would prefer to create the optimal situation for working without bad surprises. What should I do now?

---

### Post by pytheas22 on 2009-02-12
Good to hear that you got Ubuntu up and running.
> 
My last important questions: Now I have to migrate all my stuff from my old laptop (XP) to the new one. The best solution is, I suppose, to send everything to Ubuntu (and not to Windows), isn't it???

If Ubuntu has only 9.6 gigabytes free, your best option would probably be to move your files to somewhere under the Windows system, then mount your Windows drive under Ubuntu when you need access to those files.

From Ubuntu, you can access your Windows files by opening a file browser (go to Places>Home Folder for instance to open a file browser of your home folder) and navigating to the location '/host'.  This is equivalent to C:\ in Windows, and from there you can find your files in order to access them in Ubuntu.

Let me know if this doesn't work or doesn't make sense.

---

### Post by emmwee on 2009-02-12
And what about disinstalling Ubuntu and than re-installing it. I remembered that Wubi asked me how much place to ask for Ubuntu. I left the default value (15), but maybe I had to say 30?

At the other side, maybe the easiest way is to migrate "heavy" stuff like photos and word docs to Vista and "light" stuff like my emails to Ubuntu?

---

### Post by kanikilu on 2009-02-12
Generally speaking, Ubuntu can read Vista partitions (NTFS), but not the other way around (not easily anyways). In other words, it would be easier to access files on the Vista partition from Ubuntu, rather than accessing files on the Ubuntu partition from Vista.

Another option is creating a common partition that both operating systems can read. I think most people use FAT32 as the format in that kind of setup.

---

### Post by emmwee on 2009-02-12
I looked around the forum to find out how to have access to files from Ubuntu to Vista. And I begin to understand that I should begin to learn about ... partitions (the word that let me be afraid of Linux). K. says:
*[INDENT]"Another option is creating a common partition that both operating systems can read. I think most people use FAT32 as the format in that kind of setup."[/INDENT]*

Can somebody tell me where I can find a clear instruction how I can "divide" my harddisk (?) into partitions. Actually my Vista and my Ubuntu are still virgin; all my files are still on my old laptop.

---

### Post by pytheas22 on 2009-02-12
> I looked around the forum to find out how to have access to files from Ubuntu to Vista. And I begin to understand that I should begin to learn about ... partitions (the word that let me be afraid of Linux). K. says:

    "Another option is creating a common partition that both operating systems can read. I think most people use FAT32 as the format in that kind of setup."



Can somebody tell me where I can find a clear instruction how I can "divide" my harddisk (?) into partitions. Actually my Vista and my Ubuntu are still virgin; all my files are still on my old laptop.

kanikilu is correct in saying that some people create a FAT32 partition to share between Linux and Windows, but in your case (and in most situations today) I really don't think that's necessary.  The FAT32 approach was popular back when Linux couldn't read NTFS well, but since about 2006 that situation has changed.  So there's no good reason to create a new partition on your hard drive, which would involve a lot of time and risk.

I really think that the best strategy for you is just to copy all of your files to Windows, and mount the Windows partition under Ubuntu if you need to access them.  Copying some files to Ubuntu and some to Windows would also work, but it's more complicated; in addition, accessing Ubuntu from inside Windows is not as easy as vice-versa (although it can be done if you install the [ext3 drivers for Windows]("http://www.fs-driver.org/")).

You can reinstall Ubuntu again and tell wubi to create a larger disk image if you want, but again, I don't think there's a good reason to do this; what you have is fine, and copying all your files to Windows is definitely what I would do if I were you.

If for some reason you *really* want to create a FAT32 partition, however, I'll find instructions.

---

### Post by emmwee on 2009-02-13
I feel desperate! I'm not able to find the way to see (and work with) my files under Vista. I fear something went wrong. How should it be NORMALLY (Under Resources I should find Media or something like this with my Vista files?? There is only Recovery , after I installed NTFS Configuration.)

---

### Post by pytheas22 on 2009-02-13
I'm not sure what you mean (I've also never used Vista).  Are you unable to boot to Vista?  Or can you boot to Vista but can't find the files that you copied there from your laptop?  Where exactly did you copy the files to in Vista (i.e., what is the path?  C:\...?)?

---


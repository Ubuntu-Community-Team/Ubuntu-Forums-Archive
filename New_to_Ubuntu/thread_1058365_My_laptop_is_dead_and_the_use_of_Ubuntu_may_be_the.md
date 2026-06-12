---
title: "My laptop is dead and the use of Ubuntu may be the solution!!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by slater_21 on 2009-02-02
Hello everyone!

So I have a difficult situation and I really need help. As I said on the title my laptop ACER Aspire 1644 wlmi has problems on turning on. Everytime I turn it on, first I see the background of the Acer Company and then I receive 5 options: Security mode, Security mode with net, Security mode on DOS, Last right configuration and Start windows normally. In every tried options after the windows Xp background appears a live blue screen with white letters saying something like "Fatal error and for security the windows will restart.." This screen only appears for 1 second and the laptop restarts..After restarting the same 5 options appear and then the same situation happen and appear the live blue screen.
So my idea to solve this problem was to format the disc..So I tried to enter on the BIOS and put the starting of the laptop from the CD..Then I put a CD of the windows Xp in the laptop, then appeared the sentence "click some button to start from the CD.." what I did..then appear the sentence saying that the laptop hardware was being checked..and then the laptop restarts again..:S
I entered in another forum to find some help to solve this problem and someone told me to use Ubuntu..I don't know what it is or how to use it..So I have 2 questions:

Can Ubuntu be a possible solution to format my laptop and after that install windows XP again?
How do I use Ubuntu to format the disc (My laptop has two discs..C and D..and if it is possible I would like to erase the data of only one of the discs..but of course I prefer to have laptop than not having one..lol so if I need to erase everything..let it be..)

Best Regards and thanks,
André

---

### Post by shifty_powers on 2009-02-02
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

will be easier for your purposes...

---

### Post by yeats on 2009-02-02
No - while I recommend Ubuntu as an alternative for Windows in general, it's not the solution to your particular need.  If your final goal is a reinstallation of Windows XP, you should see if there are Windows forums on the web that can advise you.

If, on the other hand, you'd like to try Ubuntu on its own merits, then that's an entirely different situation and there are MANY of us here willing to help you get started. :-)

---

### Post by cariboo on 2009-02-02
IF it won't start using the Windows boot CD, trying the Ubuntu LiveCD isn't going to fix your problem. It appears you have a hardware problem, I suspect you have a bad hard drive. They are pretty easy to change, there is usually a cover on the bottom with 2 screws in it. Take the cover off and you may have to take out a couple more screws. You will have to slide the hard towards the side to disconnect it. Once you have the drive out, you can get a replacement, reisntall you OSs and you're good to go.

Jim

---

### Post by mkvnmtr on 2009-02-02
The Ubuntu live disk has a tool called Gparted installed that can partition you disk. But like the other poster said there is a Gparted live disk that can do the same thing and it is a much smaller download. Google the live disk page and you will find a number of live rescue disks including Gparted. I recently bought a old acer laptop to have a second system if something happens to my primary. The xp windows  os was very slow so I installed a couple of Ubuntu distros on it. 8.10 and 9.04.  They are both much faster than windows and all the hardware worked out of the box. If you wish to install a better and faster os for your acer there are a lot of people here that will help you do it. If you wish to reinstall windows get the Gparted download and burn it to a disk and get somebody with a little windows experience to help.

---

### Post by slater_21 on 2009-02-02
> **chrissharp123 said:**
> No - while I recommend Ubuntu as an alternative for Windows in general, it's not the solution to your particular need.  If your final goal is a reinstallation of Windows XP, you should see if there are Windows forums on the web that can advise you.

If, on the other hand, you'd like to try Ubuntu on its own merits, then that's an entirely different situation and there are MANY of us here willing to help you get started. :-)

Lol but Ubuntu is a new operating system?
Believe me I don't know what it is..otherwise I wouldn't say that..It's the same like going to a Manchester United fan site ask where can I buy a Chelsea or Liverpool jersey..lol

I'm a very curious person and so of course I would like to try Ubuntu as operating system..but offcourse that first I have to recover my laptop and before your answer I thought Ubuntu was more like a program to fix..and not a rival of windows xp..so if you know a way to use Ubuntu to fix my laptop please tell me..

---

### Post by yeats on 2009-02-02
> Lol but Ubuntu is a new operating system?

Yes, that's right - you can run Ubuntu on pretty much any computer you want and use it for the same sorts of things you use Windows for.  HOWEVER, you will certainly want to do some research into this before proceeding (which, again, many of us here are willing to help you do).  It sounds like you've got some pressing issues to solve first. :-)

I agree with cariboo, though - sounds like you might have a hard drive problem, in which case you'll need some working hardware first.  Follow the advice you've got here - try Gparted.  We'll help you with it if we can.

---

### Post by slater_21 on 2009-02-02
I made the download of this file gparted-live-0.4.1-2.rar I open the rar file and there are many files in it.. I suppose that if I burn the rar file to a CD and put it in my laptop it won't run right? Normally in other programs I see a .exe that will run automatically when the cd is insert..So can you please tell me how to burn the gparted to become ready to work on the laptop when I put my laptop running from the CD? One other thing..I never format using gparted..the instructions are easy to follow?
If this don't work I will then try to change the hardrive..but first I wanted to see if I can recover it..

---

### Post by Bradtek on 2009-02-02
Looks like you have downloaded the wrong file to make a Live CD

Download gparted-live-0.4.1-2.iso   
from here [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Then using your usual burning program burn it as a CD Image
DO NOT burn it as a data CD
Always a good idea to burn at a slow spped to ensure a good burn.

---

### Post by lkraemer on 2009-02-03
André,
If you have already decided to blow away the first partition,
I must assume that you have a backup of the important files
you will be needing from that partition.  If not, why not
try booting the Ubuntu LiveCD on your machine, and see if you can
access that XP drive to copy your important files to DVD or another
external USB drive.  Then, you could give "testdisk" a try to
see if it could fix the problem with your drive.  But, this all
is going  to take a bit of time.  Most likely the easiest thing
to do is to purchase a new drive, install it, and then start the
Windows (YUK!) install process.   

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

(Don't forget to copy your FAVORITES, and all your Downloads, Documents,
Important Data files along with any registration information you may 
have saved for installing the software again.)  WHEW! in just a few days
you will be ready to surf!

And if you purchase a slightly larger Drive (160 or 250 Gig), and want to
install Ubuntu as a Dual Boot system have a look here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You will probably need this too!
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

On your new Drive, make 4 Partitions (MAX of 4 Primary Partitions)
using Gparted on the LiveCD.
Example:
~50 Gig XP (or Windows can do this also)
~10 Gig Recover Partition (or Windows can do this also)
~45 Gig Ubuntu (Root Partition /)
~5 Gig Linux Swap (~>2 times RAM)

Install or restore XP first.  This will make your first two partitions.
Then copy your saved data and files that you recovered.  Now,
get to the good stuff and install Ubuntu.  (I prefer 8.04.2 LTS)  After
using Ubuntu for a year, you won't ever look back.

Good luck on your adventure.

Don't forget that you can boot from the LiveCD and use Ubuntu to surf
and do what you need while you are resting and gathering the necessary
items to continue rebuilding XP.

lkraemer

---


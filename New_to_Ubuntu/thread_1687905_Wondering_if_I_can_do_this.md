---
title: "Wondering if I can do this"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by homefire on 2011-02-14
I'm not a techie, but have been intrigued by trying a non-Windows system for quite awhile. Today I tried to reformat an old XP system only to find that the original Windows discs have a couple of files corrupted, so I'm thinking of trying Ubuntu on the system instead.
 
The question is, Can I? It's OLD. It's a 1.8GHz Pentium 4 processor with an 80 MB hard drive, but it only has 256K of RAM.
 
I've found some conflicting info on whether it will run on that, so I decided to ask here for input. What do you think?
 
Also, reading up on it a bit, I'm finding that some people have trouble working with Ubuntu. Our kids use this machine mostly for Internet access, so it wouldn't need to have many programs on it, but we do want to be able to stream video, play games, etc. Possible?

---

### Post by TeoBigusGeekus on 2011-02-14
256k? Did you mean 256mbs?

---

### Post by sanderd17 on 2011-02-14
You don't have enough RAM for Ubuntu, but lighter ubuntu variants like Lubuntu will work quite smooth.

About the video: it will play video, but don't expect great things from such hardware. Same for the games. Card and bord games will run without a problem, but don't try to play a 3D game.

---

### Post by JOHNNYG713 on 2011-02-14
If it ran xp it will run Ubuntu ! (Or should) I have an old IBM 600X 10 gig HD 512 RAM amd a coppermine P3 CPU and it runs every thing but compiz-fuzion descktop effects ! :D

---

### Post by matt_symes on 2011-02-14
Hi

> It's OLD. It's a 1.8GHz Pentium 4 processor with an 80 MB hard drive, but it only has 256K of RAM

You don't have much ram. If you want to run Ubuntu or Kubuntu i would invest in more.

However, there are plenty of other distro's that will run with that amount of ram. If you are interested in a *buntu distro take a look at xubuntu or even lubuntu(They are both light weight).

Or take a look at DSL, slax or puppy linux. They will run fine on that machine.

> but we do want to be able to stream video, play games

For those (apart from the most basic games) i would recommend more ram again.

80G hard drive, 256M ram ?

Kind regards

---

### Post by lisati on 2011-02-14
A bit more ram probably wouldn't hurt. Other than that, I see no problems.

You might want to consider looking at one of the "lightweight" flavours of Ubuntu, such as [Xubuntu]("http://www.xubuntu.org/") and [Lubuntu]("http://lubuntu.net/").

---

### Post by Nytram on 2011-02-14
There's a version of Ubuntu called Lubuntu which should work ok with that machine, or you might want to try Puppy Linux which is also designed for older hardware.

---

### Post by CharlesA on 2011-02-14
I'm pretty sure it doesn't have an 80MB hard drive, probably 80GB with 256MB of RAM.

Should be able to run Lubuntu.

---

### Post by homefire on 2011-02-14
**Laughing***  Okay, I am officially out to lunch!  I guess I will plead that I wrote that quickly while in the midst of a massive headache.  Anyway, yes, it's all wrong.  Yes, it's 256M of RAM and an 80G hard drive.  Totally losing my mind!
 
I'm impressed with all the activity on here!  Quite a happenin' place.
 
So I see several recommendations for Lubuntu.  I'm assuming that the only difference is that it wouldn't run heavy-duty programs?  And video and simple internet-based games should be okay?  They don't do any 3d games, I'm pretty sure.
 
If I can get by with that, I'm going to be very happy!  
 
Since I have no operating system installed right now, will I be able to do the CD trial thing okay by booting from the disc?

---

### Post by CharlesA on 2011-02-14
It comes as a LiveCD, so you can try it out without installing if you desire.

It's "lighter" in that it requires less memory and hard drive space to run.

Check it out here: [http://lubuntu.net/](http://lubuntu.net/)

---

### Post by homefire on 2011-02-14
Thanks!  I'm downloading it right now, so we'll see.

---

### Post by matt_symes on 2011-02-14
Hi

Remember, it will run quite a bit slower from a LiveCD than if it was installed on the hard drive so you will not get an accurate measure of its speed when fully and finally installed.

You will get to see the look and feel of the OS though.

Kind regards

---

### Post by homefire on 2011-02-14
Another question.  About getting more RAM...  How can I go about that?  It has two slots, which each contain 128MB.  So what would I have to buy?

---

### Post by matt_symes on 2011-02-14
Hi

Ebay ? Get the hardware specification from the net to see the exact type of ram required and to see what your motherboard specs are.

Kind regards

---

### Post by homefire on 2011-02-14
I know that what's in there is RDRAM, and the cheapest price I can find on 512 MB is about $100.  I'm really wondering whether it's worth it to spend that on this old thing.  
 
Also, how do I tell whether the motherboard will support that much?

---

### Post by matt_symes on 2011-02-14
Hi

> Also, how do I tell whether the motherboard will support that much?

You would need the motherboard specs. I would suggest Lubuntu for this PC. With those specs it will never be a power house but should be fine for surfing the net, e-mail, writing documents and the kids homework. Better than taking it down the dump because it will not run commercial operating systems.

I live in Britian so i'm not sure of RAM prices in the US but $100 seems expensive. Keep shopping about. The more RAM you put in the better. If you are going to keep it at 256 ram create a generous swap partition.

Kind regards

---

### Post by homefire on 2011-02-14
> **matt_symes said:**
> Hi
 
 
 
You would need the motherboard specs. I would suggest Lubuntu for this PC. With those specs it will never be a power house but should be fine for surfing the net, e-mail, writing documents and the kids homework. Better than taking it down the dump because it will not run commercial operating systems.
 
I live in Britian so i'm not sure of RAM prices in the US but $100 seems expensive. Keep shopping about. The more RAM you put in the better. If you are going to keep it at 256 ram create a generous swap partition.
 
Kind regards
 
Where do I get motherboard specs?  I have the original invoice, but all it says is Pentium 4 processor and motherboard.
 
How do I "create a generous swap partition?"

---

### Post by jroa on 2011-02-14
If you can boot with the liveCD, then open a terminal and run the following command.

```
sudo lshw |less
```This make take a little while to run.  When it is done, it will list everything about your computer one page at a time.  The first thing that should be listed is the mother board information.  Once you get that, hit the q key to stop the program or if you want to, you can use the space bar or up/down arrows to look at all of the information.

Edit to say that I should have explained the commands that I told you to use.  "sudo" will give you temporary root access.  "lshw" is the command to list the hardware configuration.  "|" (pipe or vertical bar above the enter key) tells it to input the results into another command or program, which in this case is a program called "less", which allows the information to be displayed one page at a time.  You can run without |less, but you will get a whole lot of information when all you really need is the first bit of it.

---

### Post by Irihapeti on 2011-02-15
For what it's worth, I had an old Toshiba laptop with 256MB of ram and a 30GB hard drive. At different times, it ran Xubuntu and Lubuntu OK, thought it was sometimes a little slow to load some programs.

If you have no operating system installed, you have nothing to lose by trying an installation and seeing how it goes. If it doesn't work, you can always try something else.

---

### Post by matt_symes on 2011-02-15
Hi

@Irihapeti. How well did it run Lubuntu ? That's one of the great things about Linux. It can breath life into older PC's. I have an old server that is overclocked to 1GHz :p

Kind regards

---

### Post by Irihapeti on 2011-02-15
> **matt_symes said:**
> Hi

@Irihapeti. How well did it run Lubuntu ? That's one of the great things about Linux. It can breath life into older PC's. I have an old server that is overclocked to 1GHz :p

Kind regards

As I recall, it ran pretty well. There were a few bugs in Lubuntu at the time (we are talking about the time Lucid was the current "development release"), and I ended up doing an Openbox custom install. That was quite impressive with its memory use. If it weren't for the fact that it would probably confuse the OP at this stage, I'd recommend something like Openbox on his/her machine.

---

### Post by homefire on 2011-02-15
I can't get it to boot with the CD. I tried to install Windows XP yesterday and there were a couple of corrupted files, so now it just boots to Windows, up to a certain point, where it stops and asks for those files, then reboots...again and again. I've tried hitting all the F buttons during bootup, but it doesn't give me the option of booting to the CD, so evidently I need to get rid of that partially-installed Windows. How do I do that?

---

### Post by sanderd17 on 2011-02-15
Try the alternate installer. That doesn't require the amount of ram like a live cd does.

---

### Post by homefire on 2011-02-15
I'm wondering if I just have a bad CD, because it seems like it's not even recognizing that it's there.

---

### Post by cascade9 on 2011-02-15
> **homefire said:**
> I know that what's in there is RDRAM, and the cheapest price I can find on 512 MB is about $100.  I'm really wondering whether it's worth it to spend that on this old thing.  
 
Also, how do I tell whether the motherboard will support that much?

RDRAM? Dont bother. Besides beign stupidly expensive and not easy to get, there are 2 major variants to RDRAM- PC600/8001066 and the extra rare, super hard to find RIMM 3200/4200/4800/6200. PC600/800/1066 needs to be installed in pairs, and 'empty' RAM slots need to be filled with terminatiors. RIMM 3200/4200/4800/6200 is single stick (and I cant reven recall if the empty RAM slots on RIM needed to be filled with terminators). 

Really no fun at all, even for techies. 

Add into that the old 1.8GHz P4s are hardly speed demons even with a ton of RAM. So dont bother, save your money for a newer, better computer. I've seen nice dual core S939s and early Core2Duos go for similar amount to just a RAM upgrade with RDRAM....

BTW, if its a P4 using RDRAM its got to be a 850/850E chipset, they go to 2GB.

---

### Post by homefire on 2011-02-15
How do I do that?  (alternate installer?)

---

### Post by homefire on 2011-02-15
Thanks for the info, Cascade.  I wasn't really considering spending money on it anyway, but that's good to know.  Dh says pitch it :) but I would really like to try ubuntu if I can!

---

### Post by sanderd17 on 2011-02-15
> **homefire said:**
> I'm wondering if I just have a bad CD, because it seems like it's not even recognizing that it's there.

If it isn't reconized, that it is probably a bad CD (or a bad CD reader). When you don't have enough RAM, the CD would take days to boot (normally it only takes certainly less then 15 min on old hardware)

---

### Post by homefire on 2011-02-15
So I just need to download it to a new CD and try again?  sigh.

---

### Post by cascade9 on 2011-02-15
> **homefire said:**
> I can't get it to boot with the CD. I tried to install Windows XP yesterday and there were a couple of corrupted files, so now it just boots to Windows, up to a certain point, where it stops and asks for those files, then reboots...again and again. I've tried hitting all the F buttons during bootup, but it doesn't give me the option of booting to the CD, so evidently I need to get rid of that partially-installed Windows. How do I do that?

You might have a HDD or CD problem. Sorry. 

If you are set to boot from CD, and use the WinXP disc you should be able to repair the XP installation. I'd give it a try, if it fails, try a clean reinstall of XP. 

BTW, I always use a torrent client to d/l linux .isos. Besides being faster in most cases (apart from when I can get a .iso that for a local mirror) you can always just use the 'force recheck' option to make sure that you've got a good copy.

---

### Post by homefire on 2011-02-15
Hmph.  I just pulled the file out of my temporary burn folder onto a new CD and it still doesn't work.  What do you think?

---

### Post by sanderd17 on 2011-02-15
> **homefire said:**
> Hmph.  I just pulled the file out of my temporary burn folder onto a new CD and it still doesn't work.  What do you think?

check md5 sum?

---

### Post by homefire on 2011-02-15
Um, newbie here, cascade!  That last paragraph is not in my language.  ;)
 
I've tried a zillion or so times on the Windows install, but the disc has a couple corrupted files.  AND it's the first time it's been out of the package.  Grr.  We're going to try to find another XP disc in order to repair it.

---

### Post by homefire on 2011-02-15
Oh, you guys!  This is a wonderfully helpful forum, but I don't know the lingo!
 
"check md5 sum?"  Whazzat mean?

---

### Post by lol768 on 2011-02-15
The Ubuntu downlaod site provides md5 sums with each download. These are 128 bit "hashes" that can be used to check if the file is corrupt, damaged or somehow altered from the original. They are usually represented as a series of 32 hexadecimal digits, so they can be represented as "ascii text".

Here's an example from wikipedia:
 MD5("[The quick brown fox jumps over the lazy dog]("http://en.wikipedia.org/wiki/The_quick_brown_fox_jumps_over_the_lazy_dog")")   = 9e107d9d372bb6826bd81d3542a419d6 

Every file usually calculates to a unique md5 hash.

Most Linux distros comes with a command (md5sum) for calculating the md5 hash of a file. On windows you can try [http://www.toast442.org/md5/](http://www.toast442.org/md5/) which gives you a graphical user interface to calculate md5 hashes.

See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) to find out the md5 hash for your distro.

---

### Post by cascade9 on 2011-02-15
> **homefire said:**
> Um, newbie here, cascade!  That last paragraph is not in my language.  ;)

Opps. 

You can d/l ubuntu via FTP (the 'normal' way people get it) or you can d/l a torrent. You need a torrent client to use the torrent protocol (transmissuion, delgue, a ton of others with linux, utorrent is probably the most popular for windows). 

Torrents dont d/l from one location like FTP does, you are actually d/ling from everybody who has the file and is running a torrent client. 

Its nicer for the linux distros, as they dont have to pay for all the bandwidth, the users do. Its also good because you can check if the file is right, or if it has any corruption ('force recheck'). If any part of the file is correupted, the torrent client can just d/l the bad part. 

MD5sum is a way of checking the files are correct as well. If you got the file via FTP, then if there is an error you have to re d/l the whole file. 

To check the MD5sum, you need a program to do that as well. Almost all linux distros will let you do it from a command line, or there are GUIs to do it as well. 

Personally, I find that torrenting is much easier, if only because checking MD5sums is boring, and the torrent client does it all in the background. No need to boot a different program, or use commands to check for correuption.

---

### Post by homefire on 2011-02-15
mm-hmm.  Clear as mud.  :)  Don't think I'll try that--sounds labor intensive.  I'll just hope that I can find a way to finish the XP installation and try again.

---

### Post by jroa on 2011-02-17
Just reburn the install CD at the lowest speed.  I have never had a problem doing it this way.  Then, boot the disk, or in other words, restart you computer with the disk in a drive.  If all goes well, you should see some Ubuntu information.  If not, then your disk or ISO is bad or we need to change some of your conguratuons.

When you do finally get to intall options, choose the options that will let you "try the OS", or it5 will say something simialr.

---

### Post by homefire on 2011-02-17
I have tried it with three different CDs now, and each one has the same result. When I boot the machine with the disc in, it totally ignores it. With the Windows disc in, it always asks if I want to boot to the CD, but with the Lubuntu disc, it just ignores it--never recognizes that it's there. The last one I tried was an old 4x Cd-RW, and it didn't work either.
 
And it's caught in this endless loop of the XP installation. Since it wasn't able to copy a couple files, it retries over and over...checks for the files, and when it doesn't find them, it restarts, over and over and over. 
 
So I thought I would just reformat again, but I don't even know how to get to the DOS prompt. I have tried hitting everything I can think of after I turn it on, during bootup, but can't get there. I can get it stop at the BIOS setup, but don't know what to do from there.Help please?

---

### Post by eriktheblu on 2011-02-17
If it's not even booting, but the Windows disk does, that sounds to me more like an improper burn than a corrupted image. I've downloaded several Ubuntu ISOs over the past few years and not once encountered a corrupted file.

If you insert the disk in a running machine and open it, do you see 1 file (ubuntusomethingorother.iso) or several?

Windows in my experience does not make it easy or straightforward to properly burn ISOs. Many Windows users have instead burned ISO files on to data disks. If this is the case, it will not boot.

Check out [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and pay close attention to step 2.

---

### Post by JKyleOKC on 2011-02-17
I agree with the "improper burn" idea. There are two different methods of burning CDs/DVDs: the usual method simply copies the individual files onto the disk, while the other way copies the content of the named image file rather than the image file itself. I know that doesn't make a lot of sense -- the second way, usually called "burn image," simply makes a bit-for-bit copy of what is **IN** the image file onto the CD, while the first way copies the image file itself. 

It sounds like you've used the usual method; if you can list the content of the CD using another machine, and find just a single file on it, that's pretty good evidence that this is your problem.

Look for the "burn image" option in your burner program, and use the slowest possible recording speed, and you should be in good shape with CD number 4.

---

### Post by 3177 on 2011-02-17
one word: Xubuntu.
Though Im not sure if its "that" light.

---

### Post by homefire on 2011-02-17
There's one ISO file on it called lubuntu-10.10 and that's all.
 
Checking out the link...

---

### Post by JKyleOKC on 2011-02-17
I run Xubuntu in a box with only 256 MB of RAM and a rather slow Athlon CPU, and while it's painfully slow (in comparison with my other boxes) it's quite usable.

For some 14 years, I ran an ancient version of Mandrake on a 1995-model box using a Pentium II, with 80 GB of disk and only 80 MB of RAM. It finally bit the dust when its power switch shorted out one morning. To do that, I had to replace its window manager with IceWM to hold down the resource load. The main differences between the various flavors of *buntu are the window managers; Xubuntu uses XFCE and Lubuntu uses LXDE. Both are significantly lighter than the Gnome or KDE environments found in the mainstream flavors; I like the XFCE feel better but LXDE is said to be the lightest...

---

### Post by CharlesA on 2011-02-17
> **homefire said:**
> There's one ISO file on it called lubuntu-10.10 and that's all.
 
Checking out the link...
So the ISO is on the cd?

See here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by homefire on 2011-02-17
The ISO *_was _*on the CD.  I just erased it to try again.  
 
So I've been reading the Burning ISO how-to, which I confess I totally ignored before.  I downloaded and installed Infra Recorder, but I have a (probably dumb) question.  On step 4, it says "Select the Ubuntu CD image file you want to use, then click 'Open'. "  
 
Select it from where?  The download page?  And it will automatically use Infra Recorder?

---

### Post by CharlesA on 2011-02-17
You would select it from whereever you downloaded it to.

---

### Post by homefire on 2011-02-17
I burned it straight to the disc.  Just checked the Temporary Burn folder and it's not there anymore.  So I guess I need download again.

---

### Post by JKyleOKC on 2011-02-17
Right. Download it to the hard disk, then burn it from there.

---

### Post by homefire on 2011-02-17
That worked!! But how long should the install take? It's been sitting there with a blue swoop across the screen and a little clock in the middle for ages.  And light on the drive isn't flashing.

---

### Post by homefire on 2011-02-17
Okay, it's been well over an hour now.  Obviously it hung up.  What do I do now?  Getting very frustrated!

---

### Post by homefire on 2011-02-17
Rebooted, hit Check Disc for Errors, it said there were none.  Tried to run it from the disc, and it did seem to load, but was so slow that it was agonizing.  Now I've clicked the icon to install it and I'm waiting...

---

### Post by COMPUTIAC on 2011-02-17
Hello, go to crucial.com and use the memory advisor. Very easy and will give all spec's and prices.

[http://www.crucial.com/index.aspx](http://www.crucial.com/index.aspx)

COMPUTIAC

---

### Post by homefire on 2011-02-17
I've already been there and it would cost way too much to upgrade.  So you're saying that all the problems I'm having just mean that I don't have enough memory to put Lubuntu on this machine?  Seems really weird that it ran XP just fine, but won't run this supposed "lightweight!"

---

### Post by COMPUTIAC on 2011-02-17
If I were you I would run from the Live CD first to see how it is. Then you can install as a dual boot or just do a full install of just Ubuntu.

As you say, if it ran XP I don't see why it won't run Ubuntu.

---

### Post by homefire on 2011-02-17
Evidently you haven't read the whole thread, Computiac.  Been through it all.  It won't install.  Again.

---

### Post by eriktheblu on 2011-02-18
If you're short on memory, try creating a swap partition before you install.

From the live CD, go to system>administration>GParted

Assuming you have a large partition on the right side of the graphic, right click and resize. Reduce it by ~512 MB, then right click the empty space and create a new swap (under File system). 

I've found this to make installation go better on lower spec machines. 

Now for your specs, I would Lubuntu as others suggested. Full Ubuntu is designed for a pleasant computing experience rather than efficiency; it can eat up a lot of RAM. Lubuntu is significantly less resource intensive.

Ubuntu recommends 1 GB of memory where Lubuntu ought to be fine with 256 MB.

---

### Post by homefire on 2011-02-18
My System folder doesn't have Administration in it. And everything is so agonizingly slow running from the disc that it is severely testing my patience. I click, then wait for a minute and a half to find out whether I'm where I want to be. Not exaggerating. Maybe I'd better give this up.  But I really don't want to.  Stubborn, I guess.  :)
 
And now my toolbar is gone.  Humbug.

---

### Post by Vaphell on 2011-02-18
so you run livecd successfully? yes, running the system from cd is painfully slow, especially on low speed CD drive/low ram machine. Native installation to hdd is 10x faster.
Someone in this thread mentioned alternative CD, it's a good to install without the bloat of full desktop environment with all the bells and whistles. User interface of alternate CD installer is text based so it's much much lighter and faster as it doesn't waste CPU cycles and RAM on useless bling.

---

### Post by eriktheblu on 2011-02-18
> **homefire said:**
> My System folder doesn't have Administration in it.
You can also get there by hitting Alt + F2, then type the following in the window that pops up.
```
gksudo gparted
```

> And everything is so agonizingly slow running from the disc that it is severely testing my patience.
Lubuntu and that swap partition will make a world of difference I assure you.

---

### Post by homefire on 2011-02-18
I have LOTS of questions, and you guys are being great to answer them!  :)
 
Running a memory test and noticed that something called ECC is disabled. Should it be? If not, how do I enable it?
 
Also when I got up this morning, there was a cute little fiber optic screen saver running. Surely the screen saver takes memory, right? so how do I turn it off?
 
Also is there an escape button? Like in Windows CTRL/ALT/DEL? Because I had opened a solitaire game last night and when I got up the icons in the games window had disappeared and there didn't seem any way to close the solitaire window. Had to reboot.
 
During bootup, there is a very tiny message that comes up at the top of the screen that says something failed due to unknown user ID.  What is that?

---

### Post by homefire on 2011-02-18
> **eriktheblu said:**
> You can also get there by hitting Alt + F2, then type the following in the window that pops up.
```
gksudo gparted
```
 
 
Lubuntu and that swap partition will make a world of difference I assure you.
 
I did that and typed in the code, but nothing has happened after a couple minutes.  The light on the DVD drive is not flashing.  Nothing.

---

### Post by homefire on 2011-02-18
I've been thinking about this, and I'm seeing a pattern.  
 
Tried to install XP, and it couldn't complete, so that install is partially on.
Tried to install Lubuntu and it stalled out--also stalled out, so that stopped in the middle, too.
Tried to run Lubuntu from CD, and it sort of works, but is so slow that long minutes go by while I wait to see if anything happens from a click.
 
So what I'm wondering is...maybe I should reformat the hard drive again?  Get rid of these partial installs, which could possibly be balling things up?

---

### Post by matt_symes on 2011-02-18
Hi

> So what I'm wondering is...maybe I should reformat the hard drive again? Get rid of these partial installs, which could possibly be balling things up?

Unlightly i think but it might be worth a go. I would suggest it's an issue with memory though (but without the PC in front of me it's always a guessing game).

Personally what i would do if i were you is to get a smaller version of Linux and try to install that on the PC. 

Try something like Puppy Linux, Damn Small Linux, Slax or Slitaz and try to install one of them. They are tiny. 

If they install you will know it's an issue with Lubuntu. If not it's the PC.

CD's are cheap ;)

Kind regards

---

### Post by SEisch on 2011-02-18
I agree with matt_symes suggestion.  I have Damn Small Linux on a CD.  It only takes up fifty megabytes, and so far it has run on every single computer I've tried it on.  It is designed to run completely off of the CD and you don't need to install it to the hard drive.  Works good on old computers.  
It might be worth a try.

---

### Post by cascade9 on 2011-02-18
> **homefire said:**
> 
Running a memory test and noticed that something called ECC is disabled. Should it be? If not, how do I enable it?
 
No, its shouldnt be enabled, and no, you cant do anythign about it. 

ECC is special RAM, normally found in servers (ECC RAM = error correcting code memory). 

> **homefire said:**
> Also when I got up this morning, there was a cute little fiber optic screen saver running. Surely the screen saver takes memory, right? so how do I turn it off?
 
Screen savers take up such a small space, RAM and CPU use its normally pointless to disable it. 

> **homefire said:**
> Also is there an escape button? Like in Windows CTRL/ALT/DEL? Because I had opened a solitaire game last night and when I got up the icons in the games window had disappeared and there didn't seem any way to close the solitaire window. Had to reboot.
 
Neat trick- Ctrl + Alt + F1 (al at once like Ctrl + Alt + Del),  that will drop you back to a  command only screen. 

Then type this- 

sudo shutdown -h now

Your computer should shutdown. 

Or you can use-

sudo reboot

To reboot the computer ;) 

> **homefire said:**
> During bootup, there is a very tiny message that comes up at the top of the screen that says something failed due to unknown user ID.  What is that?

No idea on that, sorry. Could be the source of your trouble though. 

I've used xubuntu and lubuntu on machine slower than a 1.8GHz P4, and it shouldn't be that slow. 

BTW, with a liveCD the filesystem is not used (apart from swap, if it exists) so I doubt that any partial, borked installs are slowing down the lubuntu liveCD.

---

### Post by homefire on 2011-02-18
Downloaded Puppy Linux. It installed great, but when I tried to download the internet browser, it froze. 
 
QUESTION: How do I get to a DOS prompt? I'm assuming this is still possible? I'd like to wipe out the whole thing.
 
Or is it just landfill time?

---

### Post by jumpgroup on 2011-02-18
> **homefire said:**
> Downloaded Puppy Linux. It installed great, but when I tried to download the internet browser, it froze. 
 
QUESTION: How do I get to a DOS prompt? I'm assuming this is still possible? I'd like to wipe out the whole thing.
 
Or is it just landfill time?

Might be landfill time.  The repeated issues seem to indicate you may have hardware problems.  If every OS you attempted to load has, at some point, either not installed or froze, that's not a good sign.  The only thing they all have in common is the hardware.  And if you're not good at diagnosing the hardware, by the time it's fixed, you'll likely burn enough time and cash to have gotten a new laptop.

Also, Linux uses a shell, which is similar to a dos prompt.  But the same commands won't generally work (a few are similar).  

I'm a little reluctant to suggest this, but there are free programs available that you can use to diagnose your PC.  Ideally, you want to burn these to a CD, set you PC to boot from the CD, and it will load a minimal OS shell.  It is completely command-line driven.  But you can then perform memory tests and check for bad hard drive sectors.  You can also reformat your HD, partition it and start from scratch if you want.  The issue is, using most of these tools can be a little daunting for the uninitiated.

The fate of all PCs is to eventually become bricks.  I'm not sure how much additional effort you're willing to dedicate to this one.

---

### Post by homefire on 2011-02-18
So you're saying that once I've put Linux on, I can't get to DOS anymore?  What's booting it to start with then?  I still see the Gateway screen before it shows the Ubuntu disc.
 
I would like to try a total reformat just to make sure...  No I don't give up easily.  And I have lots of time to burn.  :)
 
And once again, I thank all of you who are taking YOUR time to help me!

---

### Post by JKyleOKC on 2011-02-18
> **homefire said:**
> So you're saying that once I've put Linux on, I can't get to DOS anymore?  What's booting it to start with then?  I still see the Gateway screen before it shows the Ubuntu disc.Every PC motherboard/mainboard includes a read-only memory chip that contains the BIOS, and this is what boots things when you first power up. This boot code in the BIOS chip looks on devices that are listed in the BIOS "boot sequence" area for the next-stage boot loader, which for a hard disk is in the MBR (Main Boot Record) and presumably a similar fixed area for a bootable CD/DVD. That code, in turn, completes the boot process.

DOS itself was on the hard disk, and reformatting for the various installs has almost certainly made it unusable even if you could get it to boot. The install attempts have probably rewritten the MBR several times anyway.

If you can download a copy of DBAN, that will totally clean your hard disk. It's a bootable package, designed to fit onto a floppy so it will easily go onto a CD or a USB stick. Expect to let it run overnight; it's no speed demon, but it cleans the drive back to factory-fresh condition: no formatting, no nothing.

Hope this helps some; it certainly is beginning to look like hardware failure, and possibly several different items all failing at different times. Bad RAM, or a single bad sector on the hard disk, could easily cause the pattern you're seeing...

---

### Post by s1baker on 2011-02-18
```
"So you're saying that once I've put Linux on, 
I can't get to DOS anymore? What's booting 
it to start with then? I still see the Gateway
screen before it shows the Ubuntu disc."
```


 Yes, you can have DOS on a Linux machine. You must remember that the Linux Operating System is different than DOS ( or the Windows 7 Operating System for that matter ). The commands that you will input into Linux, that would be comparable to inputing commands into the old DOS, would be commands that you would put into the terminal on Linux.  
 There is a program that you can install on Linux that will allow you to run the legacy Windows DOS programs, although there might be a problem with the graphics intense programs. It is called dosemu. I have it installed and I still use it to run Qbasic old programs that I have. Some of these programs are 20 years old.

---

### Post by homefire on 2011-02-18
Thanks, Jim, for the info.  I'm learning a lot, if nothing else!  :)  I may try DBAN.  What do I have to lose, after all? 
 
> Yes, you can have DOS on a Linux machine. You must remember that the Linux Operating System is different than DOS
 
Yeah, I realize that, but that's not what I was asking.  What I wanted to do was to reformat my hard drive again, now that I've had all these failed installations.  I don't _want_ something that runs within Linux--I want to get rid of it all!  The idea is that maybe that would also get rid of anything that is messing up my installs so that I could have a fresh start.  The only way I knew to reformat was in DOS, so I guess I'll have to learn a new way!  :)
 
Anyway, right now we're still messing with the browser.  First used Dillo, which is worthless--no java, can't enable cookies without major hassle--and now we're trying to download Chromium.  We'll see.  
 
Ugh.  Just froze again.  DBAN, here we come.

---

### Post by eriktheblu on 2011-02-18
If you're comfortable with DOS, there is [FreeDOS]("http://www.freedos.org/").

Otherwise, I quite like the [GParted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") for it's small footprint and simple interface. You can use this to create a swap space as well (bet you a dollar a swap partition will improve your live CD performance).

For someone new to Linux, I still recommend an Ubuntu varient. Lubuntu ought to run fine on your hardware even though Puppy and DSL probably require less resources. Ubuntu is great for the Linux newbie if for no other reason than the support you can find online.

I know this can be frustrating. Know that there are many ways of doing things in the Linux world, and we haven't even scratched the surface yet.

---

### Post by homefire on 2011-02-19
I started running DBAN yesterday afternoon and it said 8 hours remaining.  Last night when we got home, it said 16 hours remaining.  This morning it has been running for over 14 hours and it now says 31 hours remaining.  And one must wonder if it will ever stop?

---

### Post by JKyleOKC on 2011-02-19
That sounds as if there's a problem on the hard disk that DBAN cannot get past for some reason. When the time estimate keeps going up (for any program that provides one, not just for DBAN) it usually means that the program cannot get past a certain point, but keeps trying.

I don't know the internals of DBAN, but have programmed other routines that provide the time estimate. The usual way of calculating such an estimate is to determine speed (often in bytes per second but for something like DBAN I would probably use disk sectors per second instead), and elapsed time in seconds. Then divide the total size of the job by the speed, to determine the total number of seconds, and from that subtract the number of seconds already gone by. The result is the number still to go, and conversion to minutes or hours is fairly simple.

If the number of bytes or sectors doesn't increase, but elapsed time does, then the speed goes down, and "time to go" increases. Since the program just keeps trying, this will go on until you power it down.

For your situation, it might be something as simple as a bad configuration of the BIOS (I'm fairly sure that this is where DBAN gets the disk size from, since it's almost the only place that it can; however it might be getting the size directly from the drive) that makes the disk seem larger than it really is, or it might be an actual disk failure somewhere near or past its halfway point. 

If it's a BIOS misconfiguration, you may be able to change the setting by going into the BIOS setup screen (the Dell splash screen at power-up should tell you how to get there) but I've never owned a Dell machine so can't be a lot of help past this point.

If it's an actual disk failure, it's the end of the road unless you want to buy a new drive and install it. That wouldn't cost nearly as much as a new laptop or even new RAM for it, but would still be in the range of $50 to $100 in my neck of the woods...

EDIT: I just went back to the start of the thread to check the specs of your system and see that it's an 80-GB drive. For comparison, last year I bought a 500 GB drive, new, for $55 plus sales tax. It's very hard to locate anything smaller than 250 GB today, but a bit of browsing through used-computer shops or flea markets might get you a real bargain in a used drive that could replace your problem child!

---

### Post by cascade9 on 2011-02-19
> **JKyleOKC said:**
> If it's an actual disk failure, it's the end of the road unless you want to buy a new drive and install it. That wouldn't cost nearly as much as a new laptop or even new RAM for it, but would still be in the range of $50 to $100 in my neck of the woods...

EDIT: I just went back to the start of the thread to check the specs of your system and see that it's an 80-GB drive. For comparison, last year I bought a 500 GB drive, new, for $55 plus sales tax. It's very hard to locate anything smaller than 250 GB today, but a bit of browsing through used-computer shops or flea markets might get you a real bargain in a used drive that could replace your problem child!

It could be a controller problem, not a HDD problem. A HDD problem would be far more common, but never rule out the controller untill you know its not the problem. ;)  (if its a controller issue, that would explain why liveCDs ran badly)

Being a old 1.8GHz P4 its probably only got IDE ports, not SATA. IDE drives are more expensive than SATA now.  It might also have the 128GB BIOS limit as well, so if the bigger drive was something that sounds nice, I'd check to make sure that they would work. 

BTW, getting a smaller drive than 250GB is still possible. Newegg has 80GB and 160GB IDE drives.

---

### Post by homefire on 2011-02-19
It's gone down to 29 hours now, so I'll let it run awhile longer. 
 
So Jim, would you honestly replace the hard drive on this rather than buy new? I doubt we will, because the memory is a huge issue, too. I'm thinking it actually might be possible to find a system someone is *giving away* that's bigger and newer than this one! Then I could play with ubuntu to my heart's content! :)
 
hmmm. Craig's list... ;)

---

### Post by COMPUTIAC on 2011-02-19
Hello, That is the way to go at this point.  In my area there high school level tech schools which sell complete systems for under $100. Used of course !

---

### Post by homefire on 2011-02-19
Seems like it has held steady and is going down at the same rate the time elapsed is going up now, but wow, it's going to be 40 hours total if it's accurate!  I'm sure anxious to see whether it does anything good.

---

### Post by Irihapeti on 2011-02-20
When I ran DBAN on an old computer, it took 2 hours to run one pass on a 20 GB drive. That suggests that 3 passes, which I think is the default, would take 24 hours on an 80 GB drive.

If it wants much more than that, somthing odd could be going on.

---

### Post by homefire on 2011-02-20
Well, it's been running 38 hours and says it has 4:40 left to go.  It's on the third pass, 89% complete.  No idea what's going on, but I'll be gone for a few hours today, so presumably this afternoon it will be done, and we'll see what I have.
 
Btw, I love your signature line, Irahapeti!  Clever.  :)

---

### Post by homefire on 2011-02-20
Looks like it's toast.  When I got home, the message on the screen was 
Fail: ATA Disk...blahblahblah bunchofnumbers.  
 
I guess that means forget it.  
 
Ah, well.  Thanks for your help, everyone!

---

### Post by cascade9 on 2011-02-21
Try the disc on a different computer if you can.

---

### Post by jumpgroup on 2011-02-24
Ok, who in the betting pool picked "hardware failure"?

Sorry about the hard drive.  You spent a good amount of time on this project. Don't give up on Linux.  Obviously the community is here to support you.

---

### Post by cgroza on 2011-02-24
> but we do want to be able to stream video, play games, etc. Possible?
There are games for linux, but that depends very much of your taste. Vistit [http://www.linuxgames.com/](http://www.linuxgames.com/), they have a list available there. I got Counter-Strike running in wine on a machine like yours.

---

### Post by homefire on 2011-02-24
Yes, I tried it on this machine and it ran fine, so we've just given up on that one. Oh, well...I guess that happens sometimes! So now we're down to only 3 computers in the house...terrible huh? :)
 
I do want to thank everyone for all your suggestions and input.  It was a good experience, even if it didn't pan out.  I still may try Linux again if we happen onto a computer really cheap somewhere.

---

### Post by guilleme on 2011-02-24
Hi.
I think ubuntu should work fine on that computer. I've got an even older system running ubuntu 10: it's an old celeron (pentium III-based), with 391 mb ram, and 30 gb hard disk, and it manages to take ubuntu out for a walk ( Because I can't say it runs all the time:)), but works fairly well. 
If you desire the computer to be easy to use for kids and to run smoothly, I would suggest you to take a look at quimo, it's a very lightweight ubuntu distro that uses not even KDE, but xfce, and that means it can run from a cd on a computer with no hard drive and 256 Mb ram with no problems. 
My little cousins love it as it has a dock on the desktop full of kids games and useful things, and that way it's easy to use. 
The web page is: [http://www.qimo4kids.com/post/Qimo-20-is-now-available!.aspx](http://www.qimo4kids.com/post/Qimo-20-is-now-available!.aspx)
Remember you can give it a try from the live cd, and then decide what to do about it.
Good luck, and see-ya.:)

---

### Post by homefire on 2011-02-24
Um, my kids are teens, and most of the games they play are online.  
 
We tried Puppy Linux, and it wouldn't even support a decent browser, as far as I could see.  Are you saying that Qimo would?  Because even if we could just have internet and nothing else on that machine, it would really free up mine.  In fact, it would suit me fine if my kids could facebook and not much else on it!  :)

---

### Post by guilleme on 2011-02-25
Sorry about the misunderstanding about your kids, I bet then that they won't be as exited by playing "find-the-letter-to-protect-the-penguins" as my little cousin is :). 
Now, if you want to use the computer for internet, facebook, mail and youtube, i bet you can survive running from a live cd. 
Quimo as a cd comes with firefox preinstaled and ready to use. I can't recall if it has flash support, but I'd bet it does. A note: If you are running from the cd, you won't be able to install applications or extensions, because the cd will already be full, but if you'r computer has a dvd drive, you should better put it on one, because that way, you can install more things later. 
see-ya:).

---

### Post by cascade9 on 2011-02-26
> **homefire said:**
> Yes, I tried it on this machine and it ran fine, so we've just given up on that one. Oh, well...I guess that happens sometimes! So now we're down to only 3 computers in the house...terrible huh? :)

Was that 'tried the HDD that failed on this machine and it worked fine'? 

If so, you probably have 1 bad IDE channel (probably primary). You can run the CD/DVD drive and the HDD hooked up to a single IDE channel ;) 

Another option is a USB flash drive. If you have a early P4 with USB 2.0 ports (pretty rare) or are prepared to buy one (fairly cheap) it should run pretty well.

---

### Post by hakermania on 2011-02-26
You could try [TinyCoreLinux]("http://www.tinycorelinux.com/") :D It's fantastic and around 10 MB! :D

---

### Post by homefire on 2011-02-26
Fantastic as in...will run video nicely, browse the internet with no lag, run java, etc?  And requires no knowledge of code?
 
> Was that 'tried the HDD that failed on this machine and it worked fine'? 
 
If so, you probably have 1 bad IDE channel (probably primary). You can run the CD/DVD drive and the HDD hooked up to a single IDE channel :wink: 
 
Another option is a USB flash drive. If you have a early P4 with USB 2.0 ports (pretty rare) or are prepared to buy one (fairly cheap) it should run pretty well.
 
You lost me, Cascade.

---

### Post by JKyleOKC on 2011-02-26
Okay, since the drive works in another machine, the problem appears to be in the HD controller of the original system. Since the CD appears to work in that system even though the HD does not, this implies that only half of the controller has gone south.

These controllers have two main channels, each of which has two sub-channels. Normally, the HD will be connected to one of the two main channels, and the CD drive to the other, with both drives set up as "master" via little jumpers plugged into the back of each drive.

What Cascade suggests is that you could move the connection of the HD from its original cable, to the unused connector on the cable going to the CD drive, which would take it from the first main channel to the second, using the second sub-channel of that main one.

For this to work you would also need to change the jumper from the current "master" position to the "slave" position, on either of the drives. It makes no difference which connector is which; the jumper determine which drive on the cable responds to signals coming in from the controller.

It's definitely worth a try, especially since there's nothing to lose but a little time. I would leave the HD set as master and change the CD to slave, but that might be easier said than done since the jumpers are very small and difficult to get to without removing the drive from its home. You should find information on the drive that tells you how to position the jumper; every drive is different. If you're lucky, you'll see the letters M, S, and C stamped into the drive case just above the pins for the jumpers -- they stand for master, slave, and cable-select respectively, and in this case just pull the jumper off of the M pair and put it on the S pair. However it may be a bit more complicated than that...

---

### Post by cascade9 on 2011-02-27
Thanks JKyleOKC, that saved me some typing. 

You probably explained it better than I would have anyway. ;)

---


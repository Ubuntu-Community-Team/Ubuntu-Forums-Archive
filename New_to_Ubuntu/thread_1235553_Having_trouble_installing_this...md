---
title: "Having trouble installing this.."
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Ronchap on 2009-08-09
My friend gave me his computer. I wanted to learn linux and everything I need to know on it and how to use it as a beginner. So I bought Ubuntu Linux for Dummies. It came with a live CD, but my friend had a more updated version (9.06) that I am running live from the cd right now.

I was trying to install it permanently onto the computer, but during the install, the window that stopped me from installing was asking for a petition? I read in the dummie book that, it is required if I was running another OS, probably Windows. So I took the cd out, and restarted the comp. That doesn't work cause when I start it up, it asks for a system boot disk without the Linux cd in. So I just assume right now, that my friend has already removed any other OS on this comp. The internet and Firefox is running fine from Linux live cd as you can see.

Am I screwed for now on trying to install it to the pc without another boot disk? Or am I doomed to a sure fire halt on my challenge of doing this myself without having to call my friend over about the system boot disk?

EDIT: I said 9.06 on here cause that's what my friend had written, but I'm only seeing 9.04 online to download. Maybe he wrote it down wrong. I don't know for sure.

---

### Post by Bradtek on 2009-08-09
So is Windows on the computer or not ?

If it is and you want to keep it, choose Use the largest continuos free space option for partition (something like that)

If it is and you want to get rid of it choose, Use entire drive (something like that)

And yes 9.04 is the current version, no such thing as 9.06

---

### Post by Ms_Angel_D on 2009-08-09
Any OS Needs a partition to install on. It sounds to me like this computer has no OS installed on it. So You should probably just follow the installers recommendations as to what to do. It will automatically partition and format the hard drive as necessary.

---

### Post by Ronchap on 2009-08-09
I have no idea what it is. Without the linux cd, I can't start the computer up. When I use the cd to run it live, the install icon is on the top left, so I double clicked that. I select my language, then time zone, keyboard layout, then it goes to the "Prepare partitions" window. Nothing to select, and the buttons on the bottom are grayed out. I can't select anything. So I try to just hit Forward. "No root file system is defined. Please correct this from the partitioning menu." Can't do anything else from this point.

---

### Post by halitech on 2009-08-09
while running the live cd, open a terminal and run
```
sudo fdisk -l
```and post the results here

---

### Post by Ronchap on 2009-08-09
Halitech - I copied and pasted that into the terminal, and when I hit enter it just drops to a new line and says "ubuntu@ubuntu:~$ "

---

### Post by halitech on 2009-08-09
sounds like your friend did more then remove the OS, sounds like he removed the hard drive completely. You should have gotten something similiar to this
```
daryl@debian:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7bbb99b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       19209   125001765   83  Linux
/dev/sda3           19210       19457     1992060   82  Linux swap / Solaris
```

---

### Post by Ronchap on 2009-08-09
That's news to me. :(. I always thought you couldnt do ANYTHING without a hard drive, so when I was about to boot it up and surf the net, I didn't even wonder about not having a hard drive.

---

### Post by halitech on 2009-08-09
as long as you have ram and a video card installed, it will boot. If you have a cdrom you can run a live cd but unless you have a hard drive, you can't install anything. Do you feel confident enough to pop the cover and see if it has a hard drive or not?

---

### Post by Ronchap on 2009-08-09
He has a clear sided case, I see one in there. I should also note that, as far as computers go. I have not so good experience. I just know how to play games on it. Then, I started to get bored with my games, and actually want to learn something. And that is where this comp and linux comes in. I've been told it is gonna be a little hard to learn, but I like challanges and thought it would be fun to learn to be honest.

---

### Post by halitech on 2009-08-09
ok, and there are 2 sets of cables going to it? maybe boot into the BIOS and see if it is detecting the drive

---

### Post by Ronchap on 2009-08-09
Yea, I've tried restarting twice, but everytime I do. It tells me to eject the linux cd and hit enter. Then it restarts, and comes back to the insert boot system disk. Even when I restarted it, this computer looked alot different than mine and I was opress f10 and delete to try to bring up the BIOS but with no luck. It's getting pretty discouraging. Really don't want to have to wait 6-7 more hours before my friend can get over here.

Under places>computer, there is a filesystem, it shows fodlers and files..etc. Plus with spaced used and free space available. So i was assuming that was the hard drive too.

---

### Post by halitech on 2009-08-09
so it does show the drive under places - computer, odd that fdisk -l doesn't show it. when you boot the live cd, there should be an option to install, maybe try that instead of the try option. You also need to tell it where to install it so try the manual setup

---

### Post by Ronchap on 2009-08-09
That's the thing though.  It just loads up straight to the desktop with the linux disc in. It doesn't give me an option of anything. Your probably right, something isnt connecting or reading right. I really don't want to keep spamming the forum with problems. Ill continue to look around and read more for a few, and if nothing else happens. I'll just switch back to my comp until my friend gets here.

Thanks for the patience and help! Once we get it back and fully running, I'm sure I'll be back here with future questions.

---

### Post by halitech on 2009-08-09
so it doesn't even give you the option of selecting a language when you first boot? sounds like a custom made cd which could be whats going on.

---

### Post by Ronchap on 2009-08-09
No straight to the desktop, like a windows OS. It does this with his burnt cd, I'm going to try it with the linux cd that came with my book for dummies. Something I probably should have done in the first place right?

---

### Post by halitech on 2009-08-09
I wonder if he used remastersys or something to create a bootable cd? try your cd that came with the book and see what happens

---

### Post by Ronchap on 2009-08-09
Alright.. The disc from the book brought up the menu about installing it or running it. NOW the problem is, both keyboards I have and tried this with, they don't "come on" until everything loaded up from the disk. It stays on the option menu for about 30 seconds, but I cant scroll down or up, or even hit enter. Like my keyboard's are  blocked until everything loads. So it just automatically loads it, like it has been. *sigh* If it isnt one thing, it's another. 
This is probably why I couldnt pop into the BIOS on this computer. Like I said, I dont know alot about how to fix a comp, but something's I know how to do. Opening BIOS I know how, but without being able to use the keyboard until LInux is loaded, it doesn't give me much of a choice.

---

### Post by halitech on 2009-08-09
are you using a usb keyboard? if you are, you may need a ps/2 keyboard to get into the bios so you can enable legacy support for keyboards

---

### Post by Ronchap on 2009-08-09
1 is USB and the other is ps/2.

---

### Post by halitech on 2009-08-09
and you still cant get into the bios with the ps/2 keyboard? thats strange

---

### Post by zkriesse on 2009-08-09
I think what happened here is that, through no fault of yours man, the install process got REALLY F****D up somewhere along the way. It shouldn't even be this hard...not even a little bit! Give your buddy a call and ask him or maybe someone else you know to burn a new copy of Jaunty Jackalope on a DVD disk for you and then try that...

---

### Post by Ronchap on 2009-08-09
Yea. This time I got the USB keyboard to turn on in time to enter BIOS. But that was only cause I unplugged it and then restarted. When it booted up, it said no keyboard and stayed there. I just plugged it in and pressed Del. Things are looking good right? so I thought. 

After i left that, it went back to the black screen with "Disk Boot Failure, Insert System disk and press Enter." So I put the un burnt disk and, once again I cant press enter. The lights on my keyboard went out had to restart with the disk in it again. 
So then it loaded, and with the book disk, the install/load menu popped up again before loading up to the desktop. 30 second timer, and keyboard not working there again.

Right now, with my small learning speed at this rate, it's like me trying to comprehend the size of the universe in my head, starting with our smallest planet, and then moving to the next biggest planet and star I know about...something I cant personally fathom :/.

So, looks like I am actually gonna wait till my friend get's here. I appreciate all the patience and help!!

---

### Post by zkriesse on 2009-08-09
It's cool man...that's what the forums are for.

---

### Post by Ronchap on 2009-08-10
Update!! Got it working! And I installed my first plug-in, Adobe Flash, by myself. (well thanks to instructions from a post on here.) The comp wasn't reading the hard drive he had in here cause... it wasn't connected. Even though it's a free hand me down computer.. it still tramples my old one. My next task is and probably will take all night. Tryin to see if I can get Guild Wars to install and run.

---

### Post by Ms_Angel_D on 2009-08-10
Guild Wars is very simple to get running just use Play On Linux([http://www.playonlinux.com](http://www.playonlinux.com)) to get it up. Both my hubby and I play Guild Wars on our Ubuntu, and it runs just fine.

---

### Post by Ronchap on 2009-08-10
oh, haven't heard of that program yet. I installed Wine and its almost done installing with that. You recommend I stop and re-do it with PoL?

---

### Post by Ms_Angel_D on 2009-08-10
Well, Play on Linux is just an installer for wine, so either way can get Guild Wars up. Play On Linux however just makes it easy to make sure you have all the dependencies and configurations set up properly. 

There is also [Crossover]("http://www.codeweavers.com/products/cxlinux/") and [Crossover Games]("http://www.codeweavers.com/products/cxgames/") as well as [Cedega]("http://www.cedega.com/"). These all use wine, but they attempt to make it as easy as possible to accomplish your task. While Cedega and Crossover are not freeware, Play On Linux is.

---

### Post by Ms_Angel_D on 2009-08-10
As an afterthought I wrote a blog post when I installed Guild Wars, the first time on Ubuntu, Detailing how I did it. So I thought I might share it with you, hoping it would help you out.

[LOOK HERE]("http://www.thedallemagnes.info/index.php?option=com_content&task=view&id=206&Itemid=72")

I hope this helps.

Angel

---


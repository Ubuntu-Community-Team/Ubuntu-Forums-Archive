---
title: "Installing Ubuntu on Aspire One"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Ioosef on 2010-03-18
Hi there! A while ago I installed Ubuntu 6.something on an old computer I had, that my brothers used without restrain, and the computer lasted... up until now (or rather, until my brother took it to his room and changed the password so only he could use it...). 

Anyway, for the brief period of time I used Ubuntu, I was quite happy with it, even though I didn't know squat about it. That was the first time I had ever seen Linux. So, when I went to buy a netbook for school, I specifically bought the one that came with Linux, much to my surprise it came with Linpus Linux Lite (that's a mouthful). I've been looking only and have read cases of people installing Ubuntu on this same netbook, and I was wondering, who could I go about doing that, installing Ubuntu there? The netbook doesn't have a CD reader, so that poses a bit of a problem. 

Also, I have read that people had some trouble using the wireless hardware stuff (so I don't know much about computers, what else is new?), and so couldn't access wireless networks. Any ideas how I could fix that? Also, how would I uninstall Linpus to make more space for Ubuntu, since I only have 8 gb of space on my hard drive. 

Anyway, thanks for any responses, hopefully the transition will be as smooth as a baby's bottom.

---

### Post by Peter09 on 2010-03-18
I have an Aspire One and use Ubuntu NetBook Remix - works out of the box. Download the iso and use the Create bootable thumbdrive utility (whose name I forget) to create a bootable drive. You can use that to install to your Aspire One.

---

### Post by Ioosef on 2010-03-18
Ok, so I looked up Ubuntu netbook remix, and got this site
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I looked up UNetbootin, and found this other site. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm having some trouble downloading the file for Linux, so, would I be able to download the CD image to my laptop (which has Windows XP), create the bootable USB drive and then use it on my netbook, all without running the risk of like, deleting everything I have on my laptop by installing Ubuntu by accident or something?

Also, would installing Ubuntu on my netbook, from the USB drive delete everything I have on my hard drive? I only have 8 gb of space, I don't want to be left with only 1 gb after installing Ubuntu. 

One last thing, does the wireless internet work on your netbook after installing Ubuntu? If not, how did you fix it?

---

### Post by spiderbatdad on 2010-03-18
I use an acer aspire also with remix. The out-of-the-box wireless depends on the wireless card you have. The Atheros should work automatically. 8gb is very little for a full install. Do you have a larger hdd you could reallocate some space for? Run from a live flash drive is of course possible, but very little room for creating persistence, user preferences, and upgrades are out of the question. The installation will offer you partitioning options should you choose to install the OS, so you will not have to wipe out linpus.

Not sure what problem you are having with unetbootin, I use it all the time. You should be able to point it to any iso you have saved in your filesystem.

---

### Post by Ioosef on 2010-03-25
I tried downloading both the Linux and Windows version of UNetbootin but they both register as executable files which apparently I can't open. It seems I don't have the right program to open such file (I think the Linux version is a BIN file, and not even that). Is there some way I can create the bootable USB drive on my laptop (which has windows XP) and then use it on my netbook? 

Also, I have 2 slots to insert SD cards (I think that's what they're called), and I have 2 cards of 4 gb each, would that be enough memory?

---

### Post by Ioosef on 2010-03-26
Ok, I asked my cousin for a bit of help, and he showed me a program called LiLi. I used that and I think I've got a bootable USB drive now (at least for my laptop with windows it looks that way). I connect the USB drive to my netbook, and try running pretty much all the files I've got there, but nothing happens. It seems my netbook can't run any file that is described as "executable". It's really starting to piss me off... Anyone's got any suggestions? 
I can post a picture of what I've got on my USB drive at the moment. I basically downloaded that 600 mb file with Ubuntu and put everything on the USB drive. I then used LiLi to make the USB bootable, but I think there's something really wrong with my netbook.

---

### Post by Peter09 on 2010-03-26
No - you dont do things like that - have you any other Ubuntu machines that you can get to? 
 
You download the .iso and then point Unetbootin at it. It will unpack the .iso and create a bootable drive.
 
My Son has just done the same thing and it worked first time - he did have access to another Ubuntu machine though. Once you have a bootable drive your machine should boot directly from that - it should not go to the onboard system. 
 
P.S my Aspire One has an 8GB dirve, with the install and my emails I use 4GB - thats it. As long as you do not wish to load large games on it 8GB appears ample.

---

### Post by Slonda828 on 2010-03-26
Ioosef,

 If I am repeating anything others have said, then just humor me. If you have windows on your netbook, or access to a windows box at work or elsewhere, then this is how I would handle it. 

1.) Google "ubuntu netbook hardware compatibility list" and find the wiki that lists which netbooks work best with Ubuntu. Make sure yours is one of them.

2.) Google pendrive linux. Go to their site, and download their windows based application for slicking and burning a thumb stick as a bootable USD drive. Run the application, and do what it says.

3.) Get an .iso copy of the distro that you want. Put it on the USB drive. I know that pendrive linux natively supports ubuntu netbook remix if you fancy a good distro for your netbook.

4.) stick your fancy new bootable USB drive in your netbook with it off. Boot it up, press F2 to get into the CMOS setup, and then select it and make it the first "hard drive" to boot. Save and exit.

5.) wait for your computer to reboot. Grub's menu should appear and you should pick your distro. It will boot (live) into your distro. Then select your distro's installation application, which will re-partition your hard drive.

6.) Enjoy. Also, if you have boogered up your netbook at this point, get DBAN. It will slick your hard drive to DOD specs and make everything easier as far as installing new stuff. Additionally, you can add DBAN to your pendrive linux thumb stick and it already has a menu item for it in the menu.lst file on your bootable thumb stick (which may or may not be commented out).

---

### Post by NightwishFan on 2010-03-26
This link may or may not be of help.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by undecim on 2010-03-26
> **Ioosef said:**
> I tried downloading both the Linux and Windows version of UNetbootin but they both register as executable files which apparently I can't open. It seems I don't have the right program to open such file 

If you are doing this from your Linpus system on your netbook, you will need to run UNetbootin as root.

If I recall, my AA1 that I had didn't have a terminal icon or run dialog anywhere. I had to open the terminal via the file browser right-click menu.

So try this:

Open a file browser and navigate to the directory with the UNetbootin file.

Right click inside the file browser and open a terminal.

In the terminal, type ```
sudo ./unetbootin.bin
``` where unetbootin.bin is the name of the UNetbootin file (this is case sensitive)

Then it should open UNetbootin and you can select Ubuntu and your thumb drive.

---


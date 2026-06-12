---
title: "AVI wont play in Totem"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by macheted01 on 2009-10-12
Hi, new to Ubuntu and having some problems. Getting very discouraged. I am trying to play an AVI file with Totem 2.22.1. The file is playing and I hear sound, but no video. It just shows the visualizations working to the sound. I am guessing there is some kind of codec needed or something, but totally clueless. I just recently figured out how to enter commands in the terminal and clean up some space on my drive and this is the extent of my knowledge to Ubuntu. Any help would be great on what I need to get and how to install it. Thanks.

---

### Post by PrePenguin on 2009-10-12
You have to go into the program manager and install restricted extras for your codecs etc to work.

---

### Post by macheted01 on 2009-10-13
I'm already lost. How do I get into the program manager? As I said, I am very new to this and my knowledge of Ubuntu is bad. I'm thinking I may have made a mistake by ordering this new laptop with Ubuntu. I understand why Ubuntu would be favored after running XP, Vista for so long, but it seems to be an operating system for those that have some programming background. Thanks.

---

### Post by whoelse on 2009-10-13
go into "Application"->"Add/Remove ..." and search for "restricted-extras"

---

### Post by |Mitch| on 2009-10-13
or go to terminal and type sudo apt-get install ubuntu-restricted-extras

---

### Post by whoelse on 2009-10-13
> **|Mitch| said:**
> or go in terminal and type sudo apt-get install ubuntu-restricted-extras
which is of course faster, but as macheted01 mentioned that he is  new to Ubuntu I still recommend him to get a look at the "Add/Remove ..." tool. There are a lot of useful programs there and nobody can argue that marking a checkbox is for programmers only. ;-)

---

### Post by |Mitch| on 2009-10-13
The OP just said he recently learned how to enter commands in the terminal, just trying to work on what he already knew.

---

### Post by macheted01 on 2009-10-13
Ok, I entered the command: sudo apt-get install ubuntu-restricted-extras
I did figure out how to open the terminal window and enter commands.
It ran through the process and it seemed to install successfully. Although, I ran into a problem I ran into earlier. A little window popped up and said that a 100% of disc space has been used. I stumbled onto the command that cleans out unused stuff on the system, so I will run that later.
I tried to play the avi and it did the same thing. I restarted the computer because I know that it is needed sometimes and it did the same thing. What do I do next?
 
By the way, I have the Dell 910 mini 4 gb solid state hard drive. That is why the hard drive space is ate up so fast.

---

### Post by |Mitch| on 2009-10-13
Did it install or just abort the installation?

Thread with how-to to clean junked up files: [http://ubuntuforums.org/showthread.php?t=140920&highlight=clean](http://ubuntuforums.org/showthread.php?t=140920&highlight=clean)

Either way: 4GB may not be enough space on the hard drive...

---

### Post by macheted01 on 2009-10-13
Yeah. it seemed to complete the install. Nothing popped saying it did not. The terminal just ran through a lengthy process and finished with waiting for another command.

---

### Post by macheted01 on 2009-10-13
You know what, I think you are right about not enough space. I dont understand why they would even build a system like this. I think I am going to call Dell up and send it back. That just dont make no sense to me. I mean the operating system cant even really update itself. What a joke.

---

### Post by lavinog on 2009-10-13
Is this a netbook?  If so 4gb is normal for a netbook install. 4gb is not enough for a regular desktop install.

---

### Post by Vaphell on 2009-10-13
true that
4GB is not enough space to have any general purpose machine with heaps of sotware installed. SSDs are ungodly fast though. It can do well as a portable web browsing device and some lightweight text editing, but don't expect it to do much more.
XP on the other hand wouldn't do much better here. It can be small, but it doesn't have any meaningful software in a default setup, everything from codecs to office suite has to be additionally installed (Ubuntu has a lot of software already installed except licensed/non-free stuff like codecs in your example).
If you want to have 'normal' computer go with oldschool hdds 200GB big.

---

### Post by macheted01 on 2009-10-13
Yes, it is a netbook. The Dell Inspiron 910. With 8.9" monitor. I dont even see them on the Dell website anymore. They must of been a bad idea. I'm on hold with Dell right now.

---

### Post by lavinog on 2009-10-13
The mini 10 series is the only one i see on their store with linux.

---

### Post by macheted01 on 2009-10-13
Yeah, they dont even have it up on Dell no more. The support guy said there is a 16 gb solid state drive available for this. Just waiting to hear how much. I'm not really looking to do a whole lot with this thing. I have a Dell XPS system that I do any of my more technical stuff as far as video and audio editing goes. I'm just looking to get this thing to where I can take it on the go and get online or watch a movie or something. It has an SD memory card slot, which is cool to store files. I dont know still on hold, good times.

---

### Post by |Mitch| on 2009-10-13
You could throw puppy linux on there and be done.

---

### Post by macheted01 on 2009-10-13
Well, $75.00 for 8gb upgrade or 175.00 for 16gb upgrade. Waiting for a call back to see what is available. What is the puppy version all about?

---

### Post by |Mitch| on 2009-10-13
Puppy Linux takes about 100mbs to install, very resource efficient, quicker than Ubuntu, base install doesn't take a lot of space, for what you want to use the netbook for it would be ideal...

[www.puppylinux.org](www.puppylinux.org)

---

### Post by fc2a on 2009-10-15
THis is my first post. I have a brand new Mini 9 with ubuntu and a 4gb SSD. I got it yesterday. I am not trying to hijack your thread I merely have the same question. The box came with totem, but I managed to find VLC as well.
 
When I try to play with Totem: "An error occured could not read from resource"
 
When I try to play with VLC: "Unrecognized format for 'file:///media/cruzer/video/BLAHBLAHBLAH.avi
 
Is there anything in the Synaptic Package Manager that I can get to makey workey?:confused:

---

### Post by lavinog on 2009-10-15
> **fc2a said:**
> THis is my first post. I have a brand new Mini 9 with ubuntu and a 4gb SSD. I got it yesterday. I am not trying to hijack your thread I merely have the same question. The box came with totem, but I managed to find VLC as well.
 
When I try to play with Totem: "An error occured could not read from resource"
 
When I try to play with VLC: "Unrecognized format for 'file:///media/cruzer/video/BLAHBLAHBLAH.avi
 
Is there anything in the Synaptic Package Manager that I can get to makey workey?:confused:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by macheted01 on 2009-10-15
Hey fc2a,
I think you will run into the same problem I did. You will use up all your disc space. If you discover something different and get things working, I sure would like to hear about it.
I really want to like this mini. I just dont understand why they would put this out there with just a 4 gb hard drive, when the operating system eats up all your space. I went through to see if there is any unnecessary stuff running that I dont need, but really kind of scared to mess with too much. I was able to order the 8gb solid state hard drive, that I should of upgraded to in the first place. $95.00 to add on to this. I think I will feel safe with that running this Ubuntu system as I am anctious to start learning my way around on this operating system.
One fella replied back with using puppy linux, which sounds good, but I think I will try it out on an older computer first. Anyways, let me know what you come up with.

---

### Post by fc2a on 2009-10-15
Yes its a problem, I havent had this thing for 24 hours yet.  I have done one update and I have about 500MB of space left.  And I thought ubuntu was supposed to work on very minimalist systems.  I am not going to download anymore updates.  If I cant make it work I will buy a 64MB SSD and windows 7.

---

### Post by macheted01 on 2009-10-16
fc2a,
You might be interested in this thread,
[http://ubuntuforums.org/showthread.php?t=1283607](http://ubuntuforums.org/showthread.php?t=1283607)
You might be further along on this operating system than I. I'm just learning my way around, but thought this might help. I'm putting things on hold till I get the other hard drive.

---

### Post by macheted01 on 2009-10-16
Dell calls me today to tell me that the bigger hard drive for this is unavailable. So back to the drawing board.

---


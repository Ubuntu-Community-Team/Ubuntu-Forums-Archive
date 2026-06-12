---
title: "Windows XP - 2nd disk needed for Ubuntu"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by gladys emmanuel on 2010-06-24
Good evening
 
Complete newbie to Ubuntu and not that good with hardware so apologies if this question is too simple. I have done a search and can't find the answer either.
 
OK, I have a six year old Dell pc that is running Windows XP. It's mainly the wife and kids that use it but it is really slow. I've tested the Ubuntu CD and like what I see so far.
 
What I intend to do is the following:
 
* Puchase a second hard drive (already got this actually. It's an IDE one as a SATA would not fit)
 
* Fit the hard drive to the machine.
 
* Install Ubuntu onto the drive and have the machine so that it will boot into either Ubunto or XP.
 
This is where my technical knowledge lets me down. I've got the hard drive physically connected to my computer. It's connected to the ribbon cable that also feeds the CD drive. That is as far as I have got.
 
Do I want the jumper on the drive as Master or slave (or something else)?
 
What do I then need to do to get it so that the computer will recognise the drive?
 
Should I then partition the drive or will Ubuntu do that for me?
 
 
Once I've fit the hard drive, I'll trawl around looking for how to install Ubuntu onto it and whatever.
 
Sorry for being a complete dimwit but if anyone can help - or point me in the direction of a guide, I'd be grateful.
 
 
Cheers
 
Gordon

---

### Post by KdotJ on 2010-06-24
Hello there and welcome.

Many people will tell you its a good idea to disconnect your other (Windows?) hard drive, and just have the new one connected. Then you can put the Ubuntu Cd in and install it to the hard drive. As far as partitions go, you can, if you want let Ubuntu do it for you. At the partitions screen of the installation process, your drive should be shown and your best bet would be to select "use entire drive".

Once finished, you can shutdown your machine, and re-attach the 'old' hard drive. I think that for jumpers, you choose master or slave depending on what drive you want to be primary.

Now I may be somewhat a bit wrong in some of this but someone will correct me

---

### Post by Nightstrike2009 on 2010-06-24
> **By KdotJ:**Many people will tell you its a good idea to disconnect your other (Windows?) hard drive, and just have the new one connected. Then you can put the Ubuntu Cd in and install it to the hard drive. As far as partitions go, you can, if you want let Ubuntu do it for you. At the partitions screen of the installation process, your drive should be shown and your best bet would be to select "use entire drive".

Once finished, you can shutdown your machine, and re-attach the 'old' hard drive. I think that for jumpers, you choose master or slave depending on what drive you want to be primary.

This is not necessary (the jumpers are only relevant on first secondary hard disk installation, disconnection is not needed and will prevent grub from giving you a choice of which OS to boot up if you do).

I am a Dual booter too, you need to install Windows on the 1st hard disk  first then install Ubuntu on the 2nd hard disk afterwards (Ubuntu will format this itself), other wise you will not be able to boot Windows (Ubuntu's GRUB Bootloader could not detect Windows if first drive was disconnected). 

The only other things of note are to connect the power cable and the data cable (look the same as you installed drive and should only fit one way around) and screw to the case by aligning the 4 screws in the holes already in the tower units insides. 

In my experience as long as you do this and select the second drive as the installation target in Ubuntu's installer set up (not the windows one has that would erase it) you should have no probs.

Place the ubuntu disk in your cd/dvd drive before boot up and it should give you an option "Install" is the one you want.

If done correctly a black & white menu boot up screen will appear allowing you to choose either OS a boot up (This is the GRUB Bootloader mentioned earlier)

Good luck, friend :-)

PS: You are allowed 2 drives on an IDE cable the first jumper should be set to Master and the second to Slave (1st hard disk master, 2nd hard disk or CD/DVD drive set to slave) you should have two IDE connectors allowing 4 drives in total (as long as one is master, one is slave on each connector you should be fine AVOID TWO MASTERS OR TWO SLAVES ON SAME CABLE) 

> **By KdotJ:**Now I may be somewhat a bit wrong in some of this but someone will correct me

Sorry it had to be me my friend, didn't mean to upstage anyone just provide the correct info to new users. :-)

---

### Post by gladys emmanuel on 2010-06-24
> **KdotJ said:**
> Hello there and welcome.
 
Many people will tell you its a good idea ...
 
Many thanks for the quick answer. Never thought of doing that, I'll try it later when I get home.
 
 
Cheers

---

### Post by snip3r8 on 2010-06-24
you also have to have the power cable attached to the HDD not just the IDE ribbon.

---

### Post by snip3r8 on 2010-06-24
> **Nightstrike2009 said:**
> 
[COLOR=SeaGreen]Downloadable Ubuntu 10.04 Manual:[/COLOR][http://ubuntu-manual.org/](http://ubuntu-manual.org/)
  

Does this manual include how to install damn Nvidia drivers?

---

### Post by Nightstrike2009 on 2010-06-24
Hello snip3r8,

> **By nightstrike2009:**The only other things of note are to connect the power cable and the data cable (look the same as you installed drive and should only fit one way around) and screw to the case by aligning the 4 screws in the holes already in the tower units insides.

(Too be fair, I may of added that later has I thought of missing info.)

> **By snip3r8:**Does this manual include how to install damn Nvidia drivers?

In ubuntu 10.04 it just detects you choose install drivers, it downloads from net and thats it, you would have to search forums for 9.10 how to but I think if you select "Hardware Drivers" from the Top ubuntu menu it should do the same thing. (I originally wrote an how-to for that to install from .deb (on a geforce 6600), but thats a pain, the new way or terminal command installation is easier). I use an ATI card now so can't help other than that.

---

### Post by eriktheblu on 2010-06-24
> **gladys emmanuel said:**
> Do I want the jumper on the drive as Master or slave (or something else)?Typically you'll want it set as "Cable Select".

> What do I then need to do to get it so that the computer will recognise the drive?Most often, nothing at all
 
> Should I then partition the drive or will Ubuntu do that for me?The Ubuntu install has some pre-defined partitioning schemes, or you can customize it with the install CD.
 
Once you install, you probably want to go into your BIOS to set the new hard drive above the old in the boot priority. If it is not first, you might not be able to boot to Ubuntu.

---

### Post by snip3r8 on 2010-06-24
> **Nightstrike2009 said:**
> Hello snip3r8,



(Too be fair, I may of added that later has I thought of missing info.)



In ubuntu 10.04 it just detects you choose install drivers, it downloads from net and thats it, you would have to search forums for 9.10 how to but I think if you select "Hardware Drivers" from the Top ubuntu menu it should do the same thing. (I originally wrote an how-to for that to install from .deb (on a geforce 6600), but thats a pain, the new way or terminal command installation is easier). I use an ATI card now so can't help other than that.

My problem is the terminal way.it says it doesnt like the kernel and a lot of other things.

My apologies to the starter of this thread for going off topic

---

### Post by KdotJ on 2010-06-25
Nightstrike2009, thanks for clearing that up lol. I thought you were able to connect the windows drive after you have booted into windows and the sudo update-grub lol

Nonetheless I learnt something new so thank you lol

---

### Post by gladys emmanuel on 2010-06-27
Thanks for the advice. Had some spare time last night so gave it all a go. Disconnected the Windows drive and installed Ubuntu. Went on no problem but on reboot the drive was not visible.

After much playing about, I realised that having the drive on the same ribbon cable as the CD Rom was causing a problem. Connected the drive to the old windows cable, rebooted and it all works fine now. Haven't got dual boot but there's not a great deal that I need off the windows drive.

Just need to have a trawl around the forum now for a virus checker and what not.

Thanks all

G

---

### Post by Nightstrike2009 on 2010-06-29
> **by gladys emmanuel:**After much playing about, I realised that having the drive on the same ribbon cable as the CD Rom was causing a problem. Connected the drive to the old windows cable, rebooted and it all works fine now. Haven't got dual boot but there's not a great deal that I need off the windows drive.

sounds like you may have two masters, or two slaves on same cable. Try setting cd jumper to Slave and Hardisk jumper to master if on same cable.

for anti virus try:

sudo apt-get clamtk

Clamtk (or clamav if you don't want a GUI) the best virus checker on ubuntu and opensource has to be run manually though (It doesn't do background checks) best not to run on "Filesystem" due to "false positives" (Assumed Viruses that aren't)

to update antivirus signatures you have to type in terminal:

sudo freshclam

hope that helps :-)

> **By KdotJ:** Nightstrike2009, thanks for clearing that up lol. I thought you were able to connect the windows drive after you have booted into windows and the sudo update-grub lol

sudo update-grub

Sounds like it could work to but if their both connected, ubuntu setup usually picks it up automatically removing the need for disconnection. Your theory is sound and could work, but I just do things a different way. :-)

PS: The *sudo update-grub* command updates the bootloader (grub) with new information about connected hardisks for the new users out there.

---


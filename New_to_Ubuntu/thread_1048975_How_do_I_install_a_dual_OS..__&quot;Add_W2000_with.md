---
title: "How do I install a dual OS..  &quot;Add W2000 with Ubuntu&quot;..?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-01-24
Running a Compaq Presario, 75-gig hd, 1-gig Ram...

I just got into Ubuntu less than a week ago... I like it...  It's a "breath of fresh" not having to see microslop's logos on every screen.. makes a feel like I finally removed an scratchy itchy stinky collar...  
All I see on the screen with Ubuntu is a clean computer OS desktop, and my name, saying "This is My Computer!"...

I find that Gimp isn't what I need to do pix edits.. it's too "something?".
I prefer "Photo Plus-8"..  So it seems I've got-to install W2000 on this hd, with Ubuntu, so I'll be able to do pix edits properly, and fast... Gimp is a big pain, in trying to get multipix options to show, and it to save edits...  Are there any other Linux pix-editors?..

Can I install W2000 on the same hd, with Ubuntu already on the hd as one big partition?..  Or is it better to run 2 hd's..?
(I'm hoping I don't have to start again with W2000, format, split the partition, then add Ubuntu again)... 

Plus, when W2000 & Ubuntu are on the same hd how do you change to each..?  How would I load edited-pix from W2000 to Ubuntu..?  Would be nice if there was a PhotoPlus-8 for Ubuntu-804...

---

### Post by jimmy the saint on 2009-01-24
get virtual box from synaptic
System>administration>synaptic package manager

use it to create a virtual machine and install windows on it.

---

### Post by Michael.Godawski on 2009-01-24
hi,

there is a tool called Wine. It can run windows-esque applications.
Just try it out first before installing a whole new operating system.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Then just right click onto the .exe of the setup of Photo Plus and Wine should install the software.

If you need more help or have some questions just ask.

---

### Post by DonaldJ on 2009-01-24
HotDam! This Linux gets better and better by the minute...  Thanks!..

I hopes it works...

---

### Post by DonaldJ on 2009-01-24
I installed Wine...  Then put the PhotoPlus CD in the slot..  and nothin'..?

Seems Wine is for easy-switching from Windows to Linux..?
Seems I still need to install Windows..  "in a "virtual", or go back to square-one..?  Ummm..? :-k


Umm..? :-k



Umm..? :-k 



Oyie!.. :neutral:

---

### Post by SunnyRabbiera on 2009-01-24
Just dual boot, but I would take caution and back up your data first.
Get CD's, get an external, whatever works for you.

---

### Post by carml on 2009-01-24
Wine is a program that lets Windows programs run under Linux,like they were on Windows,it is useful to use MS Windows software without rebooting your machine if you have a dual boot.
A virtual machine is a machine created by software like Virtualbox,it let you install and use any OS supported by the virtualization software.
When you use a virtual machine,the OS installed there thinks it's running on a real machine,so you can install and do everything you want to,but keep in mind that a virtual machine will never have the same performances of the real machine where is running on.
If you want to use at 100% your PC(e.g. you want to use any software like videogames or software for video-editing),I suggest you to use a dual boot machine,and so the better idea will be to install Windows and Ubuntu on different hard disk.;)
If you need more explanations let us konw it.:D

---

### Post by DonaldJ on 2009-01-24
OK, some of it worked.. I used Wine to install PhotoPlus into Ubuntu-804..  but PP8's image browser doesn't bring up any pix from any of the pix files in Ubuntu..?  And the buttons in PP8's tools are dead... Seems it needs a lot more done to fully connect to the Ubuntu system..?  Seems there must be a special pix-bridge package(s), not yet in this machine, between Ubuntu and PP8..?

---

### Post by SunnyRabbiera on 2009-01-24
thats the problem with proprietary formats of course.

---

### Post by DonaldJ on 2009-01-24
So what packages are there, out there in Linux-land, that made a few stubborn windows software buttons work in Linux..?  Maybe if I add those old packages to this OS, PP8 might work..?

Would it help if I installed PP8 over itself a couple more times..?

It would be nice if I could make PP8 connect to Gimp's coding.. but I suspect that would be like trying to create canine-cats and orngapples...

Somewhere in the Linux-world of experimentation someone has probably written what's needed to make PP8 work in Ubuntu...

---

### Post by eriqjaffe on 2009-01-24
> **DonaldJ said:**
> So what packages are there, out there in Linux-land, that made a few stubborn windows software buttons work in Linux..?  Maybe if I add those old packages to this OS, PP8 might work..?

Would it help if I installed PP8 over itself a couple more times..?

It would be nice if I could make PP8 connect to Gimp's coding.. but I suspect that would be like trying to create canine-cats and orngapples...

Somewhere in the Linux-world of experimentation someone has probably written what's needed to make PP8 work in Ubuntu...Not all Windows programs work through Wine, that's just the way it is.

A good place to start with that is the [Wine Application Database](http://appdb.winehq.org/) to check to see how well a given program works.

There's no entry for PhotoPlus 8, but there is an entry for PhotoPlus 11.  If your version is a few revisions old, there's less of a chance that it's been tested with Wine.

As far as installing W2K, you can't do it on the same partition, but you can do it on the same hard drive if you partition it, although it's far easier to install Windows first and Ubuntu second than the other way around.  It's possible, though, there are plenty of forum posts about it.

---

### Post by DonaldJ on 2009-01-24
Oh Thankyou so much, honorable eriqjaffe..      
PP8 is working now..  oh sigh & yay...  
I've got a lot of photo-work to do now...

This Linux community is sure wise...

---

### Post by DonaldJ on 2009-01-25
I found that parts of Gimp come up after I've been running PP8 for a few minutes..  so I uninstalled Gimp, and now PP8 works properly, and faster...

It seems that if you've installed similar softwares that duplicate processes and tasks, they might conflict, resulting in a slower machine with various strange glitches...  To speed-up the OS, my plan is to remove everything that seems to be a duplicate of another software, keeping the best one...  Like I'm running SeaMonkey.., so I'll time SeaMonkey's responses, then dump the other browsers, reboot, then test SeaMonkey's responses to commands...  oops!..

---

### Post by DonaldJ on 2009-01-27
Is there a way to strip-down Gimp, to only: Quick pix browser (like PP8), Crop, Brush, Smudge, Size, View, and Save..?
I don't use all the other junk...
I tried uninstalling Gimp, but that damaged the OS...
I tried Wine & PP8, but bits of Gimp pop-up in PP8, and mess it up...
I surfed for another Linux pix-editor...  All I found were pix-handlers...

Gimp is like having a whole grocery-store dumped on your head, when all you asked for was toothpicks...
It's like asking for an "A", and getting a multi-volume encyclopedia tossed at you...  Is there gonna-be a light-weight high-speed Gimp.. for us not so technical little critters..?  
Maybe you could make a basic solid little system, that the user adds preferred options too..?   "Mini-Gimp"...

---

### Post by Roadbloc on 2009-01-27
You can either: 
1. install wine (it will be available from add/remove)

2. Get partition logic at [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/) (it worked for me) it lets you control your partitons off a bootable cd-rom.

3. Remove ubuntu completly, install win 2k and then install ubuntu again within windows (although i am not sure whether it is possible through win 2k, but definantly xp.)

4. If you want to get games running, there is nothing better than crossover games [http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/) or just put up with wine.

good look :D

---

### Post by DonaldJ on 2009-01-27
Thanks Roadbloc.. that's what I'm gonna do to the 80-gig hd tonight... which is probably a 90-gig in Ubuntu..?

I've had a tiny experience with Wine, installing PhotoPlus8...

I've already destroyed two Ubuntu installs, seriously messing-up in them...  Ubuntu sure is fragile...

Any ideas why the 35-gig hd, in Windows, shows as a 41-gig hd in Ubuntu..?
Are Linux-gigs smaller than Windows-gigs..? like liters are smaller than quarts...

What's the easiest way to format a drive for Linux?..  
I find that formating with "the W98 CD and boot-floppy" seems to give me the quickest cleanest format, and it's in "Fat" too... It destroys all of microsoft's security remnants in the hd...  Is there a better way?..  Is there a linux bootable image CD bit of software that totally wipes a hd, sending everything on it back to zeros..?  

After messing with OS's on top of OS's in trying to get windows stuff working with Ubuntu, I've learned the Gimp does much finer work than PP8, so PP8 is history.. and windows stuff just wrecks Linux.. so I've dumped the idea of adding anything windows to the hd... It's better this way.. less grief.. less cussing.. less headache..  That's it!  Windows is out of my life!..

---

### Post by Roadbloc on 2009-03-23
> What's the easiest way to format a drive for Linux?..  
I find that formating with "the W98 CD and boot-floppy" seems to give me the quickest cleanest format, and it's in "Fat" too... It destroys all of microsoft's security remnants in the hd...  Is there a better way?..  Is there a linux bootable image CD bit of software that totally wipes a hd, sending everything on it back to zeros..?  


i tend to find either Killdisk [http://www.killdisk.com/](http://www.killdisk.com/) or using the xp formatter on the xp install disk works. Good luck ;)

---


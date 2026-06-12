---
title: "Installed new Kernel, but Can't Log On to Old One"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by jackrednur on 2009-09-08
I am a noob, so forgive me but I'm at a loss of what I should do.  I recently installed Jaunty 9.04 on cd, keeping my old partition/kernel....where all my files are at.  Unfortunately, I installed Jaunty because the graphics interface is not recognized on my old kernel but i NEED to get that working as I have all my files on it.  When I boot into that kernel, it says "Failed to start X server.  using config file: "/etc/x11/xorg.conf" (EE) No Devices detected   Fatal Screen error:  no screens found        f'      

Now, does anyone know how I can install the drivers needed for my graphics card to work with my old kernel?  It's working fine on Jaunty 9.04, hence why I'm able to post this thread.  I know I have a Geforce 6200 card, and I think that old kernel assumes I have an ATI Radeon 9200 pro or something.  Maybe this is the reason I can't get into my GUI?  If anyone knows of any code or anything I can type into terminal at boot to get that particular kernel up and running again, I would be MOST appreciative!!

---

### Post by jsoellner on 2009-09-08
Hi

If I understand you correctly, you have installed 9.04 on a new partition on a local hard disk?

If you can boot into the new installation ok, you should be able to go to places-->Computer and mount the old partition. You can then browse for your files and copy them accross to your new partition that contains your new install.

Hope I've understood correctly, if not let me know.

---

### Post by jackrednur on 2009-09-08
Thank you, yes...I see that now, and I've mounted it.  Alas, none of my files are in there, and that's the major partition...150 gigs.  I'm on a 2 gig partition now, the only other one I have.  Does this mean I formatted my hard-drive by simply upgrading to Jaunty 9.04 or what?  I was careful not to install it to the ENTIRE hard-drive, that's why I assumed I saved the 150 gig partition for the old kernel...to keep all my files.  Needless to say I'm freaking out about the possible loss of my files...any advice?  

Thanks for your help.


Edit:  Okay, I found my files, as I obviously didn't format my hard-drive (I'm a noob, but I'm not an idiot)....still, I would like to boot up in my 150 gig partition as opposed to the 2 gig one, is that possible?  If so, how would I go about it?  The only options are the 2 gig one in Grub at boot or the other one I'm having graphical problems with, as per the original post.

---

### Post by bodhi.zazen on 2009-09-08
First of all STOP using your hard drive.

Boot a live CD and start gparted, let's look at your partitions.

---

### Post by jackrednur on 2009-09-08
Wow, okay so anyway...GRUB had the partition I needed to start on, so thanks everyone for your help.  All I needed was a bit of clarity and, perhaps, a keener sense of observation.

---


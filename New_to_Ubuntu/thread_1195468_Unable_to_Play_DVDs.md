---
title: "Unable to Play DVDs"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by mjnuss on 2009-06-23
Hi, I just recently made the switch to Ubuntu and I'm having troubles playing a DVD movie on my laptop.  I get the error "Could not open location; you might not have permission to open the file." when trying to access the disc using Totem Movie Player.  So I openned the Terminal and type in

ls -l /media

to get this:
> 
total 2
lrwxrwxrwx 1 root       root         6 2005-02-15 23:54 cdrom -> cdrom0
dr-xr-xr-x 3 4294967295 4294967295 184 1969-12-31 19:00 cdrom0
 

I don't know where to go from here.  I figured I had to change the ownership of cdrom0 so I used "sudo chown michael cdrom0" but to no avail.

Please help me oh great Ubuntu Forum gods!

---

### Post by starcraft.man on 2009-06-23
[Link]("https://help.ubuntu.com/community/Medibuntu")

Your missing libdvdcss2 file to decrypt protected movies. Just go here, read how to add the repos and then just install the package by your favorite means terminal or gui. Ubuntu should display something more useful like "can't play this encrypted DVD".

---

### Post by 73ckn797 on 2009-06-23
The link to Medibuntu is your best solution. Follow the instructions and you will be ready to go.

---

### Post by mjnuss on 2009-06-23
Thank you starcraft.man for your help, although it didn't seem to work.

I followed your link and installed via terminal.  After completion I tried openning the movie and received the same error as before.  I then checked to see if I had indeed installed it correctly:

> michael@Michael-laptop2:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


I oppened up the folder and clicked the second .VOB and it began to play something entirely unrecognizable and without sound.

Then I tried installing the non-native format package and still no luck.

---

### Post by SunnyRabbiera on 2009-06-23
This might be the same totem issue I bumped into, I suggest going to system > administration > synaptic package manager.
With synaptic I would install totem-xine

The default totem had an issue with me while playing DVD's, totem-xine fixed the issue for me.

Here is a good start for any new user wanting to know how to install apps in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by starcraft.man on 2009-06-23
> **mjnuss said:**
> Thank you starcraft.man for your help, although it didn't seem to work.

I followed your link and installed via terminal.  After completion I tried openning the movie and received the same error as before.  I then checked to see if I had indeed installed it correctly:



I oppened up the folder and clicked the second .VOB and it began to play something entirely unrecognizable and without sound.

Then I tried installing the non-native format package and still no luck.

I was sure that was your only problem. The non-native formats package is mostly for wmv and similar windows formats.

Just to be certain, have you installed the ubuntu-restricted-extras package? And secondly, install VLC and try that. I'm not a big user of totem, VLC always works. If your still having trouble after then something is afoot!

Edit: Really sunny? I don't use totem to play much but never had trouble using it/gstreamer to play DVDs homemade or bought before...

---

### Post by SunnyRabbiera on 2009-06-23
> **starcraft.man said:**
> I was sure that was your only problem. The non-native formats package is mostly for wmv and similar windows formats.

Just to be certain, have you installed the ubuntu-restricted-extras package? And secondly, install VLC and try that. I'm not a big user of totem, VLC always works. If your still having trouble after then something is afoot!

Edit: Really sunny? I don't use totem to play much but never had trouble using it/gstreamer to play DVDs homemade or bought before...

To me gstreamer has been a mess, though it is getting better as time passes.

---

### Post by mjnuss on 2009-06-23
I switched to VLC, crossed my fingers and it worked no questions asked!  I can finally watch the Blues Brothers! 

Thank you sunny and starcraftman for your help.  Although I couldn't get Totem to work, I feel like I learned a little bit on bout how to navigate ubuntu better.  Someday i'l be a guru..someday haha

---

### Post by 3rdalbum on 2009-06-23
(suggestion already used successfully)

---

### Post by starcraft.man on 2009-06-23
> **mjnuss said:**
> I switched to VLC, crossed my fingers and it worked no questions asked!  I can finally watch the Blues Brothers! 

Thank you sunny and starcraftman for your help.  Although I couldn't get Totem to work, I feel like I learned a little bit on bout how to navigate ubuntu better.  Someday i'l be a guru..someday haha

OH MAN! That was a great movie!

May the great Belushi rest in peace. He will always be missed.

---

### Post by SunnyRabbiera on 2009-06-23
> **mjnuss said:**
> I switched to VLC, crossed my fingers and it worked no questions asked!  I can finally watch the Blues Brothers! 

Thank you sunny and starcraftman for your help.  Although I couldn't get Totem to work, I feel like I learned a little bit on bout how to navigate ubuntu better.  Someday i'l be a guru..someday haha

VLC does have a great rate of success, its no doubt the best video player for linux right now alongside Mplayer.
Xine is my personal favorite though

---

### Post by mjnuss on 2009-06-23
forgot to mark as solved.  Hopefully I'm doing this right.

---


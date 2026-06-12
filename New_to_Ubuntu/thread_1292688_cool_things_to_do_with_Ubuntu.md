---
title: "cool things to do with Ubuntu"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by nandan on 2009-10-16
Hello

Have been using Ubuntu for more than a year now and have been fairly happy with it.

Was wondering if experienced people out here could start a series like "Cool things to do with Ubuntu", which will outline how users, especially newbies, can do stuff that takes ages/is very complicated with other OSes (I'm looking at you, M$)..e.g. something as basic as changing themes is a snap, downloading and installing themes is very easy, themes generally don't slow down/crash your system, installing programs is very easy etc..am giving well-known benefits here, experts would be able to give better, in-depth tips and ideas.

Tried to search for this type of thread, but did not find it. I feel this could go a long way in helping newbies (which includes me, still!) try and experiment and be amazed with the ease of the system.

---

### Post by ankspo71 on 2009-10-16
Hi,

Here's some good links.
[http://www.davehayes.org/2009/01/16/7-cool-things-to-do-with-linux](http://www.davehayes.org/2009/01/16/7-cool-things-to-do-with-linux)
[http://www.handlewithlinux.com/10-cool-things-you-can-do-with-windows-and-not-with-linux](http://www.handlewithlinux.com/10-cool-things-you-can-do-with-windows-and-not-with-linux)

Looking through the Tutorials and Tips section of this forum gives me some ideas too.
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

James

---

### Post by lovinglinux on 2009-10-16
One thing that I like about Ubuntu is that you can download and install all your software at once. So if you want to re-install Ubuntu, it makes really easy to get your system up and running just like before. 

To do that you can go to Synaptic, select "File >> Save Markings As", then tick the option "Save full state, not only markings" and save it. To re-install, select 'Read Markings". It will download/install all packages and also remove those previously removed before saving the markings.

You can also do that with:


```
dpkg --get-selections > ~/my-packages
```  (to save)


```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
``` (to read)

...or you can use my [Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153/) extension for Firefox.

---

### Post by Sir Jasper on 2009-10-16
Hi lovinglinux,

Thank you. Your suggestions are supercool and I have installed your Firefox add-on.

I do not want to hijack this thread and I hope my question below is acceptable.

However, I do not entirely understand since if I/we do not save our installed  program details externally then will it be available upon a system re-installation?

My regards

---

### Post by lovinglinux on 2009-10-16
> **Sir Jasper said:**
> Hi lovinglinux,

Thank you. Your suggestions are supercool and I have installed your Firefox add-on.

I do not want to hijack this thread and I hope my question below is acceptable.

However, I do not entirely understand since if I/we do not save our installed  program details externally then will it be available upon a system re-installation?

My regards

Every time you create a backup, it saves the current markings to the extension folder and add the file path to the extension database. So if you have a separate partition for home, then all you have to do is launch Firefox, select one backup from the list and re-install it. You can also export it to your desktop then import it back, then install.

If you need further assistance, post at [http://ubuntuforums.org/showthread.php?t=1216679](http://ubuntuforums.org/showthread.php?t=1216679)

The next version (see screenshot) has a simpler interface and does not depend on extra applications, but I'm still struggling with a bug that makes Firefox use 100% of the CPU when you close the extension sidebar.

---

### Post by titan_90 on 2009-10-16
Thanks for the info lovinglinux:P 
I am buying a larger hd next week and will be installing 9.10 on it. Now I don't have to write down all of my programs.

---

### Post by A_M_S on 2009-10-16
Excellent info!

Thank you guys!!

---

### Post by nandan on 2009-10-17
Great! if we get more such replies, this thread may actually help convincing peope to move from proprietary OSes to ubuntu...

---

### Post by Big_Croc7 on 2009-10-17
STOP!

Read this:
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

[refers to a post that's since been deleted]

---

### Post by ankspo71 on 2009-10-17
@ Big_Croc7, Thanks for reporting the bad code.

---

### Post by ranch hand on 2009-10-17
This isn't real handy but I think it is cool.

Being in a remote area we have to do our own repair work or haul boxes about 100 miles over poor dirt roads to get service.  I run Linux so I am an expert - in the minds of the neighbors.  If they have MS problems they can't fix they call me.

Data recovery is a common need.  I have an external enclosure with Jaunty on it.  Plug it in and change their bios to boot from there and I can get to their files.  Assuming that I can get their box back up (I do have a rescue disk for MS too) I like to have them try and get into my files.  Seeing that I am on ext4 there is no way.

Makes them stop and think about their "security" when I can just walk through their files.

---

### Post by anewguy on 2009-10-17
I'll go at a slightly different tack - something that was fun for me to do with Linux.

CVS pharmacies sell, or at least used to sell, a 1-time use digital camcorder that you turned back in to get a dvd of what you recorded.  There are sites on the net the explain hacking these cameras (actually quite simple) so that you can use them as many times as you want without ever returning them - just plug in to USB and download the videos.  The same goes for their 1-time use digital still cameras.  I won't go into the hacking itself, as that is off-topic, but using GCC and GTK, I was able to port the code for these into a single program and have it work in both Windows and Linux.  To me, that was fun, a learning experience, and the best part - outside of the initial cost of the cameras (under $25) - everything was free!

That's just one of things I find as a cool thing to do with Ubuntu.  Obviously there are the countless benefits of free open-source software, etc., as documented all too well.  

Another cool thing - you can become involved in any part of working with the actual OS or it's tools at whatever level you want.  You can join a team working on parts of the kernel, or working on a new or improved utility, or even something new and useful just from yourself.  Try doing that for Windows - unless you work for Microsoft you won't get far (not talking applications here, but the "internals").

Just my weird take on things!!

Dave :)

---


---
title: "Desktop"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by snuggs on 2009-10-08
1 yes i'm a newb (from windows - dual booting vista and ubuntu now)
2 have loved it so far! 
3 have already looked to find solutions for many of my questions so far - these forums are great!
4 i haven't found a solution for this yet... and i'm wondering if i'm looking for a solution when really this is running normally - ha - have nothing to compare it to. 

Ok here's what i'm seeing maybe this is just me, but the sizes of my "windows" (firefox, folders, mail..whatever i open) take up the whole screen...

in preferences i have 15" laptop in options and it seems to be running that fine, but still eveything seems to be large size. excuse my windows talk but like when you have a new install of windows and haven't changed the screen resolution yet. big icons, big writing, everything. 

example to put it into persepective: when i click on "system/preferences" the drop box goes all the way to the bottom of the screen. on tutorials and screen shots online they appear normal taking only part of the top of the screen. 

thoughts? (go easy on me....) haha

thanks!

---

### Post by MelDJ on 2009-10-08
system-preferences-system resolution and then change the resolution?

---

### Post by snuggs on 2009-10-08
> **MelDJ said:**
> system-preferences-system resolution and then change the resolution?
it's at 1280x800 and configured to the 15" screen... that's what i already tried and why i'm at a standstill

---

### Post by wojox on 2009-10-08
Is there anything to activate in System > Admin > Hardware Drivers for graphics?

---

### Post by Chris Edgell on 2009-10-08
I can only tell you that I had a problem with resolution and even though mine was never really solved (not that yours can't be) but I just worked with pressing the       Ctrl  -  and/or Ctrl +  to adjust the size of stuff. 

Some screens it didn't adjust the size at all, but it worked on these forum screens and it worked in email. 

I hope this does some work for you as you try to get a better resolution to your problem...no pun intended although it does work...

---

### Post by abelbrito on 2009-10-08
you probably have to update your graphics driver.

---

### Post by snuggs on 2009-10-08
> **wojox said:**
> Is there anything to activate in System > Admin > Hardware Drivers for graphics?

no.. when i pull that up I only see the networking hardware

I have Mobile Intel(R) 965 Express Chipset Family (i think that's my graphics card) lol 

do i have to install drivers?

---

### Post by amsum on 2009-10-08
is this a fresh install? if yes, then did you download all the updates? I had this problem with fresh install but after downloading all the updates and setting the right resolution I got it working.

---

### Post by snuggs on 2009-10-08
> **amsum said:**
> is this a fresh install? if yes, then did you download all the updates? I had this problem with fresh install but after downloading all the updates and setting the right resolution I got it working.

Installed and updated. the only thing i've added after that is CCSM, Thunderbird, and dropbox.

i just checked if i have to install the latest driver by
[B]sudo apt-get install xserver-xorg-video-intel

[/B]but it says that everything is up to date.. other ideas? or is the screen "size" i have just "normal", should the menu screens go all the way down the page?

---

### Post by starcannon on 2009-10-08
I found this post [http://ubuntuforums.org/showpost.php?p=3530851&postcount=10](http://ubuntuforums.org/showpost.php?p=3530851&postcount=10)
Not sure if that will help fix you up or not; all of my intel gpu's have "just worked out of the box".

GL

---

### Post by CharlesA on 2009-10-08
You could try envy to install graphics drivers, but other then that, I'm not quite sure what the deal is.

If you resize the windows manually, so they stay the same size when you reopen them?

---

### Post by snuggs on 2009-10-08
> **starcannon said:**
> I found this post [http://ubuntuforums.org/showpost.php?p=3530851&postcount=10](http://ubuntuforums.org/showpost.php?p=3530851&postcount=10)
Not sure if that will help fix you up or not; all of my intel gpu's have "just worked out of the box".

GL

awesome... i'll give this a try... and if you can help me decipher what to do.. remember be easy, mr gates has had my mindshare for quite a long time... 

# means root user right? so i use "sudo" in the terminal? or when i see things like this on the forums do i just copy/paste the whole thing? 
< laughing at my green-ness

Hi, i was the same problem, i was cannot get 1680/1050 on my flat panel, I have g956 graphics. I install 915Resolution an change some values, try next:


#apt-get install xserver-xorg-video-intel
#apt-get install 915resolution
#gedit /etc/default/915resolution

mode=3c
XRESO=1280
YRESO=800
BIT=32

#reboot

Thats Work so fine to me

Regards

---

### Post by CharlesA on 2009-10-08
In that case # means sudo, yes.

Good luck!

---

### Post by snuggs on 2009-10-08
I tried the above and received this... 

Package 915resolution is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 915resolution has no installation candidate

...

---

### Post by snuggs on 2009-10-09
i think this might me just me... i don't know... but i'm learning to work around the size thing... maybe i'll catch something as i get deeper into this.

---


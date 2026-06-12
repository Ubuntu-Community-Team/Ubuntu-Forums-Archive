---
title: "Ubuntu 9.10 - several issues"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by anigodin on 2010-04-01
Hello everybody,

This one is going to be a bit long. 
Up until a few weeks ago I was working on unbuntu 8.04 LTS and all was fine. I had mac4lin installed (that thing that makes the computer look like a mac). the problems stared when one day there was an update to the avant dock and after that the dock stopped working. I tried to fix it but to no avail. so a friend (the guy who introduced me to Linux :-)) told me I should update the system to ubuntu 9.04 or 9.10. so I did.

After the update-upgrade trouble started: first, the mac4lin was no longer working properly, so I change the theme. second, the visual effect did not work. after some reading I understood that my graphic card, an on-board card, was to weak. so I got another one - nVidia Quatro FX 3400. it took me a few day to get it working and it work fine (more or less), until this morning.

Now the fun part - the problems. all this problems appeared after I switched to ubuntu 9.10:

1. Graphic card problem - I installed some updates yesterday and this morning when I turn the computer on - no xorg. I get a black screen with lots of text and that's it. It happened last time I installed some updates but then I restarted the computer in recovery mode, run the 'fix broken packages' and it was solved but itself. this time it's not working. I have no idea how to solve this and if this happens every time I install updates I'll go nuts..

2. Audio issue - every time I restart the computer - the sound it muted. I tried to fix it using some fixes I found here but it's not working. also, my skype have no sound when the sound is NOT muted and one day when I changed the audio source it worked for two seconds and stopped and I lost all sound completely.. 
I tried to install a newer version of skype (now I have v2.0) but it failed.
I'm not sure but it looks like I have a permission problem here that prevent from any changes I do in my user to be saved. why I think so? because of this -->

3. Time set - we switched to summer time here (moved to clock forward one hour) and I tried to re-set the clock but I cant save the new setting - I was told I have no permission to do that.

4. When the graphic card did work, the visual effect still wouldn't start, no matter what I tried. also, the screen saver doesn't work all the time.

5. Updates - until I upgraded to 9.10 I was getting updated notifications all the time. now, if I don't check for updates, I wont know there are any. also, on the first day I worked on 9.10 I saw in the update window that there's a system upgrade available for ubuntu 10.04 beta. now it's gone.

6. I have another computer connected to the TV with mythbuntu installed. before I upgraded to 9.10 I was able to remotely control the mytbuntu computer, but now it's just wont connect.

These are all small problems but they drive me crazy and I have a feeling I'll have no choice but to re-install the all system from scratch, something I really don't want to do. I think there a permission problem that prevent me from fixing small problems, but I'm not sure. 

Any idea what can I do (beside re-installing)?
Many thanks in advance!

---

### Post by NightwishFan on 2010-04-01
I would recommed a reinstallation personally... I never install mac4lin as root or use the script I just add the componants manually. (If that is what you did)

In newer versions Ubuntu switched to using DKMS for nvidia drivers. Perhaps disable Nvidia drivers, then reboot and reenable them in the the device manager.

Setting time system wide requires root access, perhaps you are missing policy? Try this command:
```
sudo apt-get --install-recommends install ubuntu-desktop
```

In System -> Administration -> Software Sources check to see if you have any of the sources enabled and if it is set to check for updates daily.

I am not sure about the TV issue.

---

### Post by anigodin on 2010-04-01
Thank you for the reply.

I did installed the mac4lin as a complete package. you think that might cause problems with newer versions of ubuntu?

As for the graphic card, I cant get ubuntu to start X-session.. all I can do is start it in recovery mode and I'm not sure how to disable pacakages from a console. :-)

---

### Post by NightwishFan on 2010-04-01
To remove packages drop to root console and run:
```
aptitude remove *packagename*
```

To fix X, no idea, what is your card/driver? If you have nvidia run:
```
jockey-text -l
```

Then run:
```
jockey-text -d xorg:nvidia-***
```
replace *** with your version

---

### Post by anigodin on 2010-04-02
Thank you again.

After talking to my friend (the guy I wrote about), I decided to re-install the system.

---

### Post by lidex on 2010-04-02
You updated from 8.04 to 9.10 directly? That would cause problems in itself. If you want to *_upgrade_* the path should be 8.04 -> 8.10 -> 9.04 -> 9.10

Easier just to do a new install.

---


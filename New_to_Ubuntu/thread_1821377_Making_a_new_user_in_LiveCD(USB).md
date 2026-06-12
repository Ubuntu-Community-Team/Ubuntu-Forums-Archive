---
title: "Making a new user in LiveCD(USB)?"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by Astroe on 2011-08-09
Ok, so I finally decided to give Linux another shot, but I'm not ready to make the commitment that is the dual-boot, so I installed Ubuntu 10.04 onto a USB stick and added a persistent file system.

Thing is, I don't like it when it boots to "Live Session User" so I went System>Administration>Login Screen and made it ask me who I want to be today, and that's all well and good, but when I create a user that isn't root (And even when I make one that is) I get an error message when I try to login as the new user.

I didn't have the presence of mind to write it down, and I don't really want to induce the problem again as I am scared of error messages.
But it said something about ICEAuthority and then Nautilus said that it didn't have the right permissions to create /User/Astroe/Desktop, and that I should give it said permissions.

So my questions is this, is there a problem with not logging in as Live Session User in a persistent USB install or am I being re-tarded?
Also, regardless of aforementioned tarded-ness, how do I fix it?

---

### Post by beew on 2011-08-09
Yes, there is a difference between a real install and a liveusb with persistence and I think the liveusb only allows live session user (what do you expect? :)) Besides, a liveusb is limited in size and is slow and can't handle multi-tasking well.

If you want to truly try out Linux without dual booting I would suggest you find an external drive and do a full install of Ubuntu in it. Apart from boot time (that would depend on your BIOS for example) it is as fast as an install in the internal drive and it supports everything that you can do with a "real install" because it is a real install.

---

### Post by Astroe on 2011-08-09
Unfortunately I don't have the funds to go with an external drive. I do have a few old internal drives (512MB and 1GB) if there is some easy (and cheap) way to use an internal drive without it physically being in the computer that might work.

But otherwise I'm gonna have to stick to the LiveUSB. It's too hard to uninstall and re-install one side of a dual-boot every time I screw the system up.

And I did use the search bar before I posted this and I found another post where somebody was able to log into a different user on his stick..

---

### Post by beew on 2011-08-09
An old internal drive is fine. I have installed Ubuntu in a 4G old internal drive used as an external and it was very fast comparing to a liveusb. But 1 G is too small.

---

### Post by jtarin on 2011-08-09
> **Astroe said:**
>  It's too hard to uninstall and re-install one side of a dual-boot every time I screw the system up.
It is easier than you think to setup if you do it right the first time you will never have to do anything but reinstall the one side....and you can do that from an image of the install so it will be an exact duplicate of your installed system as you have it set up.......before the screw-up.

---

### Post by Astroe on 2011-08-09
See and doing something like that has been a goal of mine for a while. Whenever I ask the question how to make an image of my current install with everything tweaked how I like it, no one seems to know.
But then I haven't put much effort into finding that out myself so I don't blame you. I blame the Nazis. If it weren't for them we wouldn't be in this mess in the first place.

But I digress. I wish I didn't have to choose. I want Windows and Ubuntu at the same time... :(

---

### Post by magic8ball on 2011-08-09
I just used Clonezilla for the first time as part of resizing and reinstalling Ubuntu 10.04 on my dual-boot (Ubuntu/XP) system.  I used it to image the entire drive, but I seem to remember options for just doing partitions.  All my stuff went well, so I didn't have to try restoring and can't attest to how well that works.

---

### Post by fslezak on 2011-08-09
Ok. I've been using persistent for a VERY LONG time. 

Step 1: Use the terminal and enter this command:
```
sudo adduser <username>
```It will walk you through the new user process.

Step 2: Press Alt+F2 and run this:
```
gksu users-admin
```Configure the new user.

Step 3:Logout, and login as user.

Step 4: Report back to us on if it worked.

Some tips:

DO use an external storage media that is 2GB or larger.
DO NOT remove the user ubuntu.
DO NOT run too many apps at once.
DO NOT have more than two workspaces.
[COLOR=Red][COLOR=Black]>>>>[/COLOR] If you can, install to the drive instead of using a persistent. [COLOR=Black]<<<<[/COLOR]
[/COLOR]

---


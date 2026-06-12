---
title: "Royally Screwed Up Ubuntu"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by donnagarnet on 2011-08-02
My desktop was set up to dual boot 11.04 & Vista.

I was getting messages that I had little space left on my hard drive, so I decided to delete old ubuntu versions using easybcd.  I looked at several YouTube videos about easybcd & was confident I could do what I wanted to.

Instead of getting rid of old versions, easybcd got rid of everything, all versions of Ubuntu & Windows Vista.

After the customary hand-wringing & teeth-gnashing, I started to reinstall everything.  I began with the Vista recovery disks, then tried to install Ubuntu.  I got a message that all the old partitions were still there.  After more web surfing, I figured out how to delete old partitions using Vista's disk management.

I burned 11.04 to a CD, but could not get it installed.  I tired a "free with magazine" disk, but without any success.  I was able to install 10.10, & as soon as that was finished, I got a message inviting me to update to 11.04. 

As soon as the update was finished, I got another message that disappeared before I could write it down.  It said that it didn't seem that I had  the proper hardware to use 11.04, so I should choose "Ubuntu Classic" when booting into it.

Except that "Ubuntu Classic" doesn't appear in the boot menu.  I click on "Ubuntu Generic" (the only version that appears in the menu) & get "Classic" with a 'Linux Identity' button (which I've nevr seen before).

I really liked the Unity Launcher.  Is there any way to get it back?

Thanks so much for your help, kids.:D

---

### Post by gandaran on 2011-08-02
> As soon as the update was finished, I got another message that disappeared before I could write it down. It said that it didn't seem that I had the proper hardware to use 11.04, so I should choose "Ubuntu Classic" when booting into it.

Except that "Ubuntu Classic" doesn't appear in the boot menu. I click on "Ubuntu Generic" (the only version that appears in the menu) & get "Classic" with a 'Linux Identity' button (which I've nevr seen before).
you are probably already using ubuntu classic if you don't have a video card/drivers installed to run unity desktop.
also you don't get "ubuntu classic" in the boot menu, that option you find it only if you log out of you current session then click the login username and look on the bottom panel for unity or ubuntu classic options to login to.
and about easybcd, I think you got the wrong idea about this software, easybcd is for managing boot options not managing partitions.

---

### Post by srisharan on 2011-08-02
If you cant use unity then you can always use unity 2D.Search for it in the software center

---

### Post by gandaran on 2011-08-02
> **srisharan said:**
> If you cant use unity then you can always use unity classic.Search for it in the software center
'unity 2D' not 'unity classic', unity 2D is just like the 3D version but can run on any video card without 3D drivers

---

### Post by kaldor on 2011-08-02
Which graphics card do you have?

Check with:

```
lspci -v
```

Look where it says "VGA compatible controller".

---

### Post by grahammechanical on 2011-08-02
The message that you do not have the hardware to run Unity is a standard message that is used because Ubuntu sticks closely to open source. Therefore it will not install closed source video card drivers. Ubuntu does make it easy for the user to install these closed source drivers.

Use the utility called Additional Drivers to activate the recommended driver. You will get a message saying that the driver is activated but not in use and another message that says no proprietary drivers are in use on this system. Ignore them they are not telling the truth.

After this you reboot and click on your user name and on the bottom panel on the right you will see a menu that has Ubuntu and Ubuntu classic in the list. You will not see Ubuntu 2D unless you have installed Unity 2D through the software centre. Select Ubuntu and when the desktop loads you will have the Unity desktop again.

Regards.

---

### Post by donnagarnet on 2011-08-02
> **gandaran said:**
> and about easybcd, I think you got the wrong idea about this software, easybcd is for managing boot options not managing partitions.

You're right, but I thought I could use it to uninstall Ubuntu & the old partitions & start over without all the old versions (each with it's own partition), then do a clean install of Ubuntu.  That's the way easybcd was used in the vids I watched.

According to the sticker on the tower (along with info about my processor, etc). I have:

NVIDIA GeForce
7100 Graphics.

I had Unity before I tried easybcd (I know, I know...stupid!), & I had no problems with it, so I don't think the graphics card is the problem. While I don't play any graphics-intensive games, I had no trouble with the ones I reinstalled on the Vista side of the partition.

There are other problems, but those are just annoying rather than tragic.  So far.

Thanks for your patience, kids.:D

---

### Post by srisharan on 2011-08-02
> **gandaran said:**
> 'unity 2D' not 'unity classic', unity 2D is just like the 3D version but can run on any video card without 3D drivers

Yes,sorry about that.It is a kind of typo. Didn't read what I wrote after properly

---


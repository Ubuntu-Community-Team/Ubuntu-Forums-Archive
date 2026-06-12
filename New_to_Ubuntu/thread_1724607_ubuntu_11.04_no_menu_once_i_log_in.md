---
title: "ubuntu 11.04 no menu once i log in"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by dagarshali on 2011-04-08
HI,
I upgraded this morning.. I have nvidia ge110m graphics card on my laptop. When i login with the default ubuntu (unity), i don't see any menu at all . All i see is a screen which has the contents of the desktop folder. i am attaching the photo of the desktop for your reference. Any idea as to what might be going on here? I have also attached a picture of nvidia-settings screen.

Regards,
Vishwa

---

### Post by earthpigg on 2011-04-08
right click on the desktop -> create launcher

enter whatever you wish for 'name' and 'gnome-terminal' for 'command'.

now we have an icon that gives us access to a terminal.

if you weren't using unity, i would suggest merely entering the command 'gnome-panel' and seeing how that goes.

however... i've never worked with unity and didn't even know 11.04 was out already! maybe entering 'unity' in the terminal?

---

### Post by madmax75 on 2011-04-08
11.04 is still in Beta, so it is not meant for everyday use, just for testing and finding out bugs.

The stable release comes out at the end of this month. I would wait at least until the middle of May before installing it.

---

### Post by mikewhatever on 2011-04-09
Unity doesn't seem to work with proprietary Nvidia drivers, which is somewhat disturbing, as Natty is already in beta, and there is less then three weeks to go till the release date.

---

### Post by earthpigg on 2011-04-09
> **mikewhatever said:**
> Unity doesn't seem to work with proprietary Nvidia drivers, which is somewhat disturbing, as Natty is already in beta, and there is less then three weeks to go till the release date.

guess i will be sticking with 10.10 until at least the 6th or 7th month of 2011, possibly later, and possibly moving on from ubuntu. ty for heads up.

---

### Post by beew on 2011-04-09
> **earthpigg said:**
> guess i will be sticking with 10.10 until at least the 6th or 7th month of 2011, possibly later, and possibly moving on from ubuntu. ty for heads up.

I see no reason to upgrade from 10.10. Now all the hardware works out of the box and my softwares are cutting edge because I use lots of PPAs. Mav is rock solid and fast as lightning on my box. Why  risk ruining a good thing with the compulsive 6 month upgrade (or even before that like some people with ADD)? Most likely I will keep 10.10 on my main machine til 12.04. It is 10-10 perfect for me. :)

Three weeks to go and 11.04 is still very unstable, wireless still  doesn't work, webcam doesn't work, Compiz still crashes every now and  then.. Unity is still a mess, I am not sure going from 10.10 to 11.04 is  upgrade or downgrade.

I will replace 10.04 with 11.04 on one of my older machine maybe around June and probably replace my 10.10 install on an external drive with 11.04 just for testing and playing with Unity.

---

### Post by Joeb454 on 2011-04-09
> **mikewhatever said:**
> Unity doesn't seem to work with proprietary Nvidia drivers, which is somewhat disturbing, as Natty is already in beta, and there is less then three weeks to go till the release date.

It's been working for me with the proprietary nvidia drivers installed. I have a 9800GT in my desktop, for reference.

@ OP - if you create the terminal launcher, as suggested above, you could try running compiz from the terminal, it almost looks like it's not starting when you login.

---

### Post by mikewhatever on 2011-04-10
Hopefully, it's an isolated issue with only a few affected. 
I've filed a bug report meanwhile.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/756492)

---

### Post by earthpigg on 2011-04-12
identical problem happened to me, with natty beta in virtualbox.

> sudo killall Xorg 

seems to have magically fixed the problem.

---


---
title: "How can I best manage how GRUB2 displays?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by bwallum on 2010-05-14
Hi

I have found the /etc/grub.d files and /etc/default/grub and had some success in changing the background and font size of the GRUB2 menu.

Is there a neat (more user friendly?) utility that enables me to do this without poking about in the files contained in the grub.d folder?

---

### Post by Opti_Rick on 2010-05-14
I've not tried it but there is this...

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by wilee-nilee on 2010-05-14
> **bwallum said:**
> Hi

I have found the /etc/grub.d files and /etc/default/grub and had some success in changing the background and font size of the GRUB2 menu.

Is there a neat (more user friendly?) utility that enables me to do this without poking about in the files contained in the grub.d folder?

What exactly are you trying to do?

---

### Post by bwallum on 2010-05-14
Tried that. It used to be good for grub legacy but is incomplete for grub2. 

The sort of thing I would like to see for example, is how to turn the grub menu on or off simply. I know I can hold down the shift key to show the grub menu but that is not obvious to a non technical user. A simple check box (within Start Up Manager even) would be the sort of interface that a user might expect.

Any other utilities you can think of?

---

### Post by bwallum on 2010-05-14
> **wilee-nilee said:**
> What exactly are you trying to do?

Manage how the grub menu displays in a simple way.

E.g.

Turn the menu on or off at boot time
Change the background pic
Order the list of boot choice at will, e.g. put windows at top and vice versa.
Set delay before booting default.

All the above can be achieved by poking about in files (which has some merit in helping understanding the first time around) but I am looking for a simple gui to achieve the same management.

---

### Post by wilee-nilee on 2010-05-14
> **bwallum said:**
> Manage how the grub menu displays in a simple way.

E.g.

Turn the menu on or off at boot time
Change the background pic
Order the list of boot choice at will, e.g. put windows at top and vice versa.
Set delay before booting default.

All the above can be achieved by poking about in files (which has some merit in helping understanding the first time around) but I am looking for a simple gui to achieve the same management.

I think startup manager is what you want you can set the boot default and set the boot delay time. You can also change the boot countdown from.
gksudo gedit  /etc/default/grub

If you set it to 0 it will be rather difficult to reset the boot order as it has to be done from Ubuntu, I would set it to 1-3. I don't think there is any other way to do this, but others can chime in that know.

---

### Post by bwallum on 2010-05-14
Start-up Manager is not really functional yet. The first thing that perhaps it should do is to turn the grub menu on or off at boot. It can't do this, hence my search for any other user friendly utility.

I guess we are stuck with the /etc/grub.d and etc/default/grub file tweaking at the moment.

Thanks for the replies
Bob

---

### Post by wilee-nilee on 2010-05-14
> **bwallum said:**
> Start-up Manager is not really functional yet. The first thing that perhaps it should do is to turn the grub menu on or off at boot. It can't do this, hence my search for any other user friendly utility.

I guess we are stuck with the /etc/grub.d and etc/default/grub file tweaking at the moment.

Thanks for the replies
Bob

Actually your not going to find all that your looking for in a nice gui, I am with you on this, I use the terminal all the time but prefer a gui. I am working on finding a solution to the grub splash, here is a link for lucid.
[http://www.sucka.net/2010/03/change-grub-splash-image-for-grub-legacy/](http://www.sucka.net/2010/03/change-grub-splash-image-for-grub-legacy/)

Actually this is for grub-legacy, my bad, I will keep looking as it would be nice to have a picture of something at grub.

---

### Post by wilee-nilee on 2010-05-14
So I think your on the right track with having to edit the grub.d here are some links which I think will do it.

[http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)
This is the link from post 3#
[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

---


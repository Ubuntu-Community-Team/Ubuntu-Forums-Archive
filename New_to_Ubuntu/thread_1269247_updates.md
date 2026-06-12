---
title: "updates"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Glenn Owen on 2009-09-18
I have just installed Ubuntu on an older PC and everything seems to be working OK. I have one question though. The update manager is telling me I have 144 MB of updates to be downloaded, I have scrolled through the list and have no idea which need to be installed or what they do. Is this normal when you first install Ubuntu, do I need to download them all.

Thanks

---

### Post by Waappu on 2009-09-18
Hi,

Yes. I propose you install those all.

To avoid that when re-installing I use mini cd
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by MelDJ on 2009-09-18
you can see the description in update manager too

---

### Post by majiciannz on 2009-09-18
A large download of updates is normal after a fresh install.

The quickest way to get everything updated is to open a terminal then type in...
sudo apt-get update
Then hit enter.

Then do the same with...
sudo apt-get upgrade.

Hope this helps

---

### Post by donato roque on 2009-09-18
It's a big Yes.  After a fresh install especially in the middle of the Ubuntu 6 month cycle expect a big update.  I find the update a breeze if you use the gnome-terminal.  Just press alt+f2 and type in gnome-terminal (you don't have to finish typing it,:)).  In the terminal type: sudo apt-get update && sudo apt-get upgrade.  This will tell your local list of repositories to synch with the official servers and the second part of the command tells your system to attempt to download the updates.  Don't worry there will be a final confirmatory question if you want to install them.  Just hit yes.

---

### Post by 3rdalbum on 2009-09-18
They should be presented in three categories: Important Security Updates which are important, Recommended Updates which are recommended, and Backported Updates which are just nice to have.

Yes, it's really that simple.

Third-party repositories which have updates will show up as "Distribution Updates". Obviously Ubuntu doesn't know if they are important or not, so use your discretion there.

---

### Post by Glenn Owen on 2009-09-18
Thanks everyone for your help with this question

---


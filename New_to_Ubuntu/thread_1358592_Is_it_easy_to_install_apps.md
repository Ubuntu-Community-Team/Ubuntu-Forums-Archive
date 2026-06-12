---
title: "Is it easy to install apps?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Bodrey on 2009-12-18
Hello All,

I am absolutely new to Ubuntu.  A friend of mine has been raving about it.  I've never tried it but I'm thinking about giving it a whirl.  First, I have a couple of questions about it...

1) Is Ubuntu easy to install AND can I create a dual-boot configuration with Windows XP without altering the MBR or creating a separate partition for UL? 

2) Is it easy to install APPS in Ubuntu?  I just installed Puppy Linux and although the  OS installation itself worked fine I haven't been able to install **any** applications since then.  Nothing wants to work!  For instance, I've tried installing three different browsers today and none of them will install (Firefox, SwiftFox, SwiftWeasel).  Extremely annoying and frustrating.  If I can't install the programs that I want/need to use it's useless to me...

What is the process for installing applications in UL?  Does it use scripts via a GUI or what?  From what I've seen so far Puppy Linux is severely lacking in this department.

---

### Post by 0cton on 2009-12-18
1) yes through wubi, though not recommended (personal opinion)
2) yes very easy, easier than puppy linux and easier than windows, there is a central software center were you can find lots of free software, plus there is wine to get some windows applications working.
Enjoy your ubuntu

---

### Post by halitech on 2009-12-18
If you want to try Ubuntu but you don't want to mess around with partitions, you can try WUBI (as mentioned by Octon) or you can get Sun's VirtualBox and install it there.

For installing apps, there is the Software Center, Synaptic and you can use the CLI (sudo apt-get install <programname>)

---

### Post by audiomick on 2009-12-18
Hi Bodrey.
Mostly yes...:)

There is a type of install that is referred to as "wubi"
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)
which installs Ubuntu as if it were a windows application. This works apparently, but there are posts here from people having trouble with it. All in all, it seems wise to consider that as a way of trying out Ubuntu, but not a serious long term solution.
If you should choose to continue with Ubuntu, you should do a "proper" install at some point.

Ubuntu is easy to install. Even I can do it....:)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Installing applications, at least those in the Ubuntu repositories, could not be easier. The graphical application is called Synaptic Package manager.
[http://en.wikipedia.org/wiki/Synaptic_package_manager](http://en.wikipedia.org/wiki/Synaptic_package_manager)

 In karmic 9.10 there is a new thing called the Software Centre for managing software. I haven't used it yet, and it appears to have the odd problem still, but it's aim is to make software management even simpler.

---

### Post by deadalus.globalnode on 2009-12-18
I had no problems installing Xubuntu inside of windows and would recommend giving it a try. If I remember correctly it will even give you the option of removing it via add/remove programs should you want it removed. Hope linux works out for you.

---

### Post by northern lights on 2009-12-18
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by SuperSonic4 on 2009-12-18
You can use wubi or a VM but remember the real thing will be faster than both

For an overwhelming amount you can use the repo

For most of the rest you can get a deb (which is not unlike exe) or a PPA (which is like an extra repo)

You'll only have to compile on a very few occasions unless you like the cutting edge (and I mean using svn/git to get daily builds)

---

### Post by mikewhatever on 2009-12-18
'It it easy?' is a relative question, but if you have to ask, it's probably going to be different or hard at first. Why don't you ask your friend to give you some pointers.

---

### Post by joes7 on 2009-12-18
Absolutely.

---


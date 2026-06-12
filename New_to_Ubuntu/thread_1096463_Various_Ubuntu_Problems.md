---
title: "Various Ubuntu Problems"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by feralbyte on 2009-03-14
I have spent a full 2 days simply trying to get my wireless device working. Every single forum, help file or advice I could find was not helpful. Eventually I did it myself by copying the original windows installation CD, manually downloading and installing ndiswrapper using windows and copy it across and using that to install the drivers. However, now every time I restart my computer I need to go back into wireless properties and re-enter the network password to reset the connection settings before it will work again.
Also I am completely unable to find out how to get my nvidia geforce 6600 working. I cant even get the 3d screen savers to run smoothly. Hardware drivers is empty. I did manage to find something that displayed a window allowing me to enable this device, however it simply said it was not able to. So I updated from 7.1 to 8.04 ubuntu and now its gone and I cant find it again.
These are only the main problems I am having so far. It seems once I fix one problem, it simply moves on to the next one and I feel like I am going around in circles.
So far because of ubuntu I have lost a HDD that has simply failed, formated my computer 4 times and repaired my master boot record twice. Help centre has stopped responding and had to be forced quit. This has been the most unfriendly user interface I have ever come across. Is there anyway to improve its ease of use or do I simply need to spend a week reading a 1000 pages of a book to work out how to use it so it can continue to not function correctly and I can spend days typing commands into terminal?

---

### Post by diablo75 on 2009-03-15
Since you are just starting off, I would recommend that you do a fresh install of the latest version of Ubuntu (8.10).  And I would insist that you do a fresh install and not an upgrade from 8.04 (it's takes less time and ensures quirky issues, such as what you're experiencing with your wireless, don't get carried over).

It's also wrong to blame Ubuntu for your hard drive failure.  If a hard drive has failed, it's due to normal wear and tear and all hard drives are destined to die after x amount of usage because they contain moving parts.  If a hard drive ever shows the slightest sign of dying, I'd toss it in the trash and get a new one (they're cheap; you can get 1 terrabyte for $100 these days).

If after installing 8.10 the Hardware Drivers utility still does not allow you to enable proprietary drivers for your video card, try using [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the drivers.  Also, refer to the official [community documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") if you have to resort to using ndiswrapper again; it might contain a step that you overlooked and help to ensure you don't have to reenter your wireless settings everytime you reboot.

---


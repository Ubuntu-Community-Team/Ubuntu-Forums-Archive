---
title: "VirtualBox"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by seenthelite on 2009-11-05
I am considering removing Vista and having Ubuntu as my only OS but I do rarely need to use Windows so I'm looking at VirtualBox. My question is how good is VirtualBox is it actually a viable alternative, any tips on what to look out for and the best way to go about preparing to do this would be greatly appreciated.

---

### Post by howefield on 2009-11-05
It is a very good and viable alternative to a real dual boot, but there are a couple of restrictions, mainly around gaming. If you use windows for gaming, you are probably not going to enjoy the experience. Hardware requirements are tougher, due to running two or more operating systems simultaneously. 

Knowing what it is that you want to use in Vista would help answer your question.

---

### Post by Dude-PWB- on 2009-11-05
I run xp in a virtualbox for a tax program I use, and a few other minor programs like programming my logitech remote that don't run at all in linux, or don't run well under wine.

As mentioned, if you plan on gaming with it, forget it. Virtualbox just doesn't have the 3d capabilities for it. (yet)

---

### Post by phreakshew on 2009-11-05
I'm currently running Ubuntu 9.10 in a Virtualbox on my Macbook and it's great. 

Just remember that when configuring your guest OS that it does not communicate with some hardware directly. For instance, I was initially having problems connecting to the internet wirelessly when running Ubuntu in the VB. I kept trying to get Ubuntu to recognize my airport card, and it wasn't working. What I had to do was have Virtualbox emulate a wired card and bridge that connection to my airport card. So in my virtual Ubuntu, even though nothing shows up under "wireless connections", it thinks it is connected to a PCI ethernet card and can connect wirelessly. It's really not hard. I had some help over here: [http://www.linuxquestions.org/questions/ubuntu-63/9.10-does-not-see-intel-macbook-wireless-card-767147/](http://www.linuxquestions.org/questions/ubuntu-63/9.10-does-not-see-intel-macbook-wireless-card-767147/)

---

### Post by ea1387 on 2009-11-05
I was using virtualbox at first but switchted to VMWare Player 3 since it just came out and it has more features than the older VMWare Player. With WMWare Player now you can install a Virtual Machine, and also you can run Windows programs in Unity, and also you can use Aero. Its pretty easy to install just download the *.bundle file and open terminal and type in sudo bash *.bundle and it will install without asking you any questions in which i liked with the new version of VMWare Player.

---

### Post by superskateman on 2009-11-05
Yes, I use VB to run Linux with Vista and is very good. The only setback is the effects do not work with the current guest additions pack.

Preparing: All you need to do is get the guest additions ISO. This is very easy to do.  I do not have the computer with VB in front of me, but the tab to the right of Machines should have a button that says 'Install Guest Additions.' You'll need to run the linux install with administrative powers, which I can't remember how. But you will eventually get it running.

Look out for: Sometimes the internet will go down for a bit, a simple virtual reboot will work. Also, in very rare cases, the USB will stop functioning for a minute. Don't worry.

---

### Post by howefield on 2009-11-06
> **superskateman said:**
> The only setback is the effects do not work with the current guest additions pack.

Which effects ?

If you mean the desktop effects you get with compiz, then you are wrong, they do work..

At least with more current versions of Virtualbox. (2.1 onwards, I think)

Go here and watch the "Wobbly Windows or 3D acceleration" video and learn.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by ZhuaSD on 2009-11-14
I have successfully used XP on VB a bunch of times, it works great but necessarily is a big drain on system resources and requires a lot of space.

I was using it for completely vanilla purposes, so never had too many problems.

Overall, pretty big two thumbs up from me, although I just installed VB and it broke my internet connection, which is how i got here!  ;-)

---


---
title: "Broadcom BCM 4311: No wireless connection, 14.04"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by exsencon on 2014-06-18
I am running Ubuntu 10.10 for quite a time now, so I thought about upgrading to a newer version. Now, in order to do that I have to save all my stuff (because upgrading over the internet always ends up in disaster), wipe out the ubuntu partition and install the new one. Being cautious I first tried the live 14.04 DVD,but got no wireless at all. So I made a little partition to install it (besides my Ubuntu 10.10 and WinXP) and after a few hours trying,I finally got a wireless with, believe it or not, good ole ndiswrapper. Now, my simple question is: why is it so complicated to have a wireless on 14.04 while it was automatically there in 10.10. Simplicity is the name of the game I would think.
So I will be running 10.10 for quite a while.
Dell laptop Inspiron 1501, HD 120GB, RAM 2GB, running ubuntu 10.10, WinXP Prof.

---

### Post by mörgæs on 2014-06-18
Please begin with reading the sticky notes and post the required output.

---

### Post by exsencon on 2014-06-19
I read the sticky notes,you know.
I have a Broadcom wireless card BCM 4311 802.11b/g  14e4: 4311 (rev01)
Tried several of the possible solutions-no luck. So I'll stick with Ubuntu 10.10 because that works, as do several other Linuxes I have (Fedora, Slackware, Centos, an old mandriva, Mepis,Sabayon,Opensuse and a few others) I even have PCBSD and OpenSolaris running wireless.
Don't know what happened to Ubuntu 14.04 and to Mint 16 for that matter. Very strange, but I don't mind really.

Now I downloaded the new ubuntu 14.10. Same result-no wireless (live DVD). So I am stuck with Ubuntu 10.10 that works perfectly. What is wrong?

---

### Post by chili555 on 2014-12-02
Please get a temporary internet connection and open a terminal and do:

```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```
Reboot and your wireless should be working.

---

### Post by exsencon on 2014-12-04
Allright, I did all you said-no luck
sudo apt-get update was Ok
sudo apt-get purge bcmwl-kernel-source: not installed, so not to be removed
sudo apt-get install firmware-b43-installer: not to be found
On the side: installing 14:10 in a new partition ***** up my old 10:10 Ubuntu which I had to rectify with some problems,but OK
Any suggestions?
When I am in Ubuntu 14:10 even my laptop wifi light is not on, so there's no way for me to get a wireless.
Now in 10:10 it works perfectly.

---

### Post by chili555 on 2014-12-04
> **exsencon said:**
> Allright, I did all you said-no luck
sudo apt-get update was Ok
sudo apt-get purge bcmwl-kernel-source: not installed, so not to be removed
sudo apt-get install firmware-b43-installer: not to be found
On the side: installing 14:10 in a new partition ***** up my old 10:10 Ubuntu which I had to rectify with some problems,but OK
Any suggestions?
When I am in Ubuntu 14:10 even my laptop wifi light is not on, so there's no way for me to get a wireless.
Now in 10:10 it works perfectly.Did you have an internet connection at the time? Did you check your spelling? It works for me.

Can you see the 10.10 partition when booted into 14.04? I may have a sneaky trick!

---

### Post by exsencon on 2014-12-05
Yes,I connected an ethernet connection,and yes I can see the Ubuntu 10.10 partition and boot it and it works (wireless) but not the 14.10-no wireless and the laptop wifi light out.

---

### Post by chili555 on 2014-12-05
If you can see the 10.10 partition, then open the file manager with sudo:```
sudo nautilus
```Drill down to /lib/firmware and find the folder *b43*. Right-click it and select 'Copy.' Paste it to the desktop in 14.04. Close nautilus. Now in the terminal, do:```
sudo -i
modprobe -r b43
mkdir /lib/firmware/b43
cp ~/Desktop/b43/*  /lib/firmware/b43
modprobe b43
exit
```Your wireless should now be working.

It may take a reboot.

---

### Post by exsencon on 2014-12-05
OK, will do when I got some time. Thanks for staying with me!

Well, finally I got success! But not with Ubuntu,I got it with Mint 17.1.
Now I did all the same things we talked about but no luck. Then I went to their software manager and saw the b43 and the b43 fwcutter wasn't installed, so I installed it there from the Gui, although I thought I already installed in the terminal.
I rebooted and up it went! Don't quite understand it because I installed it in a terminal and it looked allright (no errors) but apparently it just didn't install.
Now I have it in Mint and that's very close to Ubuntu, so maybe I can give it another try. 
Of course when I did install Mint I had an ethernet connection.

---

### Post by chili555 on 2014-12-17
> Now I have it in Mint and that's very close to Ubuntu, so maybe I can give it another try. 
Of course when I did install Mint I had an ethernet connection.Indeed. When you install Ubuntu, resist the urge to install 'Additional Drivers' for your wireless. Once it's up and running, do:```
sudo apt-get install firmware-b43-installer
```Reboot. Enjoy.

---

### Post by exsencon on 2014-12-19
Well,I did and...success! I installed Ubuntu 14.10 in place of Mint (had to use Gparted for it to do it right) and then did what you suggested:l
sudo apt-get install firmware-b43-installer without touching anything else.
Rebooted, and up it went!
Thanks a lot for staying with me!
Now I just have to save my old Ubuntu 10.10 stuff and put it in 14.10.
Thanks again!

---

### Post by chili555 on 2014-12-19
Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by lorrie_earley on 2015-01-10
I just wanted to thank everyone who worked on this fix. I always liked this computer and it was running Vista and needed to change. Ubuntu is perfect for it. It was a bit of chaalnge to get it on here but I love it now. Thanks again!

---


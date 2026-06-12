---
title: "Ubuntu 8.10 too slow!!"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by jazz1123 on 2008-12-04
Hi guys,
        I am new to Linux. Since I was facing security problems with Windows, a friend suggested that I try Ubuntu Linux. So, I created a dual boot with Windows XP Sp3 and Ubuntu 8.10, giving 10 GB to Linux partition (ext3), keeping 1GB as swap area. Now here's my problem, the system just does not respond when I boot into Linux. I get the page with login info, clearing which I get to the desktop. then, the system doesn't respond to any mouse clicks or anything. I have tries rebooting several times. The config of my PC is as follows:
1.8GHz Pentium M processor, core speed 599MHz.2MB L2 Cache.
1.25 GB RAM, ATI 9500,64 MB video card. I dont really face any problems when I use my Windows (which I have been using since 4 years).
 Do you think its the Video RAM (too less) or anything else?
 Any suggestions are welcome!!!

---

### Post by mkvnmtr on 2008-12-04
Your system should not be slow. You have enough resources to run fine.,I am still on 8.04 but I have read about some know issues with 8.10 that I believe included your problems. These are problems that people have found and reported. Then other users and developers work to find a work around to fix up the problem. Most times things like thes are known and fairly easy for you to fix. someone that recognizes your problem will probably see your thread shortly and advise you. In the meantime I will scan the known issues to see if I can direct yhou to a thread that will help.

---

### Post by Paqman on 2008-12-04
> **jazz1123 said:**
> the system doesn't respond to any mouse clicks or anything.

Sounds more like it's locked up than a speed problem. Do you know what kind of motherboard your machine has? Some manufacturers cut corners with the power management specs and don't bother to test them properly on Linux, which can result in lockups.

---

### Post by sdowney717 on 2008-12-04
sometimes people who cant run ubuntu can run linux mint, which is based on ubuntu and debian

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

---

### Post by mybunche on 2008-12-04
It definitely should not be slow. My Dell is 3 years old and takes minute to boot, the only 'slowness' I have is that a few websites with flash ads in it takes up 50% CPU, but apart from that it is perfect. I'm sorry I can't help you, maybe your graphics card? Someone should be able to help.  Believe me it is worth finding a solution. Ubuntu for me is fantastic. I rarely and reluctantly fire up Windows.

---

### Post by vandorjw on 2008-12-04
1) When you installled Ubuntu, did you check the cd for errors?
(When you put the CD in and restart the computer, there is an option to check the cd)

It might be that the CD was bad, and that the install failed in a small way that now has a majour effect on your system.

If the CD was fine, then....

2) Is your system fully up-to-date?
If the system locks up and doesn't respond to the mouse, I would guess that you have been unable to update it.

But luckly, you don't need a mouse to update and make sure your system is fine.

Press Alt + Crt + F1

you'll get to a text based log in screen.
Log in with your username and p/w

Hopefully, you are connect the the internet, otherwise the following will not work.

Type: sudo apt-get update
enter your password, and let it do its stuff.

type: sudo apt-get upgrade
(let it do its stuff)

-----------------------------------------
It may be a video card issue???

sudo apt-get install envyng-core envyng-qt
(let it do its stuff)

type: envyng -t
follow instructions (select automatically download ATI drivers)


hope this helps you.

Cheers - CC7

---

### Post by jazz1123 on 2008-12-04
Guys I am sorry that I wasnt clear in describing my problem. What I meant was that I am not able to perform any actions, like open a program. the mouse pointer still moves but the system seems to have frozen (since I can see that the desktop clock has stopped).

 My motherboard is a Toshiba EAL20, with Intel Chpset i855GM/GME

I updated the system when I installed the Linux, and also I used a minimal CD and chose network installation.

Rescue me!!!

---

### Post by handydan918 on 2008-12-04
At the login screen, you can select "options" and "select session" and select "failsafe terminal".

Then you may be able to use the directions posted previously, to wit:

> It may be a video card issue???

sudo apt-get install envyng-core envyng-qt
(let it do its stuff)

type: envyng -t
follow instructions (select automatically download ATI drivers)



---

### Post by sdowney717 on 2008-12-05
If this happened to me, I would redownload and reinstall using live CD.
Just verify the CD first.
And if that did not work, I might try another distro.
We had a pavillion laptop that would run the live CD fine, but when installed, ubuntu would simply hang and lock.

---


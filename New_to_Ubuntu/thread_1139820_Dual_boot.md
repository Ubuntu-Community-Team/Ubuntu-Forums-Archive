---
title: "Dual boot"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by calmpey09 on 2009-04-27
is it ok, to have a 2 os in 1 laptop.. my os now is xp, i also want to install ubuntu... what should i do? install the ubuntu? what will happen to my xp os? anyone pls help..... newbie

---

### Post by overdrank on 2009-04-27
> **calmpey09 said:**
> is it ok, to have a 2 os in 1 laptop.. my os now is xp, i also want to install ubuntu... what should i do? install the ubuntu? what will happen to my xp os? anyone pls help..... newbie

Hi and welcome I have moved your post to its own thread :)
You may have a look [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Installation/I386") for some help

---

### Post by calmpey09 on 2009-04-27
hey everyone, im a newbie... can i ask wat will happen to my laptop if i dualboot it... i have a xp os now i want to change it on ubuntu.. what will i do before i install the ubuntu os?

---

### Post by squirehenry on 2009-04-27
Hi, I want to know the same thing. I recently bought an acer f5 entertainment system. It's already partitioned, can i install ubuntu on the free partition(I haven't put anything on it yet). Also, can i leave a bit of free space for the two os to share? And lastly, should i just get the new 9.04 release or is there one that would be better suited to the job?(asus f5 etc) thanks in advance.

---

### Post by me.translucent on 2009-04-27
well you people can try wubi the simplest way to try ubuntu for more info visit this link [http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by TheRedDragon on 2009-04-27
[FONT=Trebuchet MS][SIZE=3]I've not seem this question asked before, so I'll pose it.  Is it 1) possible to create a dual-boot system such that the choice is between Ubuntu and Kubuntu, possibly in different partitions on the same hard drive, and 2) is it possible to do it such that both have access to a common repository such as another partition on the same hard drive in which user files can be stored?  [/SIZE][/FONT]

---

### Post by candtalan on 2009-04-27
> **me.translucent said:**
> well you people can try wubi the simplest way to try ubuntu for more info visit this link [http://wubi-installer.org/]("http://wubi-installer.org/")

Please note that a popular way of getting ubuntu is to obtain a live CD of the Desktop version, such as ubuntu 9.04 desktop Live CD, and if you insert this cd into a running Windows machine, it will offer to install ubuntu inside windows using wubi which is included in the CD.

Sensible actions before you do this might be to defragment the drive to ensure it is good order.

---

### Post by waspbr on 2009-04-27
@Poster

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

this website is a pretty good start for making a dual boot, also there are some videos on youtube about it. essentially, I install XP on one partition then make another partition for the swap and another for ubuntu (mount as / [this should become clear once you see the installer]), for the ubuntu partition I would recommend you use ext3 or ext4 (personally I prefer #4)

This can all be done by booting your computer with a liveCD. 

remember to back up any essential data, thought unlikely accidents do happen.

@redDragon

You don't need to make another partition for that, tho you can dual boot kubuntu and ubuntu side by side. you can simply install ubuntu normally and then go to synaptic and install the package kubuntu-desktop (when installing it should ask you whether you wanna keep the gdm or use kdm, I would keep the gdm).

Anyway, once that is done log out/reboot. at your login screen you may see an options or sessions button, click there and choose KDE, input your login info and this should take you to a kubuntu desktop.

note that with a different partiton you would essencially have a different system, so different repos, different everything.

---

### Post by candtalan on 2009-04-27
> **TheRedDragon said:**
> Is it 1) possible to create a dual-boot system such that the choice is between Ubuntu and Kubuntu, possibly in different partitions on the same hard drive

yes, it would be just the same as another install. Since both distributions use the Grub boot loader then it will pick up each and you will have a choice when you boot. However, the grub choices list might not say 'kubuntu' but just ubuntu because it uses the same kernel (ubuntu......) so you will choose by looking at other clues such as which drive or partition it is on, no real problem.
Although - please note that a very much easier way of geting both would be to, from running ubuntu, then install the package 
System>Administration>SynapticPackageManager>
kubuntu-desktop
this will install the packages needed for kubuntu and just before you log in choose the option of a different Session from the options menu - kubuntu - kde

If you install like this then during the installation  you need to make the choice of which login manager to use, gnome gdm or kde kdm. If you like ubuntu mostly, choose gdm. It can be changed later.

I often do as I describe here, also installing xubuntu-desktop too.

Only one will run according to your chosen session, at a time. However, most of the applications in all of  them will be seen (and available) in the menus all the time.

If you later choose to remove say kubuntu-desktop, it will not however remove all of the couple of hundred packages it brought down, you would need to do some cleaning up if you wanted to bother with that.


> and 2) is it possible to do it such that both have access to a common repository such as another partition on the same hard drive in which user files can be stored?

yes, such partitions will probably be available automatically ('auto mounted') when you click on the appropriate 'Places' menu item.

hth

---

### Post by ashmew2 on 2009-04-27
Welcome to the community people and Please remember that after installing Ubuntu , you may or may not have issues regarding your computer. We hope that you dont run into such issues , but if you do , we'd be glad to help.

So i would suggest to calmpey09 and squirehenry that only install Ubuntu if you are willing to work to solve your problem and not exclaim "OMG it doesnt work..Why did i waste my time.." , We've all been there and let me assure you that if you get your initial problems sorted , you have a limitless stretch of horizon before you..An endless realm of possibilities awaits you on the other side.. 

Apologies for being dramatic , but couldnt help it.

---

### Post by theozzlives on 2009-04-27
> **TheRedDragon said:**
> [FONT=Trebuchet MS][SIZE=3]I've not seem this question asked before, so I'll pose it.  Is it 1) possible to create a dual-boot system such that the choice is between Ubuntu and Kubuntu, possibly in different partitions on the same hard drive, and 2) is it possible to do it such that both have access to a common repository such as another partition on the same hard drive in which user files can be stored?  [/SIZE][/FONT]

Yes, but they are the same except for the desktop. Install kubuntu-desktop and you can switch at the login screen.
```
sudo apt-get install kubuntu-desktop
```

---


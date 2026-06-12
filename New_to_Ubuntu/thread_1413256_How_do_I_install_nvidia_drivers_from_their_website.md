---
title: "How do I install nvidia drivers from their website..?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-22
I downloaded NVIDIA-Linux-x86-190.53-pkg1.run  ...what do I do with this file?

---

### Post by Ozymandias_117 on 2010-02-22
Open up a terminal, navigate to the file, type "chmod +x filename", then "./filename" it may need to be done as super user, in which case you will have to type "sudo ./filename"

---

### Post by Ozymandias_117 on 2010-02-22
Or, if you prefer the GUI, you can right click on the file, select properties, then click the permissions tab, and check the box "Allow executing file as a program", then double click on the file. Although, if the program needs super user privileges, you will still need to open a terminal to use sudo.

---

### Post by TurnOfTide on 2010-02-22
So, now it says I need to kill X Server to install the Driver. I tried doing this by following insturctions elsewhere and the first step was to press ctrl + alt + f12. This left me with a blank screen and a blinking cursor... Something seems to be wrong, what should I do to install these drivers/make sure this is all setup correctly?

---

### Post by hemimaniac on 2010-02-22
sudo telinit 3 or sudo telinit 1 should do the trick for you

---

### Post by Detonate on 2010-02-22
See this.  It's written for Kubuntu so if you are not using KDE you will have to make a few changes, but it works great.

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

---

### Post by 3rdalbum on 2010-02-22
Having looked at your previous posts, I don't see why you're not just going to System > Administration > Hardware Drivers and installing the driver from there.

Much easier, and it stays in sync with your kernel. I guess nobody has mentioned that you need to reinstall the Nvidia driver every time you upgrade your kernel, if you install the driver from Nvidia's website.

If you want the latest Nvidia driver you can just use the PPA: [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

(or in short, run these commands:)

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-195
```

---

### Post by TurnOfTide on 2010-02-22
> **Detonate said:**
> See this. It's written for Kubuntu so if you are not using KDE you will have to make a few changes, but it works great.
 
[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)
 
 
Can you go into some detail about how to modify this for gnome?

---

### Post by NoaHall on 2010-02-22
> **TurnOfTide said:**
> Can you go into some detail about how to modify this for gnome?

System -> Admin -> Hardware Drivers

---

### Post by samantha_ on 2010-02-22
alright. start up your computer. in recovery mode.
Drop to a root shell by choosing "root" when the blue window shows up.
type in 
```

chmod 777 /home/***username***/Desktop/NVIDIA*run
sh /home_/_***username***/Desktop/NVIDIA*run

```

---

### Post by TurnOfTide on 2010-02-22
> **NoaHall said:**
> System -> Admin -> Hardware Drivers
 
Obivously the OP (me) wants to do this the NVIDIA way.

---

### Post by NoaHall on 2010-02-22
> **TurnOfTide said:**
> Obivously the OP (me) wants to do this the NVIDIA way.

Then it's the same.

Except this bit - 
```
sudo service kdm stop
```
It should be - 
```
sudo service gdm stop
```

Well, and then
```
sudo service kdm start
```
should be
```
sudo service gdm start
```

---

### Post by TurnOfTide on 2010-02-22
Thanks and kudos. I am a bit of a newbie.

---

### Post by NoaHall on 2010-02-22
> **TurnOfTide said:**
> Thanks and kudos. I am a bit of a newbie.

The commands remain the same, regardless of with desktop environment you're using(Gnome, KDE). The only time they'd change is when you're running a command which will affect the desktop environment :)

---


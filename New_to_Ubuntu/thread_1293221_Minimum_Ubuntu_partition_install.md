---
title: "Minimum Ubuntu partition install?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by sirugh on 2009-10-16
Hey guys! I've been experimenting with ubuntu for a couple months now, but I have an issue for work that just came up. I have a 4 GB hard drive that I have to get Ubuntu, XP, and some free space installed as:

1 gb ntfs win xp
1 gb ntfs shared space
1.5 gb ext3 ubuntu (if possible?)

I also have to put  alittle bit of free space between each of the partitions if possible. So I tried installing ubuntu as 1.5 gb, and it wouldn't let me. When I used 2 GB, it let me go through with the install, but cut out after reaching a certain point, saying there was no more space for the install.

Is there a way to slim down the install? I used nLite to slim xp to 1.2 gb, but the partition sizes are really a must for my work. Any help would be appreciated! Thanks!

---

### Post by bodhi.zazen on 2009-10-16
Yep, do a minimal install and build up only what you need.

Ther are many light weight Ubuntu installs as well, crunchbang and lubuntu.

---

### Post by sirugh on 2009-10-16
How exactly do you do a minimum install?

---

### Post by Rocket2DMn on 2009-10-16
Check this page out for the Minimal CD - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

To be honest, 4GB is not enough space to hold all of that, I think Windows XP uses over a GB after a fresh install, and that's before service packs or additions like any sort of Office software.  There are a variety of Linux distributions that are made for small installs.  A minimal install of Ubuntu is more lightweight than a normal install and should fit on the 4GB drive with some room to spare, but I wouldn't try to fit anything more than one OS on a 4GB drive without using VM as the other "installations," and even those need to be really small.

---

### Post by raymondh on 2009-10-16
> **rocket2dmn said:**
> [/url]

  a minimal install of ubuntu is more lightweight than a normal install and should fit on the 4gb drive with some room to spare, but i wouldn't try to fit anything more than one os on a 4gb drive without using vm as the other "installations," and even those need to be really small.

+ 1

---

### Post by ikisham on 2009-10-16
Check [this]("http://ubuntuforums.org/showthread.php?t=1248322") one.

---

### Post by djbon2112 on 2009-10-16
> **raymondhenson said:**
> + 1

+1 also

There's no way you're going to get all that onto a 4GB HDD.

But I have to ask, why are you using a 4GB HDD in the first place? You can find 80GB's for under $50 that will actually give you space to work with!

---

### Post by sirugh on 2009-10-16
Haha well, my boss came to me one day and told me to set up that HDD like that. I work in the computer science department at the school and I'm pretty sure this is a simple virus attack lab that I am helping set up. We have a bunch of these old 4 gb drives sitting around that they don't care to infect, and we don't have any more budget to buy extra Hard drives for this.

I managed to get XP SP2 under 1.2 GB using nlite, I really think I can get this to work.

---

### Post by ankspo71 on 2009-10-17
Hi,
Since they have a bunch of 4 gb hard drives laying around, is it possible for you to install a second 4gb hard drive? You can then have Windows installed on one, and a linux installed on the other. My other suggestion is to look at Puppy Linux, a much faster and smaller live cd that allows you to save your settings to the hard drive when you shut down so that you never need to install the OS itself. It is installable too, but since you have limited space, I thought I would mention it. 
James

---

### Post by bodhi.zazen on 2009-10-17
You can fit a decent installation of Ubuntu into 4 Gb easily.

I have been working on Zenix and it uses 1.5 Gb

[http://zenix-os.net/](http://zenix-os.net/)

When installing , ubiquity pulls openoffice and the lnaguage packs (working on it ...)

During the install, click the "skip" button when it starts pulling these things.

The final install is just under 1.5 Gb and it has XFCE and Fluxbox.

I am just saying , minimal install + proper package selection will fit in a 4 Gb partition easily.

---

### Post by Paqman on 2009-10-17
> **bodhi.zazen said:**
> You can fit a decent installation of Ubuntu into 4 Gb easily.


+1

I built a system up from the minimal image a little while ago. 1.2GB, and that's Gnome and 64-bit. 32-bit would probably be at least 10% smaller.

[Ubuntu Minimal Howto]("http://andyduffell.com/techblog/?p=361")

---

### Post by sirugh on 2009-10-17
I'll be checking that out Monday. Thank you!

---

### Post by Dave67 on 2009-10-23
I have ubuntu on my other computer using the normal download of ubuntu 9.04 I am working on a project here is what it is.

I am working with a another guy on Ubuntu music production system for a friend of mine and we decided to use the Ubuntu minimal install and he is doing the install remotely once I get setup on my end. 

What i would like to know is what does this install or not install compared to the regular install CD I have never used this before so I am wanting to know more about it?  there is not much on the minimal install page except the downloads, or am I missing a link or something?

I do want a X GUI system we decided to go with the mini since all the Ubuntu install iso's have pulseaudio installed and this will not be a compatible sound architecture for the jack sound server etc.

thanks 

dave

---

### Post by bodhi.zazen on 2009-10-24
The minimal CD is exactly that, it is command line only.

If you want a full install you can simply install ubuntu-desktop

```
apt-get install ubuntu-desktop
```

Otherwise you install only what you want. If you want a lighter weight install, install gnome for example.

---

### Post by Dave67 on 2009-10-24
Ok that helps, I do know that we will need the ubuntu desktop install. Now will that install the desktop like in the regular iso download or do I need to add much more? If it wasn't for the pulse audio issue we would just install the regular Ubuntu 8.04 iso image. I never done this before and there is not much of a howto on this. well I will be watching mostly. excpet I will be installing the just the base minimal. 

Is there a howto on the HD partitioning for the ubuntu minimal I will get a howto from the my project team member but I would like to see this as a learning experience for myself.

:)

---

### Post by bodhi.zazen on 2009-10-24
yes, ubuntu-desktop is the same as the desktop iso, and it will install pulse audio.

If all you want is to remove pulse audio, I suggest you install the desktop iso and remove the pulse audio package.

---

### Post by snowpine on 2009-10-25
> **Dave67 said:**
> I have ubuntu on my other computer using the normal download of ubuntu 9.04 I am working on a project here is what it is.

I am working with a another guy on Ubuntu music production system for a friend of mine and we decided to use the Ubuntu minimal install and he is doing the install remotely once I get setup on my end. 

What i would like to know is what does this install or not install compared to the regular install CD I have never used this before so I am wanting to know more about it?  there is not much on the minimal install page except the downloads, or am I missing a link or something?

I do want a X GUI system we decided to go with the mini since all the Ubuntu install iso's have pulseaudio installed and this will not be a compatible sound architecture for the jack sound server etc.

thanks 

dave

Have you considered Ubuntu Studio? It is Ubuntu with Jack and lots of other music apps pre installed.

Anyway, since you are using 8.04, you don't need to worry about PulseAudio. It is installed by default in 9.10, but not 8.04 (which uses alsa instead).

---

### Post by Pipps on 2009-11-11
> **Paqman said:**
> [Ubuntu Minimal Howto]("http://andyduffell.com/techblog/?p=361")
Thank you for mentioning this great article. I am interested in creating an ultra-light Ubuntu 9.10 install for an SSD netbook. 

The article mentions the following commands for adding certain packages:

> sudo apt-get update && sudo apt-get install gdm xorg uswsusp gnome-core gnome-codec-install indicator-session-applet update-manager firefox-3.5-gnome-support gnome-themes network-manager gdebi

May I ask, what would be the minimum package commands that I would require for using only OpenOffice, Firefox, Gedit and browsing files in Knome? 

I am sorry to ask what is probably a very basic question, but I do not recognise the names of some of the other packages that have been included. 

Any help would be much appreciated. Thank you!

---


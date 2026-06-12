---
title: "Starting Ubuntu"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Rabz on 2009-07-09
Hi all!
 
i have just started using ubuntu (downloaded & Installed 9.04). everything installed fine and i have been wondering through my newly installed OS with great pleasure!
 
but..
 
Where do i go from here? what are the basic drivers that i need? and how do i install them?? i have read through the beginners guide almost halfway but would like some more clarity please. 
 
Especially on the following: playing music and games!
 
i tried playing an mp3 but it said that i need some sort of mp3 encoder or something like that. And will i be able to play my games (which i ran on XP)? i read up about it and downloaded a "wine" package, but how do i go about installing it and setting it up to work for me?
 
Anyones help will be greatly appreciated!
 
Ps: I dont have an internet connection on my ubuntu machine. will that be a problem?
 
Tx

---

### Post by random turnip on 2009-07-09
You will need an internet connect to do all the updates, this should download all of the drivers if they are available.

You might need to buy an ethernet cable then go to somewhere with a connection.
However, if everything is already working fine, you might not need to instal any drivers, although most gfx cards and wireless card require them.

After everything is done, you don't really need the internet for anything else unless want to browse the web, get e-mails or download apps, you probably won't even need to upgrade unless something goes wrong (unlikely).

---

### Post by Paqman on 2009-07-09
> **Rabz said:**
> 
i tried playing an mp3 but it said that i need some sort of mp3 encoder or something like that.


The system should install what it needs when you try to play an mp3 file. However you can install mp3 playback as well as Flash, Java, etc in one step by going to Applications > Add/remove and installing the Ubuntu Restricted Extras package.

> 
And will i be able to play my games (which i ran on XP)?

Probably not. It's usually best to run Windows software on Windows. You can get lucky with Wine, but it's hit-and-miss. Check the [Wine Application Database]("http://appdb.winehq.org/") for details of how well your games work through Wine.

---

### Post by ugm6hr on 2009-07-09
Ubuntu is not the best choice if you do not have internet available, since finding software is difficult without it.

This is due to the "repository" style of getting software, so each program comes in multiple components, making manual downloading difficult.

As for playing mp3s - see the multimedia link below.  Unfortunately, it also requires internet.

Linux Mint may be a better choice, since it includes mp3 codecs etc as default (i.e. no need to download after installation).

As for installing XP games, this may prove tiresome for a beginner, since compatibility is not 100%.  If you do want to pursue this, then you will need "Wine" or "CrossOver" (which is not free).

---

### Post by The Cog on 2009-07-09
> i tried playing an mp3 but it said that i need some sort of mp3 encoder or something like that. 
You need to install package ubuntu-restricted-extras. Using the GUI, use either System->Administration->Synaptic or Add/Remove to find it. Or using the command line, either **sudo aptitude install ubuntu-restricted-extras** or **sudo apt-get install ubuntu-restricted-extras**. 
> And will i be able to play my games (which i ran on XP)? i read up about it and downloaded a "wine" package, but how do i go about installing it and setting it up to work for me?
Some games will work in wine, some won't. In general, don't download stuff to install like you did with windows. Search Synaptic first. Or if you know the package name, from the command line: **sudo aptitude install wine**

---

### Post by Daniel1994 on 2009-07-09
I've been running on ubuntu for a couple of weeks now, and this link helped me alot in the beginning:
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)

unfortunately, you need an internet connection to do most of the stuff there.

---

### Post by Rabz on 2009-07-09
i followed the wine link and it said that my warcraft3 will play in ubuntu.
 
i got something like root user has to install aplications. i read i can borrow root powers, but how?
 
do i need to put the files i would like to install in a specific location? 
 
@The Cog: what do you mean with search the synaptic?

---

### Post by tacantara on 2009-07-09
If you install wine using the terminal, prefix the command with sudo (super-user do), and that will allow you to temporarily act as the root.  Downloading through Synaptic or the Add Programs features will prompt you for your password (the password you established during the OS installation).  The password will also give you temporary root level power.  
 
As a fairly new user myself (I started with Ubuntu in February of this year) I found "The Ubuntu Pocket Guide" by Keir Thomas to be very useful in making sense of this "Linux-Speak."  Just run the title and/or author through Google search, and you should find a link that will allow you to download a PDF version for free.
 
Welcome to the world of Ubuntu.  :)

---

### Post by IHeequ5i on 2009-07-09
For help with wine, I strongly recommend visiting  [WineHQ]("http://www.winehq.org"). If you search their database, you'll find all the software that people have tested, along with various "gotchas" and some workarounds.

My advice: since you're newish to Linux, stay away from trying to use anything but Platinum or Gold rated applications at first.

---

### Post by Rabz on 2009-07-09
i found this very cool command through your replies:
 
sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat
 
is it possible to just get the install files for these progams and taking them home to be installed without internet?
 
ps: i have an internet connection, but unfortunately not on my home pc, so downloading apps is not a problem.

---

### Post by Daniel1994 on 2009-07-09
I think it will be difficult to download on one computer and install on an other, specially sense it's a terminal command. If I were you, I would simply bring my computer to a place with internet connection for a couple of hours and install all the files you think you need there.O:)

---

### Post by Cheesemill on 2009-07-09
> **Rabz said:**
> ps: i have an internet connection, but unfortunately not on my home pc, so downloading apps is not a problem.

Ubuntu makes heavy use of the internet to install all of it's programs so may not be the best distro for you.

Take a look at [Keryx]("http://keryxproject.org/") though, I think it does what you want.

---

### Post by Rabz on 2009-07-09
thanks for all your help!
 
will me (ubuntu) and my friend (xp) be able to LAN?

---

### Post by Daniel1994 on 2009-07-09
I think so, yes.

---

### Post by 3rdalbum on 2009-07-09
Why don't you get 3 prepaid mobile broadband for your Ubuntu PC? The thing is, you really need Internet connectivity on Linux; when you have an internet connection, software installation is much more convenient and efficient than on Windows. Without an internet connection, installing software is quite a lot more tedious.

The reason I recommend 3 as a provider is because they tend to bundle an E160 modem, which works out-of-the-box on Ubuntu. For their pay-as-you-go they tend to bundle another modem that also works out-of-the-box.

---

### Post by ugm6hr on 2009-07-09
> **Cheesemill said:**
> Take a look at [Keryx]("http://keryxproject.org/") though, I think it does what you want.

This looks like it come on in leaps and bounds since nonetdebs went down.

I haven't tried it, but it looks like it is definitely worth trying.

---


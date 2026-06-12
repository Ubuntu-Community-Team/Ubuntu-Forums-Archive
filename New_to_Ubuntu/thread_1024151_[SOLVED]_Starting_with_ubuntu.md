---
title: "[SOLVED] Starting with ubuntu"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by borisagrees on 2008-12-28
:popcorn: Hello after using windows for many years and slowly becoming sick and tired of errors, Restarts etc i wish to switch to ubuntu. I am an experience computer user with windows but not familiar with any other. I wish to switch to ubuntu before i get a new mac. I have installed Ubuntu and now i wish to use it as such i am looking for a guide to get everything working. All except for my graphics Drivers work but... i have found a driver for that and need to know the following things...

1. Instaling my Driver for ATI Radeon x1200
2. Getting all my media and CD's and DVD's working like windows (simple Please)
3. Just all the things i should know to set up ubuntu like windows
4. Is Wine worth installing to run games?
5. Can i run my windows games.

Sorry this may seem like a lot but i have been looking for a guide and cant find one... It would be a good thing for someone to make. Hope to hear back soon! :P the :popcorn: is on me

**is it possible to get packages suck as medi thing on windows and install in ubuntu like you would downlaod a .exe file in windows and run like that?**

---

### Post by Kosimo on 2008-12-28
> **borisagrees said:**
> :popcorn: Hello after using windows for many years and slowly becoming sick and tired of errors, Restarts etc i wish to switch to ubuntu. I am an experience computer user with windows but not familiar with any other. I wish to switch to ubuntu before i get a new mac. I have installed Ubuntu and now i wish to use it as such i am looking for a guide to get everything working. All except for my graphics Drivers work but... i have found a driver for that and need to know the following things...

1. Instaling my Driver for ATI Radeon x1200
2. Getting all my media and CD's and DVD's working like windows (simple Please)
3. Just all the things i should know to set up ubuntu like windows
4. Is Wine worth installing to run games?
5. Can i run my windows games.

Sorry this may seem like a lot but i have been looking for a guide and cant find one... It would be a good thing for someone to make. Hope to hear back soon! :P the :popcorn: is on me

First of all Welcome to the Ubuntu community, you're really going to find out all answers to all your questions in this forum. There are many users available to help you.

About your questions.
About the games... There are several games available for linux in a native mode: Quake, UT2003, UT2004, Quake Wars, etc etc. 

All the other games can almost work perfectly using wine or other propietary software like Crossover or [Cedega]("www.cedega.com").

---

### Post by Kosimo on 2008-12-28
If you want to install your ati driver in a very easy mode, just go to preferences, propietary drivers and enable your videocard driver with one click. Ubuntu will download and install your driver for you.

---

### Post by blueridgedog on 2008-12-28
> 
1. Instaling my Driver for ATI Radeon x1200
2. Getting all my media and CD's and DVD's working like windows (simple Please)
3. Just all the things i should know to set up ubuntu like windows
4. Is Wine worth installing to run games?
5. Can i run my windows games.



As to 1, try System -> Administration -> hardware drivers

As to 2, see 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Ultimately, you will use the following in a terminal:

sudo apt-get install Ubuntu-restricted-extras
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
sudo apt-get install ttf-xfree86-nonfree

But, read the web pages for better instructions

3 will take time and I hope you give it some to see what it is like.

For 4, yes you can use many programs under wine, to install it, just use the following in a terminal:

sudo apt-get install wine

As to 5, the short answer is most windows games do not run in Ubuntu (but many games are available).

---

### Post by borisagrees on 2008-12-28
> **Kosimo said:**
> First of all Welcome to the Ubuntu community, you're really going to find out all answers to all your questions in this forum. There are many users available to help you.

About your questions.
About the games... There are several games available for linux in a native mode: Quake, UT2003, UT2004, Quake Wars, etc etc. 

All the other games can almost work perfectly using wine or other propietary software like Crossover or [Cedega]("www.cedega.com").


YAY 1 Q solved i can go windows free and still play my games!!! i have looked at the new to ubuntu forum all the coding looks so complicated ... and i am an experience Batch programmer in windows... looks like i need the internet to do everything...( i have a very limited access to the internet at home) i thought  ubuntu was simple...

---

### Post by borisagrees on 2008-12-28
> **blueridgedog said:**
> As to 1, try System -> Administration -> hardware drivers

As to 2, see 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Ultimately, you will use the following in a terminal:

sudo apt-get install Ubuntu-restricted-extras
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
sudo apt-get install ttf-xfree86-nonfree

But, read the web pages for better instructions

3 will take time and I hope you give it some to see what it is like.

For 4, yes you can use many programs under wine, to install it, just use the following in a terminal:

sudo apt-get install wine

As to 5, the short answer is most windows games do not run in Ubuntu (but many games are available).

Is it possible to download this at work in windows then run in ubuntu say like a windows .exe download?

---

### Post by borisagrees on 2008-12-28
i have a RUN file that was provided by ATI for my graphics card... How can install this? and > Is it possible to download this at work in windows then run in ubuntu say like a windows .exe download?

---

### Post by beastrace91 on 2008-12-28
> **blueridgedog said:**
> For 4, yes you can use many programs under wine, to install it, just use the following in a terminal:

sudo apt-get install wine

Before you can install Wine (with apt-get at least) you need to add it to your repositories.

Open your sources.list (with the command ```
sudo gedit /etc/apt/sources.list
```) and add these lines to it: ```
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb-src http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
```

As for most game I hate to tell you but ALOT of the games refuse to work with ATI + Wine/Cedega in fact I am getting a new laptop because of this... Nvidia is the way to go ATI linux drivers = t3h suck :(

~Jeff

---

### Post by beastrace91 on 2008-12-28
To use a .run or .bin file use the following in console:

```
chmod +x file.run
./file.run
```

As for drivers I have found using [EnvyNG](http://albertomilone.com/nvidia_scripts1.html) is the best/easiest way to install them.

~Jeff

---

### Post by borisagrees on 2008-12-28
thanks

---


---
title: "point me to where to get adobe flash"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-29
point me to where to get components to get adobe flash to work so I can view movies on youtube.  I'm now hooked up the msi wind u100 via ethernet because I couldn't get it to work via wireless.

---

### Post by snowpine on 2009-12-29
sudo apt-get install flashplugin-installer

---

### Post by mickeyjoe on 2009-12-29
> **snowpine said:**
> sudo apt-get install flashplugin-installer

it replies that it could not find installer, perhaps there is a typo in your command line - ?

---

### Post by snowpine on 2009-12-29
Try:

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

or, if you are using an older version of Ubuntu

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by murphykieran on 2009-12-29
If you're using 9.10, then go to Applications>Ubuntu Software Centre and search for restricted extras.  Install that and you will be able to play lots of different formats for media including Flash.

---

### Post by snowpine on 2009-12-29
or:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sandy8925 on 2009-12-29
Or you can download from the adobe site. There's a .deb file available - you just have to download it and double-click the file to install it. I've just checked the site and found that there's an apt option but no idea how to use that - just found out about it.

---

### Post by slakkie on 2009-12-29
Or have a look in my sig :)

---

### Post by sandyd on 2009-12-29
To install flash, [[click here]]("apt://flashplugin-nonfree")

sorry guys, i couldn't resist

---

### Post by mickeyjoe on 2009-12-29
> **snowpine said:**
> Try:

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```or, if you are using an older version of Ubuntu

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```


Your very last sudo line worked.  This msi wind computer must be the problem, because I am running the very very latest Ubuntu version [however I haven't updated it yet to the latest updates].  also, i do know there is some u100 udpate for this particular netbook i must go find very soon.

---

### Post by LuisGMarine on 2009-12-29
Just throwing this out there ... I had to install the .deb straight from the adobe website.  Simply because I'm a sucker for that game bejewled from Facebook and the flash plugin that I installed through the servers would not let the game work.  But I got the one from the actual adobe website and all is good now.  :lolflag:

Simply as double-clicking with .deb these days which is pretty cool.  If you choose to do this in the future for some odd reason, just make sure that you remove whatever other flash plugins you have already installed on your system.

---

### Post by snowpine on 2009-12-29
> **sandy8925 said:**
> Or you can download from the adobe site. There's a .deb file available - you just have to download it and double-click the file to install it. I've just checked the site and found that there's an apt option but no idea how to use that - just found out about it.

I always recommend that beginning users install packages from the Ubuntu repositories, whenever possible. 

While I'm not implying that Adobe can't be trusted, the fact is that surfing the internet to download application installers is a "Windows way" of doing things. Installing from the trusted, tested Ubuntu repositories is more responsible advice.

---

### Post by Guilden_NL on 2009-12-29
> **snowpine said:**
> I always recommend that beginning users install packages from the Ubuntu repositories, whenever possible. 

While I'm not implying that Adobe can't be trusted, the fact is that surfing the internet to download application installers is a "Windows way" of doing things. Installing from the trusted, tested Ubuntu repositories is more responsible advice.

Two thumbs up in agreement when discussing with beginners.  

The interesting thing about the 64 bit forum being shut down is that there are loads of differences still about where to send a newbie who is on 64 bit and how to install the app. IMHO, that decision was one of the worst I've seen here in the past couple of years.

Definitely didn't fit this situation, but seeing more examples of "but I am on 64 bit" midway through the thread, causing me to slap my forehead in frustration about how to help the newbie.

---

### Post by s0ulkeeper on 2009-12-29
one thing that puzzles me the buttons like pause and expand to fullscreen dont work on videos on youtube ..

---

### Post by snowpine on 2009-12-29
> **Guilden_NL said:**
> Two thumbs up in agreement when discussing with beginners.  

The interesting thing about the 64 bit forum being shut down is that there are loads of differences still about where to send a newbie who is on 64 bit and how to install the app. IMHO, that decision was one of the worst I've seen here in the past couple of years.

Definitely didn't fit this situation, but seeing more examples of "but I am on 64 bit" midway through the thread, causing me to slap my forehead in frustration about how to help the newbie.

I agree completely. In this case, mickeyjoe did the right thing by specifying his hardware so we could give the 32-bit specific answer. I wish more posters followed this step.

---

### Post by Guilden_NL on 2009-12-29
I've often thought of providing a template for this forum that requires the bare minimum of info to provide newbie help.  It could be tacked up as a sticky.

---


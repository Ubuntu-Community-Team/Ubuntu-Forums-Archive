---
title: "Converting MP3s to play on CD"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-01-16
Hi All,
 Okay, I downloaded some music through a torrent site, pretty cool process, and have a bunch of MP3s and what not. I have an old CD player in the car, and would like to convert them to regular CD format. What does anyone suggest?
Thanks

---

### Post by anjilslaire on 2009-01-16
1st, if you're in the US or several other countries, watch out for the RIAA/etc.

Now on topic, most cd burning programs should convert them for you. Select "Create audio CD" or whatnot and add your tracks. When it burns, it will uncompress/convert them for you.

---

### Post by PriceChild on 2009-01-16
Brasero is the default burning tool installed in Ubuntu by default.

Applications > Sound & Video > Brasero Disc Burning

I think its then pretty easy to go from there but post if you have more questions!

---

### Post by shifty_powers on 2009-01-16
k3b in the repos...

---

### Post by PriceChild on 2009-01-16
> **shifty_powers said:**
> k3b in the repos...
Why? Brasero is installed by default.

---

### Post by shifty_powers on 2009-01-16
heh, just always preferred it. nothing wrong with brasero, just personal preference :D

---

### Post by LowSky on 2009-01-16
anyway while others argue on which program to use, use the option to burn an audio cd form brasero or K3 or what ever, it will automatically convert from mp3 to WAV (CD format)

Stealling music is illeagal in many countries and this website doesn't want to promote that type of behavoir

---

### Post by stchman on 2009-01-16
> **AndyP79 said:**
> Hi All,
 Okay, I downloaded some music through a torrent site, pretty cool process, and have a bunch of MP3s and what not. I have an old CD player in the car, and would like to convert them to regular CD format. What does anyone suggest?
Thanks

First off downloading copyrighted music via torrents is illeagal.  You can get mp3s off Amazon for under $1 each.

Second you want to make an audio CD out of mp3s?  Easy.  You will need to use K3b.  Brasero can create music CDs out of mp3s with the proper gstreamer.  I perfer K3b as it is a far better CD burning program than Brasero.  Do the following in a terminal:

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

This line is applicable if you are using Hardy or later.  The extracodecs is needed so K3b can create music CDs.

---

### Post by AndyP79 on 2009-01-16
Hi Again All,
 Thanks for all the quick responses. I had done the torrent thing cause a friend showed it to me. I guess I never really thought of the leagality of it. I will take that into consideration though. 
On a lighter note. The Brasero seemed to work fine, I had been dragging and dropping the files earlier, so i guess it was just pasteing them in MP3. I liked the Brasero simply because it just works, I think that seems to be a popular term. I checked out the music I burnt, and it plays in the car CD player, so i am happy and going to leave it at that.
Thanks again to everyone. There was no where to place a thanks to each on the posts this time for some reason, so I will mark this as solved.

---

### Post by LowSky on 2009-01-16
due to some server issues marking solved and thank you's have been temporarily turned off

---

### Post by mkvnmtr on 2009-01-16
I fool with music and movies a bit. There seems to be some that don't like to talk about it in the forums. You can do a search in the package manager for the things you want to do and it will come up with the programs to help you do it. The same is true for file types. Do a search and decide what can help you do what you want. Then many times you can find a web site of the developer to help you use. Check what it depends on and what programs it says will help and install those also. You will find that there is almost nothing you can't do with music and movies with the programs in the repositories.

---

### Post by PriceChild on 2009-01-16
> **LowSky said:**
> Stealling music is illeagal in many countries and this website doesn't want to promote that type of behavoir

> **stchman said:**
> First off downloading copyrighted music via torrents is illeagal.  You can get mp3s off Amazon for under $1 each.There is plenty of free to distribute music out there and I regularly find myself tasting something new with this method. Lets not accuse without proof.

---

### Post by stchman on 2009-01-16
> **PriceChild said:**
> There is plenty of free to distribute music out there and I regularly find myself tasting something new with this method. Lets not accuse without proof.

I did not say that downloading music is illegal.  I said downloading COPYRIGHTED music off torrents is illegal.  I too have downloaded some mp3s from garage bands trying to make a name for themselves(and found the music to be pretty darn good).

I have also downloaded a lot of mp3s off of Amazon after paying for them of course.

---


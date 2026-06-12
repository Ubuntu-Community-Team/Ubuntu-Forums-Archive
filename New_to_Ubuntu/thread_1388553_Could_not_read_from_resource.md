---
title: "Could not read from resource"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by corncob on 2010-01-23
I have not yet been able to play a DVD in 9.10.  Movie Player opens and the start screen comes on but then it says 'An error occurred.  Could not read from resource'.  I've followed the instructions at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .  Other videos like Youtube and camcorder clips work fine.

---

### Post by cariboo on 2010-01-23
Have you tried vlc, I've great success using vlc to watch DVD's

---

### Post by corncob on 2010-01-24
> **cariboo907 said:**
> Have you tried vlc, I've great success using vlc to watch DVD's

Actually, I had downloaded vlc since my last post.  After that Movie Player started working on my desktop almost as if vlc supplied the resource Movie Player was looking for.  However such is not the case with my notebook.  I can't get vlc to work either  -- like I don't know how to use it but I followed instructions, Media > open disc...  No errors but nothing happens either.

---

### Post by Thomas Garman on 2010-01-24
I can really relate.  I spent several months without being able to get a DVD to play in Ubuntu 9.04 despite following what I thought was every suggestion I could find in every forum.  Then...  poof... it just started working in mplayer one day.  Who knows why?  Probably some update installed and it had some lib that made the video stream viewable somehow...  Then when I upgraded to 9.10 it completely wiped out the capacity of my computer to play any kind of media file so I had to spend two months trying to figure out how to get everything back.

What I was doing at the time that ended up making things different on my 9.10 system in such a way that DVD's started playing again was that I was trying to get my Pinnacle PCTV HD usb stick to work for watching television on my computer.  I followed the advice for downloading and installing the em28xx drivers from the french site (google it).  In doing that I installed "ffmpeg..." and "v41-dvb" and "mercurial" and "hg" and the whole metaverse involving anything that said mutlimedia, dvd, driver, player, lib... etc etc...

In spite of all of this, the tv has never worked (not in Kaffeine or Myth TV or anything)... but in the midst of all of this hilarity I got a notion that I would try out a dvd to see if anything had changed and IT PLAYED!  WITH SOUND!  CORRECTLY!  So, I backed up my UBUNTU 9.10 configuration and I will never upgrade or change anything ever again.
  
You might think that this is a reason to just stick with windows, but actually I use a dual boot configuration with Vista Ultimate and in Vista I have never been able to get my CD/DVD player to actually play a cd despite hours of following suggestions on windows forums.  Go figure.

Computers are magic.

---

### Post by theozzlives on 2010-01-24
Computers aren't magic. All I've ever had to do was install ubuntu-restricted-extras and the stuff at [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and DVDs, CDs, Flash, JAVA, etc. all works fine no matter the version of Ubuntu.

---

### Post by corncob on 2010-02-25
I'll finally go ahead and mark this thread as solved.  Following an old tutorial I had printed out back in the Feisty Fawn days, I installed libdvdcss from synaptic and everything is working.  Thanks for all your inputs!

---

### Post by johnmay on 2010-11-28
Here are the two lines of code I ran from theozzlives's link to medibuntu.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/
$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install 
medibuntu-keyring && sudo apt-get --quiet update
```

and the infamous libdvdcss2 can be installed with:

```


sudo apt-get install libdvdcss2


```

Just wanted to post to the link to help keep it popular for the search engines!

---


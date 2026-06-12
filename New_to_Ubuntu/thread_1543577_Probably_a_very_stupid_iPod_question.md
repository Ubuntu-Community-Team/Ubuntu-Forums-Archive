---
title: "Probably a very stupid iPod question"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-08-01
Ok here goes.... I'm running lucid / vista dual boot on my Inspiron 1720 laptop.  I have a 120GB iPod classic and was wondering:

1.  is there an ubuntu download that will sync music, podcasts and video?
2.  if not, how would you set about syncing the above and what with?
3. can you post a URL to simple instructions?

TIA

Gary

---

### Post by nothingspecial on 2010-08-01
Install gtkpod-aac from the software center.

Plug your ipod in

Click it (in gtkpod)

Click add files

Choose the files

---

### Post by Joe of loath on 2010-08-01
Banshee does what you want it to, as well, and doubles as a very good music organiser.

---

### Post by llamabr on 2010-08-01
I just got a new ipod, too, and am only now coming to understand the nightmare of sync'ing and itunes, and aac file formats, etc.

For me, I've been using gtkpod, which works fine.  Before my system will see it, though, I have to mount it with ifuse.  So as root, I do:

```
ifuse /media/ipod
gtkpod
```

And then get down to business.

---

### Post by GaryTheCat on 2010-08-02
I've installed Banshee and like the look and feel of it - it recognises my iPod but gives me an error message saying that the iPod DB needs to be rebuilt because it's been synced with a version of iTunes that's too new for Banshee to cope with.

I let it rebuild the iPod DB and drag and drop new music (conspicuous absence of a sync button) and it goes about its business for a while and doesn't manage to add new music to my iPod.

Has anyone else come across this? and how did you get past it?

G

---

### Post by k3lt01 on 2010-08-02
> **GaryTheCat said:**
> I've installed Banshee and like the look and feel of it - it recognises my iPod but gives me an error message saying that the iPod DB needs to be rebuilt because it's been synced with a version of iTunes that's too new for Banshee to cope with.

I let it rebuild the iPod DB and drag and drop new music (conspicuous absence of a sync button) and it goes about its business for a while and doesn't manage to add new music to my iPod.

Has anyone else come across this? and how did you get past it?

GYes, and you wont get passed it. Banshee does not work with 6th Generation Classics like ours (I have a black 120gb as well and have tried it). GTKPod is the only program that will sync with our model.

---

### Post by GaryTheCat on 2010-08-02
> **k3lt01 said:**
> Yes, and you wont get passed it. Banshee does not work with 6th Generation Classics like ours (I have a black 120gb as well and have tried it). GTKPod is the only program that will sync with our model.


That explains a lot - have lost count of the number of sync attempts!

Thanks!

gtkpod it is then ....

---

### Post by GaryTheCat on 2010-08-02
I guess that Banshee will be able to cope with VI gen iPods in the future.....

---

### Post by k3lt01 on 2010-08-02
I hope so because I really like Banshee, it is my preferred audio media player. Until they do though I'll use GTKPod for syncing.

---

### Post by orethrius on 2010-08-02
> **k3lt01 said:**
> Yes, and you wont get passed it. Banshee does not work with 6th Generation Classics like ours (I have a black 120gb as well and have tried it). GTKPod is the only program that will sync with our model.

Just wondering, is there a real reason for this, political or otherwise? Shouldn't the Banshee team be capable of adding the library behind GTKPod if necessary?

---

### Post by k3lt01 on 2010-08-02
> **orethrius said:**
> Just wondering, is there a real reason for this, political or otherwise? Shouldn't the Banshee team be capable of adding the library behind GTKPod if necessary?Conspiracy theory? I know what you mean and truthfully I don't understand it either. I would have thought all the media player builders could have cracked the 6th generation by now but alas it seems they are not watching (dare I say sharing?) each others code base.

---

### Post by godspeedmav on 2010-08-02
You might want to try this repository : [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily) for Banshee or would Rhythmbox work for you? you might want to try that too. :p

---

### Post by GaryTheCat on 2010-08-02
I think I'm a quitter and booting back into vista and using that there pesky iTunes is the only way forward.

Apple & Microsoft 1 - Me 0 :(

---

### Post by k3lt01 on 2010-08-02
> **GaryTheCat said:**
> I think I'm a quitter and booting back into vista and using that there pesky iTunes is the only way forward.

Apple & Microsoft 1 - Me 0 :(May I ask why?

---

### Post by GaryTheCat on 2010-08-02
I wanted to add some music to my iPod and couldn't get Banshee to work (for the reasons above) and gtkpod would appear to copy the files I wanted to my iPod but when I disconnected it, they weren't on there.

It's not a long term admission of defeat and *I will* get it all to work in Ubuntu when I have a bit more time to tinker with it.  I may try the Rhythmbox approach.

I'm guessing there must be something pretty fundamental I'm getting wrong

---

### Post by mrout on 2010-08-02
Giving up isn't going to help

---

### Post by p.s. on 2010-08-02
> **GaryTheCat said:**
> I wanted to add some music to my iPod and couldn't get Banshee to work (for the reasons above) and gtkpod would appear to copy the files I wanted to my iPod but when I disconnected it, they weren't on there.

It's not a long term admission of defeat and *I will* get it all to work in Ubuntu when I have a bit more time to tinker with it.  I may try the Rhythmbox approach.

I'm guessing there must be something pretty fundamental I'm getting wrong

My first inclination wouldn't be to switch OS's just to accommodate my Ipod. 

I use [Rockbox]("http://en.wikipedia.org/wiki/Rockbox"), and love it. It's simple, reliable, and flexible.

---

### Post by k3lt01 on 2010-08-02
> **GaryTheCat said:**
> I wanted to add some music to my iPod and couldn't get Banshee to work (for the reasons above) and gtkpod would appear to copy the files I wanted to my iPod but when I disconnected it, they weren't on there.

It's not a long term admission of defeat and *I will* get it all to work in Ubuntu when I have a bit more time to tinker with it.  I may try the Rhythmbox approach.

I'm guessing there must be something pretty fundamental I'm getting wrongGTKPod has a couple of steps that don't seem to flow well. Having said that once you get the hang of it you'll understand why it is like it is.

Dumb question so don't be offended, you did "Save Changes" in GTKPod didn't you?

> **p.s. said:**
> I use [Rockbox]("http://en.wikipedia.org/wiki/Rockbox"), and love it. It's simple, reliable, and flexible.Rockbox isn't suitable for this model, I have considered that to.

---

### Post by SunnyRabbiera on 2010-08-02
Install a older version of itunes in wine, should help the issue

---

### Post by GaryTheCat on 2010-08-03
I only used the iTunes approach as a quick fix - I'll spend some time at the weekend getting the iPod to work with gtkpod, my concern was that I didn't have enough time to "understand" what it was I was doing :)

---

### Post by rob22941 on 2010-08-07
Just installed Banshee 1.7 from 1.6, directly off Banshee's site. I'm able to read/add/erase audio files (all that's on it) on my 4th generation 30gb iPod. I'm able to make a playlist but when I disconnect it the playlist isn't on the iPod. Any fix for this? I tried Gtkpod but I have the same issue with the playlist ordeal.

I've tried pretty much all the players. I'm not overly concerned with quality of the sound on this laptop. I just like the layout of Banshee and Rhythmbox the best. I just want to be able to add files, make a playlist, etc. with my iPod. Why can't banshee/rhythmbox get their stuff in gear?

On a side note has anyone had issues with using the ipod connector in a car or anything where rockbox software would replace the ipod software.

---

### Post by rob22941 on 2010-08-08
Ok, I don't know if you want to call this progress or not but I am now able to edit files on my iPod via Banshee, and create playlists with Rhythmbox successfully. I unchecked the automount option in nautilus and I'll just do it manually from now on. 

Anyone find a fix for creating playlists on Banshee yet? Also does anyone know how to shuffle a playlist on an iPod instead of playing alphabetically?

---


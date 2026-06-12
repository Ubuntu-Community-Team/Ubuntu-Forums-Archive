---
title: "Another 'No Sound on Flash' Post"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Erkytimbers on 2008-12-15
Greetings all.  It seems I have finally worked my way through the pages upon pages of 'No Sound on Flash Player' posts and found my way to the actual Ubuntu forum.

Greetings all you grand Ubuntu gurus!

So far every post Ive come across about the issue is for either an older version of Ubuntu, a different version of Ubuntu (I'm using Intrepid I think) or the person has no sound at all and a simple click at taking the mute lock off the speakers does it.

For me, I have no sound on Youtube or any other online stream.... Megavideo, any of the stuff on Sidereel... etc...

Sound works great on the mp3 players on my desktop... sounds better than it ever did before there,  But just nothing on the internet will play sounds.

If you can help, I would greatly appreciate it.  I would like to tell you what all I have done so far, but after 4 days or so dealing with this thing and reinstalling and uninstalling Ubuntu I have lost track of what all I have tried.

I did do a search on google for the issue and just meticulously worked through every fix I could find, but obviously there HAS to be something I havent tried because teh sound still don;t work :)

Thanks in advance if you find it in your heart to help a complete NoOb who is trying his damndest to figure this out....

PS- If you see fit, I will gladly reinstall Ubuntu... again... and start from scratch with any suggestions you may have...  

Thanks again.

---

### Post by Erkytimbers on 2008-12-15
Heh, anyone up for a challenge?

If no, it's cool...  I'll keep ya posted if I happen to come across anything

---

### Post by stoogiebuncho on 2008-12-15
I'm also a bit of a noob, but I've noticed that sound often doesn't work in Firefox if I'm running another program that is using the sound card (like Rhythmbox).  Have you tried shutting down all other programs that would be using your sound card and seeing if that makes a difference?

This probably isn't your solution, but it's something to try until someone more knowledgeable comes along. :)

---

### Post by maddog46113 on 2008-12-15
Do this....
Open terminal 

type:
```
sudo apt-get remove --purge flashplugin-nonfree
```
then
```
sudo apt-get install nspluginwrapper
```
then
```
sudo apt-get install flasplugin-nonfree
```
then
```
sudo apt-get install flash-plugin-nonfree-extrasound
```

Now you should have sound. :)

---


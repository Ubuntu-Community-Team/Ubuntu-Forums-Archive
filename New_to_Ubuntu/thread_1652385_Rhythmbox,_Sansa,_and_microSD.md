---
title: "Rhythmbox, Sansa, and microSD"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by ampoland on 2010-12-24
I googled the hell out of this to little avail, and am wondering if someone here has any idea what I may be doing wrong, or if there is a solution to be had at all.

I'm running 10.10, have a Sansa e250r (2GB) with a microSD card (2GB). I got the Sansa in MTP, and Rhythmbox is working like a charm -- so much easier to manage than copying/pasting.

Except that it only sees the Sansa, not the 2GB of microSD. I *assume* this is because it's the Sansa and not the microSD card in MTP.

I tried putting the blank ".is_audio_player" on the microSD, and then I tried putting the path for the music folder on it.

Worst case scenario I can just copy songs to it using my card reader (if I ever find the damn thing), but it would be much more convenient if I could do it all from Rhythmbox.

Thanks! :D Hopefully this isn't a dumb question; knowing my luck it's an easy fix that I just didn't use the right terms to find.

---

### Post by |Eric| on 2010-12-24
im no expert but id say its like my player (creative) 
you are either mtp or mass storage never both at the same time 
on the other hand you could use a SD reader for the microSD and hookup the player at same time ... 

its more related to the player itself is my guess

---

### Post by intheflesh on 2010-12-25
Hey, ampoland, I'm having my own share of problems with another SanDisk player, a Sansa Clip+, and Linux/Windows.

1. MSC mode is not working. No matter what I do, I cannot copy anything to either internal memory or the µSD card (in Windows).
2. MTP mode is working, more or less. In Windows, syncing with Winamp does the trick, but sometimes content loading takes  forever, sometimes the name of the player doesn't show up (nor do the  songs themselves)... Let's say about 75% of time it does well.
In Linux, however (Ubuntu 10.04), Rhythmbox sometimes exhibit a similar behavior like Winamp (so I guess it's a player issue), but other times, it works well.

Sansa Clip+ also has a µSD card, and I too don't see it displayed in Rhythmbox (neither in Clementine). But I have noticed that **music from internal memory and music from the µSD card are shown together in the list**. How about yourself?

---

### Post by ampoland on 2010-12-28
I had some luck with it, though I haven't had a chance to really experiment to make sure that this was what helped, but: with the ".is_audio_player" in both the Sansa's main directory and the microSD card, and the whole thing in MSC, Rhythmbox was able to see them both and let me add music.

The player then started giving me some grief, but I had at this point been erasing and moving files outside of Rhythmbox, so I'm going to totally format the thing in Rhapsody using Windows (since that'll get everything properly organized, I figure) and then try it again to see what happens.

I'll let y'all know! :D

---

### Post by ampoland on 2010-12-31
Okay, I got it working!

I did end up formatting it using Windows -- I probably didn't *need* to, but for whatever reason I had no idea how to format it in Ubuntu. (Knowing my luck, it's probably very easy, lol.)

Completely formatted, I put the ".is_audio_player" file (empty) on both the Sansa and microSD card, set the Sansa to MSC, and it now shows them both in Rhythmbox. I've transfered songs to both the Sansa and the microSD, and everything is working just as smoothly as ever.

Now to figure out the playlists...

---

### Post by sandyd on 2010-12-31
Heres something that you might like 
[http://download.rockbox.org/daily/manual/rockbox-sansae200/rockbox-build.html](http://download.rockbox.org/daily/manual/rockbox-sansae200/rockbox-build.html)

---


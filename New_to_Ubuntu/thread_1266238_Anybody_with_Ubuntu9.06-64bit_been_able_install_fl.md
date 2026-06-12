---
title: "Anybody with Ubuntu9.06-64bit been able install flash-plugin???"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-14
At this stage I start believing it could be a bug driving me mad. I've been trying all sorts of flash-plugins-64bit I found on web, I got best result with an older version, #9 of flash-plugin for 64bit arch. and I was able to SEE the video but NOT the sound.

If you had it to work I'll keep on trying. Otherwise...I'll go Opera.

---

### Post by NoaHall on 2009-09-14
Yes I have, and it works brilliantly.

Try this -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

---

### Post by 3rdalbum on 2009-09-14
You've already got a thread about this. Check your other thread (assuming you don't have half a dozen already) because I've replied. It works fine here.

---

### Post by webwiller on 2009-09-14
Oh my god...
I did it like in this tutorial you gave me before...and it did not work, I did it right now and I got video only but no sound. ANd sound works in all other app's.

---

### Post by NoaHall on 2009-09-14
Have you by any chance clicked mute on the video?

Did you delete ALL of them before reinstalling? 

Have you tried a different browser?

What browser are you using?

Are you sure you have 64 bit?

What are you using to manage your sound? Pulse audio etc.

---

### Post by Nburnes on 2009-09-14
Look at this. Should most likely be the same for Jaunty.
 
[http://ubuntuforums.org/showthread.php?t=1241313&highlight=FLash+64-bit](http://ubuntuforums.org/showthread.php?t=1241313&highlight=FLash+64-bit)

---

### Post by bumanie on 2009-09-14
[This]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html") is the only way I have found to get flash to work with any stability on ubuntu 64bit. You have to have firefox closed when following the instructions. so copy & paste to a text document. I was like you, the tutorial mentioned above did not work on my system, but the other one had worked with out ffailure since installation.

---

### Post by webwiller on 2009-09-14
> **NoaHall said:**
> Have you by any chance clicked mute on the video?

Did you delete ALL of them before reinstalling? 

Have you tried a different browser?

What browser are you using?

Are you sure you have 64 bit?

What are you using to manage your sound? Pulse audio etc.

-Nothing muted
-ALL deleted, and specifically I deleted:
/usr/lib/mozilla/plugins/libflashplayer.so
/opt/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflasplayer.so

and reinstalled about 30times now :(

- I AM sure it is a 64bit arch. Ubuntu confirmed it too saying, when I was trying to install the 32bit from Adobe (I believed it would give the right version straight away...as it didnt give me any choice at all!)

- I tried Opera too and flash works beautifully, but I have firefox on all pc's at home 'n work...with bookmarks and pwds synchronised...it would be a pain in the a...to change them all!

-I use Alsa, but tried Oss and pulse-audio as well, nothing happened.

I cant believe it...I'm using a notebook, hp6730s... could THAT make any difference???

---

### Post by NoaHall on 2009-09-14
Pulse would probably work best. 

A hp6730s? As far as I know, the processor it has is a 32 bit processor... 

Use Opera for now, until we can find a cure then :)


Try in firefox:

Tools -> Manage Content Plugins -> Plugins in use -> Make sure it's that file that it's using.

---

### Post by webwiller on 2009-09-14
> **3rdalbum said:**
> You've already got a thread about this. Check your other thread (assuming you don't have half a dozen already) because I've replied. It works fine here.

I have hundreds... :)

I just wanted to know if somebody sorted it out, as I'm trying 2days now and went through tens of tutorials...

---

### Post by Magnesium on 2009-09-14
webwiller,

Try this: switch back to using alsa for sound, and run

```
alsamixer
```

in a terminal, and make sure the PCM slider is all the way up. When I first installed the 64-bit flash player, I got video, but no audio, and this did the trick.

Let us know if this works.

Mg

---

### Post by Magnesium on 2009-09-17
> **Magnesium said:**
> webwiller,

Try this: switch back to using alsa for sound, and run

```
alsamixer
```

in a terminal, and make sure the PCM slider is all the way up. When I first installed the 64-bit flash player, I got video, but no audio, and this did the trick.

Let us know if this works.

Mg

Did this work? You kind of dropped out of the world on us... :-s

---


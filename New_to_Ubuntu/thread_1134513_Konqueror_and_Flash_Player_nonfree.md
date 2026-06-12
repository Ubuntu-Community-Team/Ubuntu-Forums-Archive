---
title: "Konqueror and Flash Player nonfree"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by teddybairs1 on 2009-04-23
I've been using Ubuntu or a variant for years now. I suppose I should have figured this one out by now, but it still stumps me. Why doesn't the flashplayer nonfree plugin work with konqueror? The gnash plugin works, but it's practically useless for most normal flash usage (i.e. youtube, and pretty much any kind of video). Konqueror is a great program for just about anything you need to do and was ahead of its time to begin with, but this one issue keeps it from really shining like it could. Can anyone explain this to me?

---

### Post by yeats on 2009-04-23
I've wondered the same thing myself, but I've never looked into it...

---

### Post by inobe on 2009-04-23
it's konq and not the plugins i know this much.

note: never tried on a 32bit environment.

---

### Post by eudemus on 2009-04-24
I have found the same problem.
I tried various things, including a "solution" here:
[http://mikearthur.co.uk/2007/12/konqueror-with-latest-adobe-flash-howto/](http://mikearthur.co.uk/2007/12/konqueror-with-latest-adobe-flash-howto/)
But it didn't work.

Would be great to get this working.
Apparently it does in KDE4, but I'm not in a hurry to upgrade (after previous fiascos! .... will let the new versions settle down a bit first).

Cheers for any help anyone can offer ....

---

### Post by gandaran on 2009-04-24
install or just copy the libflashplayer.so file (adobe flash plugin) to Konqueror plugins directory!

---

### Post by eudemus on 2009-04-24
I'm liking the simplicity of it ... 

But where is this directory?
A brief look around /usr/lib hasn't shown me anywhere obvious ....

---

### Post by gandaran on 2009-04-24
> **eudemus said:**
> I'm liking the simplicity of it ... 

But where is this directory?
A brief look around /usr/lib hasn't shown me anywhere obvious ....
I don't use KDE so I'm not sure, look in /home/'user'/.konqueror/plugins (maybe try making the plugins folder here and install the flash, usually this works for almost every browser, I don't know about konqueror!) or /usr/lib/konqueror/plugins.

edit:
adobe flash is a gtk application, maybe you need something to make it work with qt applications so I'm not sure if it can work but try anyway and let us know the outcome.

---

### Post by eudemus on 2009-04-24
Ah, I've got it in a folder detected in Konqueror, and it appears in about:plugins, but it still doesn't work.

I've really no idea why.

about:plugins lists other flash plugins, although the version I want (v.10) appears first on the list. Should work. But doesn't.

Humph.

---

### Post by eudemus on 2009-04-24
by the way, I do appreciate your help & suggestions very much.

---

### Post by gandaran on 2009-04-24
> **eudemus said:**
> Ah, I've got it in a folder detected in Konqueror, and it appears in about:plugins, but it still doesn't work.

I've really no idea why.

about:plugins lists other flash plugins, although the version I want (v.10) appears first on the list. Should work. But doesn't.

Humph.
if you have any other flash installed you have to remove them, only keep adobe flash installed then try again.

---

### Post by eudemus on 2009-04-24
Yeah, I'm getting a better result now with many sites, but not for youtube ... must investigate further ....

Cheers for your help.

---

### Post by teddybairs1 on 2009-04-24
I've tried moving the libflashplayer.so file before, and I've tried it on KDE4 and KDE3, but still no dice. I'm not a coder by any stretch. I barely got through my C++ class, and that's rusty at best.

It just doesn't make good sense to me why this problem seems to have been overlooked for so long. Konqueror is a great browser. If this problem were solved, I'd probably use it instead of Firefox most of the time. I remember it was the first Linux browser I really used on Linspire, when it was still Lindows, because I couldn't get the Mozilla suite working for some reason on 4.5 with the dial-up.

Maybe I should shoot an email to the Kubuntu MOTU.

---


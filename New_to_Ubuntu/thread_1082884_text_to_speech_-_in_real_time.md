---
title: "text to speech - in real time?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by rocka on 2009-02-28
Hi,
I don't know if this is even possible, or maybe a bit "out there"...

I was wondering: does anyone here know of a way to get text-to-speech in real time? I mean, I want to be able to type and have the computer speak the words as I type them. I have in mind an idea for my live show [I play keyboards [synths] etc]. I would have a laptop probably set aside for this purpose, with the VGA out being sent to the projection screen behind me, so the audience would see the words as I type and hear them too. It wouldn't have to be *too* realistic, a Kraftwerk-style robotic voice would be just fine. I'd probably be altering with vocoders, pitch mods etc anyway.

Anyway, just an idea...
Is it possible?

---

### Post by geirha on 2009-02-28
If you run the command ```
espeak
``` in a terminal, it will speak the text you type, but for each line at a time, not word ...

You could use a loop that reads word by word and outputs each word on a separate line though
```
while read -d' ' word;do echo $word;done | espeak
```

---

### Post by rocka on 2009-02-28
Hi,
thanks for your answer...

I tried it just quickly now [haven't had much time to delve into it at all yet...] but I got this error message:
```
merlin@merlin-desktop:~$ espeak
hello
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
```

and so on, down the page, until I hit <ctrl-c>

---

### Post by geirha on 2009-02-28
According to this, apparently a different process has locked the sound device. [http://ubuntuforums.org/archive/index.php/t-347725.html](http://ubuntuforums.org/archive/index.php/t-347725.html)

---

### Post by ikisham on 2009-02-28
Orca screen reader wont work for that?

---

### Post by cariboo on 2009-02-28
Go to Applications-->Universal Access and setup the screen reader. Have a look at the [Orca]("http://live.gnome.org/Orca") web page.

Jim

---

### Post by stoogiebuncho on 2009-02-28
> **geirha said:**
> If you run the command ```
espeak
``` in a terminal, it will speak the text you type, but for each line at a time, not word ...

You could use a loop that reads word by word and outputs each word on a separate line though
```
while read -d' ' word;do echo $word;done | espeak
```

whoa, I just spent fifteen minutes entering Beastie Boys lyrics into that thing.

Now I'm using it as my only means of communicating with my wife.

If she leaves me, I'm blaming you.

---

### Post by rocka on 2009-02-28
LOL :lolflag:

"we got the right,
. . . to paaaaaa-aaaa-rrrrr-ty"


\\:D/

---

### Post by albinootje on 2009-02-28
> **stoogiebuncho said:**
> whoa, I just spent fifteen minutes entering Beastie Boys lyrics into that thing.

Now I'm using it as my only means of communicating with my wife.

If she leaves me, I'm blaming you.

Perhaps you're interested in installing Emacs (RMS will be delighted) and try the psychoanalyst mode that Emacs provides ? :)

[http://www.emacswiki.org/emacs/EmacsDoctor](http://www.emacswiki.org/emacs/EmacsDoctor)
[http://everything2.com/title/M-x%2520doctor](http://everything2.com/title/M-x%2520doctor)

---

### Post by MattiJ on 2009-02-28
```
espeak "Amiga is tha king of computing amen"
```

---

### Post by thtrgremlin on 2009-02-28
This was really interesting to come by. In my case, it worked right away from a gnome-terminal, however, it spoke each word after I typed a <space> only;, not after <enter>. I could get it to wait between words by escaping the space, so...
> "You got to fight for the right" 
would be spoken as I typed each word (even with the quotes), but
> You\ got\ to\ fight\ for\ the\ right
would be spoken as a sentence once I typed <space> at the end.

Hope that contributes.

Also, if you want to use espeak, check your sound settings. Is your mixer set to alsa? I have had the same problem you are describing in the past.

---


---
title: "network through soundcard"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by hydraulicjj on 2008-11-22
hi
i was wondering if it was possible to set up a network through a soundcard? also if it is possible does anyone know a program for hardy that would do this?

----------------
Now playing: [The Who - Too Much of Anything](http://www.foxytunes.com/artist/the_who/track/too_much_of_anything)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by lykwydchykyn on 2008-11-22
network through a soundcard?  You mean like, send the packets over audio lines?

---

### Post by hydraulicjj on 2008-11-22
> **lykwydchykyn said:**
> network through a soundcard?  You mean like, send the packets over audio lines?

yeah, i thought it would be a good idea since as you can effectively send data to 6 computers at a time with a 5.1 card and recieve data from 4 providing you have a line in and a microphone in. also soundcards are cheaper and the cables are also cheaper.

----------------
Now playing: [Guns N' Roses - Paradise city](http://www.foxytunes.com/artist/guns_n_roses/track/paradise_city)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by lykwydchykyn on 2008-11-23
I'll save the lengthy dissection of this idea and just tell you it's not possible.  'Cause it's not.  A few NICs (assuming they aren't on the motherboard), a hub, and some ethernet patch cables shouldn't set you back that much.

---

### Post by hydraulicjj on 2008-11-23
> **lykwydchykyn said:**
> I'll save the lengthy dissection of this idea and just tell you it's not possible.  'Cause it's not.  A few NICs (assuming they aren't on the motherboard), a hub, and some ethernet patch cables shouldn't set you back that much.
but presumably it would be possible just not practible wouldnt it?

----------------
Now playing: [Hanzel und Gretyl - Burning Bush](http://www.foxytunes.com/artist/hanzel_und_gretyl/track/burning_bush)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by TerranFury on 2008-11-23
There's nothing in principle to stop you from doing this, but it'd require some significant programming effort on your part.  You'd need to write code to modulate data at audio frequencies, and to demodulate it.  I actually wrote some code a long time ago to do just this, using either binary FSK (frequency shift keying) or PSK (phase shift keying), [but there are two reasons it wouldn't be useful to you: (1) It is not integrated in any way with Linux as a "network device" -- actually, it was a weird Frankenhack running on Cygwin; instead, it accepted data piped to it on STDIN.  And (2) there's an important part of the demodulator that I never really figured out satisfactorally, which is the phase-locked loop (which lets the demodulator know when the boundaries between keys are in time).

Also recognize that "modulating data at audio frequencies" is exactly what telephone modems (remember them?) do (the phone network only works in the audio range), so rather than writing your own modulators, etc, as I did, you might be able to use existing softmodem code.

So I'd argue that it is very much possible.  Practical?  No.  Useful?  No.  But possible?  Most certainly.  It'll just take some work on your part.

Before I go, here are some random websites I googled in the last minute which might be useful:
[http://linux.maruhn.com/sec/multimon.html](http://linux.maruhn.com/sec/multimon.html)
[http://www.baycom.org/~tom/ham/soundmodem/](http://www.baycom.org/~tom/ham/soundmodem/)

Cheers.

---

### Post by hydraulicjj on 2008-11-24
> **TerranFury said:**
> Also recognize that "modulating data at audio frequencies" is exactly what telephone modems (remember them?)

i remember them only to well (turns around and looks at the pile of them stacked up behind me).
so if i learnt programing in a language like c and re-wrote the drivers for my soundcard and modulated the signal i could do it then?

----------------
Now playing: [Velvet Revolver - Superhuman](http://www.foxytunes.com/artist/velvet_revolver/track/superhuman)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by lykwydchykyn on 2008-11-24
Certainly feel free to give it a try.  Keep in mind that networks require two way communication, so you can't (as you originally suggested) just have your outputs going to computers.  You have to have an in and an out for each computer.

---


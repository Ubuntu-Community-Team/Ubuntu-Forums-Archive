---
title: "Guitar software"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by nu-to-buntu on 2009-03-15
is there any software that i can use to help read and write music with? someone told me that i could plug it in and play and this program woud translate it to notes. Is this true? I am a nub and just joined. Wanting to use Ubuntu for my music, so got Ubuntu Studio.

---

### Post by zvacet on 2009-03-15
I´m not an expert but look for [Tuxguitar]("http://www.tuxguitar.com.ar/") and see is that what are you looking for.

---

### Post by expatCM on 2009-03-16
I was wondering if rosegarden would help you out at all?
[http://www.rosegardenmusic.com/tour/](http://www.rosegardenmusic.com/tour/)

---

### Post by ivanvajar on 2009-03-16
I don't know if there is a program that translates playing into notes, but I do know how to use Ubuntu as an amplifier and guitar effects processor.

1. Install CREOX

2. Use Synaptic to install jackd.

3. Run Terminal and type 
> sudo jack -d alsa 

4. In a new Terminal window type 
> sudo creox

and you're ready to go!

When you close Creox, press ctrl+c to exit jackd and close Terminal.

For editing notes, I use Tuxguitar. It's similar to GuitarPro. For editing music, there are Ardour, Audacity, Beast...

---

### Post by sazan on 2009-03-16
I just know that there is Guitar Pro for windows.
 Never tried installing it in Linux , try it in Wine;)

---

### Post by ivanvajar on 2009-03-19
There is no need to install GuitarPro with Wine. There is TuxGuitar that is as good as GuitarPro.

---

### Post by Techproof on 2009-05-06
I installed TuxGuitar and can't seem to get it to play the notes I enter. Its one of the reasons I like the software and it won't work strangely. The weird thing is the sound output on my machine is fine. Running ubuntu 9.04 but haven't managed it with either of the 8 releases either.
Anyone got any ideas on this software.

---

### Post by rbc on 2009-05-06
I cannot help the OP, but Techproof.....If you mean that sound works normally with everything else, just not with Tuxguitar, open Synaptic find these two plugins:
tuxguitar-alsa
tuxguitar-jsa
Install them, if they aren't already, and see if that helps

---


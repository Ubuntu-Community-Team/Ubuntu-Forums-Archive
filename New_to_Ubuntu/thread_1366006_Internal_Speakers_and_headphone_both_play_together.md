---
title: "Internal Speakers and headphone both play together"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by prince2689 on 2009-12-27
I am having Lenovo 3000N100 0768HCQ laptop and i installed a fresh copy of Ubuntu 9.10 Karmic and everything is working fine expect for sound......

When i play a song, I can hear sound from both headphone and internal speakers......they both play together.

I have also windows 7 installed in my laptop and only my headphone play song if it is attached and internal speakers remain silent which is the normal working condition..

So i guess its not a hardware problem, its some kind of problem with ubuntu...

Plz anybody help me !!!!!!! :(:(:(:(

---

### Post by iMisspell on 2009-12-28
Being Karmic is still kind of new, maybe you could try a livecd of an older ubuntu version and see if the problem exsists there too. Might beable to help out the devs if its only a Karmic problem.
Just a thought.

---

### Post by Chris Edgell on 2009-12-28
Have you seen the official site about sound problems in Karmic.  Maybe you'll find something there to help with your problem.

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Sound%20drivers%20need%20to%20be%20updated](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Sound%20drivers%20need%20to%20be%20updated)

---

### Post by prince2689 on 2009-12-29
Thanks Chris and iMisspell for helping. I solved my problem by installing the following package..........

apt://linux-backports-modules-alsa-karmic-generic 

And after reboot my internal speakers get silent when i attach a headphone......:lolflag:

Thanks once again............:):):):)

---

### Post by glubbdrubb on 2009-12-29
Funny, I saw this bug as a feature. 

It is useful when watching a movie with someone who likes to talk a lot.

Could you mark this thread as solved please, using the "Thread Tools" at the top of the page.

---


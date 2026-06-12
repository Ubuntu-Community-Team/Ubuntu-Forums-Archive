---
title: "Sound problems in 8.10 x64"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by topbarn on 2008-12-24
I am new to Linux.

I have installed the above with no problems except an odd problem wrt sound.

Sound Card is Audigy ZS2. AMD 4400+, ASrock 939N68PV-GLAN, 2MB RAM.

As a "user" I can get playback/CD audio etc., to work OK but cannot get the sound event sounds to work.

But, if I open up as a "guest", the sound events are OK!

I've tried all the permutations from some of the detailed forum postings on sound, to no avail and have re-formatted and reloaded and still have the same  symptoms.

Advice please.

TIA

John

---

### Post by linux_tech on 2008-12-24
Check under System->Preferences->Sound and look under the "Sound" tab, make sure  the System Sounds are configured.

---

### Post by topbarn on 2008-12-25
Thanks, done that. Interestingly when going to guest, all the settings change to "autodetect", whereas "autodetect"  doesn't work at all for a "user".

John

---

### Post by topbarn on 2009-01-01
Mr linux_tech,

FX:<grovel>

You were right! It **was** the config! The Audigy gave 7 options to select, and that together with the vol control preference options meant I didn't get the right permutation ;-)

Thanks!

John

---


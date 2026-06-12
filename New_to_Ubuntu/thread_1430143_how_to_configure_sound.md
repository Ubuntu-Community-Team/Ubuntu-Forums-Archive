---
title: "how to configure sound"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by abhijitiitr on 2010-03-15
using ubuntu9.10 for the first time ,i haven't heard any sound like windows .how do i get the sound working on my dell inspiron laptop?

---

### Post by sahabcse on 2010-03-15
please check if the sound is muted, and also check if it detects your sound card. Run the following command in terminal :

Checking if sound is muted :

alsamixer

Checking for sound card :

aplay -1

---

### Post by lidex on 2010-03-15
For Karmic I would go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and work through the thread. Terminal can be found in your Accessories menu: "Applications>Accessories>Terminal"

---

### Post by mikemelen on 2010-03-15
I think the sound driver not installed in your notebook. Go to system-->administration-->hardware drivers.

---


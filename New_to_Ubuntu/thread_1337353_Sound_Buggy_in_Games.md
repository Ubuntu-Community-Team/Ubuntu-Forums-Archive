---
title: "Sound Buggy in Games"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-11-25
In two games I've just recently decided to try (The Battle For Wesnoth and Chromium BSU) the sound is somewhat is choppy on and off and sometimes cuts out altogether. Is there a setting or package I can use to fix this?

---

### Post by pbrane on 2009-11-25
You can try creating a file in your home directory called **.alsoftrc** (note the dot) with the contents **drivers = oss** 

that fixed the choppy sound for me.

---


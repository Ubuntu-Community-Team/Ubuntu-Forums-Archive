---
title: "Changing a kernel"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-06-13
What is the correct way of changing a kernel? I was told that I had to get an older kernel if I wanted tvtime to run in 10.04.I want to use 2.6.28-19 because it works fine. Can this be used with 10.04?

---

### Post by Tahakki on 2010-06-13
You can manually compile an old kernel, but it' be much easier to do what I did - search Synaptic for 'linux-rt' and install that. It's the realtime kernel, which shouldn't make any difference to you (it's better for audio-related stuff), but it is a lower version than the one currently in Lucid. :)

---


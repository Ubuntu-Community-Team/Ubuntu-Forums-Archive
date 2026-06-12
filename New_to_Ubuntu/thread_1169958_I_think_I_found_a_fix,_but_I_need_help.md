---
title: "I think I found a fix, but I need help"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by ChemShock on 2009-05-25
Ok, so I'm having an ALSA sound issue. It's looking for a sound card that does not exist and I do not have a back-up file. So, can I use the installer disc to re-write the file since it's OS related? Can I force it to re-create the file? I just need it in its default form. If you need for info, I'll add as needed. Thanks in advance.

---

### Post by mprince on 2009-05-25
I think if you open a terminal and type:```
sudo alsaconf
```

it will reconfigure the setup for your sound card.

---

### Post by ChemShock on 2009-05-26
It says its a invalid command. Like I i could got to default that be great.

I tried reinstalling alsa through synaptic, it didn't work.

---


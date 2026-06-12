---
title: "pulse audio and hdd temperature??"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by duruttye on 2010-02-27
Hey there!

I have a question!

Can there be a link between pulseaudio and my high hard disk temperature?

I had to remove pulseaudio from my system, because the sound is realy bad (not solved) and I noticed a drop of 5 C of my hard disk temperature. I am sure of this, because I have to monitor hddtemp constantly, because it is high (59-60C) but after removing pulseaudio, it dropped to 54-55 C.

Can this be possible?

And also, is there a tutorial about how to replace pulse audio in ubuntu 9.10?

---

### Post by sandyd on 2010-02-27
```

sudo apt-get remove pulseaudio pulseaudio-*

```
sound system will automatically fall back to ALSA.

or. alternatively
```

sudo mkdir /etc/init.d-disabled
sudo mv /etc/init.d/pulseaudio ../init.d-disabled
```

---


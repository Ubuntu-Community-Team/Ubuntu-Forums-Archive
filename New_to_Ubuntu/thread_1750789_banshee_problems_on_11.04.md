---
title: "banshee problems on 11.04"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by redspotss on 2011-05-05
just installed ubuntu 11.04 on my notebook . and was checking the banshee player can't get it to work ?

---

### Post by Shmantiv_Radio on 2011-05-05
Can't get to work in what way?

---

### Post by redspotss on 2011-05-05
wont play anything off my ipod or any of the music that i have uploaded

---

### Post by Shmantiv_Radio on 2011-05-05
> **redspotss said:**
> wont play anything off my ipod or any of the music that i have uploaded

Did you install any codecs?

---

### Post by redspotss on 2011-05-05
tried to . was able to get the gstreamer but not much of anthing else.

---

### Post by redspotss on 2011-05-05
i think the command line i got was incorrect because it didn't work for the codecs.

---

### Post by Shmantiv_Radio on 2011-05-05
Run this in Terminal.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get -f --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get -f --quiet update && sudo apt-get -f install app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update && sudo apt-get -f install ubuntu-restricted-extras
```

---

### Post by redspotss on 2011-05-05
cool thanks will try it .i'll let ya know .

---

### Post by redspotss on 2011-05-05
thank you banshee is working great ! :D

---


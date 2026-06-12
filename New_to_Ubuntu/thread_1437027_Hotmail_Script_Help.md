---
title: "Hotmail Script Help"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by tm-b on 2010-03-23
Hi (first post)

Basically I want to make a script to open my hotmail account in a browser. I can already do :

#!/bin/bash

chromium-browser "www.hotmail.com"


However obviously this only opens the website which then gives a login prompt. I am wondering if its possible to login through the script and basically be presented with my inbox?

Any help is much appreciated.

---

### Post by descendent87 on 2010-03-23
Can't help with the script but would it not work to log in and just click remember password so the next time you call the script you're still logged in?

---

### Post by Paqman on 2010-03-23
Why use a browser if you're after one-click opening? Just set Evolution or Thunderbird up to grab your Hotmail. One click to open your mail client, no login required!

---

### Post by r-senior on 2010-03-23
Are you managing to do this Paqman? Unless things have changed I thought you couldn't use Hotmail from a client like Evolution/Thunderbird? Googlemail works but I thought Hotmail had some sort of spoiler that forces you to use the website?

Am I wrong?

---

### Post by tm-b on 2010-03-23
> **descendent87 said:**
> Can't help with the script but would it not work to log in and just click remember password so the next time you call the script you're still logged in?

Don't know if its the browser's fault but the remember password option seems to be unreliable at best, and mostly just doesn't work.

[QUOTE=Paqman]Why use a browser if you're after one-click opening? Just set Evolution or Thunderbird up to grab your Hotmail. One click to open your mail client, no login required![/QUOTE]

Didn't know that this was possible with hotmail since its web based. Will look into this but would still prefer the script for general geek-factor ;)

---

### Post by undecim on 2010-03-23
> **tm-b said:**
> Didn't know that this was possible with hotmail since its web based. Will look into this but would still prefer the script for general geek-factor ;)

Can you set up mail forwarding in Hotmail? If so, just make a gmail account and forward it there. Then you can use Thunderbird/Evolution.

---

### Post by Paqman on 2010-03-23
> **r-senior said:**
> Are you managing to do this Paqman?

I used to, I've discarded my old Hotmail account now.

Microsoft finally relented and allowed POP3 access to Hotmail a couple of years ago.

---


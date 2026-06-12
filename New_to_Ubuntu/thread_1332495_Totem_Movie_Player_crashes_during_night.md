---
title: "Totem Movie Player crashes during night"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Herukam on 2009-11-20
Hello,

I upgraded Ubuntu 9.04 to 9.10 just recently on my wife's pc. She usually puts on a movie before going to bed and leaves it on while she fells asleep. Before the upgrade Totem worked well but after the upgrade the movie player has crashed during every night it has been on and it won't shut down unless the pc is rebooted and the Totem force quit while at it. It doesn't even recover from full screen.

Why is this happening and what different is in 9.10 that brings out this problem?

What can I do to fix this issue?

Thank you for your answers in advance and I will try to remember check this thread daily to give you more details if needed.

H

---

### Post by dca on 2009-11-20
You can 'try' reinstalling libdvdcss2 from medibuntu repo and also see if the 'ubuntu-restricted-extras' meta-package updated properly.  See, I'm always leery of doing dist-upgrades because it rarely goes right.  I usually copy all data off to external and perform clean install if I need new functionality that latest version provides...

---

### Post by dca on 2009-11-20
...one other option is still verify libdvdcss2 codec installation and try installing the 'VLC Media Player', I never had any problems with that app...

---

### Post by doas777 on 2009-11-20
> **Herukam said:**
> Hello,

I upgraded Ubuntu 9.04 to 9.10 just recently on my wife's pc. She usually puts on a movie before going to bed and leaves it on while she fells asleep. Before the upgrade Totem worked well but after the upgrade the movie player has crashed during every night it has been on and it won't shut down unless the pc is rebooted and the Totem force quit while at it. It doesn't even recover from full screen.

Why is this happening and what different is in 9.10 that brings out this problem?

What can I do to fix this issue?

Thank you for your answers in advance and I will try to remember check this thread daily to give you more details if needed.

H

I've had problems like that intermittently (once or twice a week) on my media boxes *( 3 completely diff hardware configurations) since Feisty. somthing about the way totem closes streams (especially ones over samba). prolly not a karmic specific issue.

---


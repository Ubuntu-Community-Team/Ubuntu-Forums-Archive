---
title: "packages have been kept back"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-09
why do i get this, not sure when it changed using jaunty, and vlc i don't use mplayer at all. it may have started when i added the nvidia driver 190 which has been the best thing i could have ever done for my pc. 
any ideas? do i need the adobe flashplugin upgrade, i use firefox 3.015 and it is fine for me. the 3.52 never worked correctly.

The following packages have been kept back:
  adobe-flashplugin libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x mplayer mplayer-nogui

---

### Post by ukripper on 2009-12-09
> **DarinB said:**
> why do i get this, not sure when it changed using jaunty, and vlc i don't use mplayer at all. it may have started when i added the nvidia driver 190 which has been the best thing i could have ever done for my pc. 
any ideas? do i need the adobe flashplugin upgrade, i use firefox 3.015 and it is fine for me. the 3.52 never worked correctly.

The following packages have been kept back:
  adobe-flashplugin libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x mplayer mplayer-nogui

in synaptic put in search field adobe-flashplugin and see if has locked sign on it. That would mean that package has been locked at that version and won't receive update for it on your system until you unlock it.

---

### Post by DarinB on 2009-12-09
i do have firefox locked is this related to that?

---

### Post by ukripper on 2009-12-09
> **DarinB said:**
> i do have firefox locked is this related to that?

Could be because of common dependencies flash and firefox share. you can try yourself. Just unlock firefox and see if flashplayer updates.

---

### Post by wojox on 2009-12-09
When I have that problem I do:

```
sudo apt-get dist-upgrade
```

Do you have DeVeDe installed. Those usually are what the mplayer upgrades are for.

---

### Post by DarinB on 2009-12-09
yeah, that will not happen i am choosing to skip karmic, i am considering lucid next summer once the bugs are worked out too many things have been changed or left out of karmic to make me want to go through that. i am really working really well with jaunty and it has been a four month process to get all the bugs out. therefore i am staying put. if the flashplugin will really improve things then i will consider it but if it breaks my firefox then i will be really unhappy. Is there a reason to upgrade the adobe flashplugin? i know it has been buggy for a while choppy in hd and full screen mode

---


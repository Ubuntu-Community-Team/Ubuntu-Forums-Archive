---
title: "can't play real media fikes in totem"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by powel212 on 2009-03-12
Can't play real media files in 64 bit ibex,

i installed the codecs but still won't play real media files in totem

powel

---

### Post by kimikrishna on 2009-03-12
why dont you try VLC  ? 
i think that it plays almost everything....!! 

Its in reps..

system > administration > synpatic 
search for vlc .... ! and install

---

### Post by powel212 on 2009-03-12
Thanks

VLC is playing everything but real media files. I think I am having some problem internally with the codecs linkage. So far it's beyond me.

Powel

---

### Post by Berserker v7 on 2009-03-12
MPlayer plays real files... its available in the repos...

---

### Post by powel212 on 2009-03-12
Yes, this is why it is so troublesome. for some reason mplyer won't play the r-m files either. I'm hoping someone can help me rebuild the connections between the codecs and the players.

Thanks

---

### Post by LowSky on 2009-03-12
what codes did you install?
Did you install the w64codec package?

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64 codecs/w64codecs_20071007-0medibuntu1_amd64.deb

sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

you can also install realplayer..
[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

---

### Post by powel212 on 2009-03-12
Thank you

Returned:

$ wget -c [http://packages.medibuntu.org/pool/non-free/w/w64](http://packages.medibuntu.org/pool/non-free/w/w64) codecs/w64codecs_20071007-0medibuntu1_amd64.deb
--2009-03-12 23:02:20--  [http://packages.medibuntu.org/pool/non-free/w/w64](http://packages.medibuntu.org/pool/non-free/w/w64)
Resolving packages.medibuntu.org... 88.191.79.39, 88.191.82.11, 91.121.62.209
Connecting to packages.medibuntu.org|88.191.79.39|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-12 23:02:21 ERROR 404: Not Found.

--2009-03-12 23:02:21--  [http://codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
Resolving codecs... failed: Name or service not known.
wget: unable to resolve host address `codecs'

I have the realplayer installed and it plays the real player files but I had it working in totem on ibex 32bit. I just can't figure out what I have done wrong this time.

Thank you

---

### Post by powel212 on 2009-03-12
Tried it again without one "space"

Returned:

$ wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
--2009-03-12 23:08:42--  [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 91.121.62.209, 88.191.79.39, 88.191.82.11
Connecting to packages.medibuntu.org|91.121.62.209|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

The codecs is in. But totem seems not to be reading it.

I can't figure it out.

Thank you

---

### Post by powel212 on 2009-03-14
I added unsuported intrepid repository and ran an update and now RMVB files are playing in MPlayer. Yippee. But still not in Totem. I can live with this. But if anyone has a similar problem and figures out how to get RMVB files working in Totem please let me know.

Powel

---


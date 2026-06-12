---
title: "TV Tuner Woes"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by TRJOHN on 2011-02-28
I am a beginner, runnung ubuntu and Windows 7 on the same machine. My current issue is that Idont know how to set up the tv tuner used by windows for ububtu.(WINFAST DTV1000 S)

Can anybody help?

---

### Post by turtle153 on 2011-02-28
Try the package tvtime:
```

sudo apt-get tvtime

```
It should automatically work with most TV cards

---

### Post by Jose Catre-Vandis on 2011-02-28
> **turtle153 said:**
> Try the package tvtime:
```

sudo apt-get tvtime

```
It should automatically work with most TV cards
^
^
If its an analog tv card?

Can you describe your tv device, internal, external, dvb, analog, make, model, serial etc?

Let's see if your card is recognised first, in a terminal type:
```
lspci -v
``` if tv card is internal, otherwise ```
lsusb && lsusb -v
```
You should find your card listed, report that back here.
Also (assuming card does dvb tv) in a terminal type:
```
dmesg | grep dvb
```
and report this back

---


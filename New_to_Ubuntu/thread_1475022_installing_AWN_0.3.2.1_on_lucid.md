---
title: "installing AWN 0.3.2.1 on lucid"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by nilsolaris on 2010-05-06
Ive been using AWN 0.3.2.1 on karmic for a while now and on the update to lucid it was updated to 0.4.0 which I find to be buggy. how can I install 0.3.2.1 on again? any help would be highly appreciated !

---

### Post by -humanaut- on 2010-05-06
I'd purge it with apt then enable the Karmic Repo's in the /etc/apt/sources.list then you should be able to download the 0.3 version through synaptic.

---

### Post by Sealbhach on 2010-05-06
> **-humanaut- said:**
> I'd purge it with apt then enable the Karmic Repo's in the /etc/apt/sources.list then you should be able to download the 0.3 version through synaptic.

Be careful though, make sure you remove the Karmic repos after you've got awn 0.3 and run sudo apt-get update.

Otherwise this can cause a lot of trouble for your system.

.

---

### Post by nilsolaris on 2010-05-06
> **-humanaut- said:**
> I'd purge it with apt then enable the Karmic Repo's in the /etc/apt/sources.list then you should be able to download the 0.3 version through synaptic.

Sorry to keep this going but im not sure exactly how to do this.

---

### Post by -humanaut- on 2010-05-06
Google karmics repo's I'm not sure excatly what they are but heres what you have to do

First sudo apt-get purge awn-4.whatever.else
open a terminal and type: sudo nano /etc/apt/sources.list
copy the karmic repo's into the sources.list then
sudo apt-get update then launch synaptic and download AWN after you download it do
sudo nano /etc/apt/sources.list and Remove the karmic repos then sudo apt-get update

and your done. 

DO NOT sudo apt-get upgrade with karmic repos!!!

---


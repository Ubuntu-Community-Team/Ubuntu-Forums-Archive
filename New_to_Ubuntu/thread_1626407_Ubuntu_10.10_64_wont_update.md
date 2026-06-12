---
title: "Ubuntu 10.10 64 wont update"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by gdbutcher on 2010-11-20
Hi I cant update Ubuntu 10.10. It has something to do with 2 games Skull Tag and Eduke32 but I dont know how to fix it.

In update manager i get the following message when i click on install updates:

Requires installation of untrusted packages

details:- eduke32 skulltag skulltag-client skulltag-data skulltag-data-announcer skulltag-data-extraskins skulltag-pk3 skulltag-server

Can you help me fix this please?

---

### Post by acrazyplayer on 2010-11-20
try using synaptic over update manager, just open up synaptic and click "reload" then click "mark all upgrades" and then apply. if you that still doesnt work then ill give you some terminal commands to try

---

### Post by sikander3786 on 2010-11-20
Seems like you've added some custom PPAs and the updates are coming from those sources and Ubuntu obviously doesn't trust external sources.

You can apply updates if you trust the sources yourself or go to Software Center > Edit > Software Sources > Other Software Tab and disable any additional sources before updating again.

Good Luck!

---

### Post by Hippytaff on 2010-11-20
Also you can add the key, then ubuntu knows it's a trusted ppa, though you'll need to find out the keyserver and the key hash (which should be present in the error message)

```

apt-key adv --keyserver --recv-keys keyid

```
where keyserver is the name of the keyserver and keyid is that key hash...admittedly it can be a pain to find this info if it isn't present in the error message :-)

---


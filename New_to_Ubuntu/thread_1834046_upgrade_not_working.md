---
title: "upgrade not working"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by idom on 2011-08-26
I am using 10.04 LTS and I tried to upgrade using update manager after some long time.


It showed warning saying that 
Not all updates can be installed  try running partial updates. 
gave some four reasons for why this can happen. 

I ran partial upgrade and  it is giving me following errors


The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_10.3.183.4-0lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_10.3.183.4-0lucid1_i386.deb) 404  Not Found


Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.4-0lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.4-0lucid1_i386.deb) 404  Not Found


adobe-flash-properties-gtk_10.3.183.7 is the only thing available there 

help is appreciated.

idom

---

### Post by idom on 2011-08-27
thanks. checked and it worked.

Samarth

---

### Post by hansdown on 2011-08-27
Hi idom.

You need to check your update settings.

Please click, 

system >administration>software sources>updates.

On the bottom, under "release upgrades"', if it says...

"long term support releases only",

change it to...

normal releases.

---

### Post by idom on 2011-08-27
> **hansdown said:**
> Hi idom.

You need to check your update settings.

Please click, 

system >administration>software sources>updates.

On the bottom, under "release upgrades"', if it says...

"long term support releases only",

change it to...

normal releases.

yes it is long term releases only and I want it that way only. still my update manager was showing some update.

idom

---


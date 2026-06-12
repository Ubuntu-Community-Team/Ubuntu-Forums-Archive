---
title: "19 hour updates?"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-10-31
I'm having a great deal of difficulty with the update manager of late. I've now got this Huge list of updates to do but they simply will not download. I left it downloading overnight and it didn't get the updates, rather it errored with a midsum mismatch. 

I checked with speedtest.net - my download speed is as it should be. 

A Lot of these updates seem unnecessary to me, but I'm no expert. I'm running Karmic and do not wish to change at this point. My questions - is it trying to upgrade me to another version or something? (I did not check that at the top of the manager) or is it giving me updates for another version? 

Anyone else having these difficulties? 

mystmaiden

---

### Post by TeoBigusGeekus on 2010-10-31
Go to Administration>System>Software Sources and change your server. Or even better, let ubuntu run a test and decide which is the best one.

---

### Post by kaldor on 2010-10-31
> **TeoBigusGeekus said:**
> Go to Administration>System>Software Sources and change your server. Or even better, let ubuntu run a test and decide which is the best one.

This. I had this issue when I first installed LMDE and the servers chosen were waaaay too far away. I switched to a closer mirror, and everything sped up.

Sometimes the OS doesn't choose the best server for you :)

---

### Post by mystmaiden on 2010-11-02
Thanks so much! Somehow, it was set to the server in Mexico, and I'm in the US. I switched it and it is cooking along much more quickly. I'm not sure how to have Ubuntu test to see which server is best though...

mystmaiden

---

### Post by coffeecat on 2010-11-02
> **mystmaiden said:**
>  I'm not sure how to have Ubuntu test to see which server is best though...

Synaptic > Settings > Repositories > Click on dropdown list by 'Download from' and choose Other > Click on 'Select Best Server'.

---


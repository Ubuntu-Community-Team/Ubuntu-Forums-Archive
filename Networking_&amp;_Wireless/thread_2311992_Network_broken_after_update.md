---
title: "Network broken after update"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by e1ektrob0y on 2016-02-01
I just booted up my old pc and the network is not working. There is no logo for the wired network even though the cable is plugged in and nothing has changed. I plugged in a usb wireless adapter that used to work but the light doesn't even go on. When i open network i just get a message that says 
"the system network services are not compatible with this version"
I think this has been caused by an update but I'm not 100 percent sure...

---

### Post by batden on 2016-02-01
Same thing here, network-manager is broken (trusty).

---

### Post by e1ektrob0y on 2016-02-01
So how do we fix this?

---

### Post by ajgreeny on 2016-02-01
If you have the proposed repos enabled in Software-sources Update tab see [http://ubuntuforums.org/showthread.php?t=2311727&p=13431415#post13431415](http://ubuntuforums.org/showthread.php?t=2311727&p=13431415#post13431415) and follow the instruction there.

I'm not sure if the problem has been solved with another update in the proposed repos, but I think I did read that somewhere, so if you have a cable ethernet connection available you may find that another update will overcome the problem for you. If it doesn't you will have to disable the proposed repos and downgrade the packages mentioned in that linked thread.

Using proposed repos is always risky and should not be done unless you know how to mend a broken system.

---

### Post by e1ektrob0y on 2016-02-01
> **ajgreeny said:**
> If you have the proposed repos enabled in Software-sources Update tab see [http://ubuntuforums.org/showthread.php?t=2311727&p=13431415#post13431415](http://ubuntuforums.org/showthread.php?t=2311727&p=13431415#post13431415) and follow the instruction there.

I'm not sure if the problem has been solved with another update in the proposed repos, but I think I did read that somewhere, so if you have a cable ethernet connection available you may find that another update will overcome the problem for you. If it doesn't you will have to disable the proposed repos and downgrade the packages mentioned in that linked thread.

Using proposed repos is always risky and should not be done unless you know how to mend a broken system.

Yep that fixed it. Thanks! I'll be disabling the proposed repos now...

---


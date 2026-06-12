---
title: "pidgin 2.5"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Smaydie on 2008-12-22
Out of the blue pidgin wouldn't work on my computer. (I'm running Hardy) Not working entails it opening then disappearing leaving a gap on the upper bar where usually there would be an icon. I was told to upgrade it and I was given this link [http://nancib.wordpress.com/2008/08/25/get-pidgin-25-for-ubuntu-hardy/](http://nancib.wordpress.com/2008/08/25/get-pidgin-25-for-ubuntu-hardy/) I tried it with no success. Please Help if you can, Thank You.

---

### Post by InfectedWithDrew on 2008-12-22
Hey, I'm the one who helped her.

I'd like to mention that System Monitor said that the process was "running" but never reached "sleeping."

EDIT: Also, she was using... what's the version that comes with Hardy, 2.4.x?  That was the version that broke.  I figured an upgrade might fix any dependencies or deleted data.

---

### Post by nhasian on 2008-12-22
i have Pidgin 2.5.2 in Ubuntu 8.10 Intrepid Ibex.  If you enable the backports repository will it upgrade you to the latest version?

System -> Administration -> Software Sources click on the Updates tab, then Hardy-Backports

---

### Post by k3lt01 on 2008-12-22
Go [here]("http://www.getdeb.net/app/Pidgin") and download the files listed under your version of Ubuntu. When you have done that uninstall the version of Pidgin you have got on your system and then install the files you just downloaded.

---

### Post by InfectedWithDrew on 2008-12-22
> **k3lt01 said:**
> Go [here]("http://www.getdeb.net/app/Pidgin") and download the files listed under your version of Ubuntu. When you have done that uninstall the version of Pidgin you have got on your system and then install the files you just downloaded.That link she posted tells her to do just that.  Meaning, that's already been done.

---

### Post by atngplusultra on 2008-12-22
try opening Synaptic, doing a "complete removal," then reinstalling altogether, to the newest version? I've done that.

---

### Post by Smaydie on 2008-12-22
> **nhasian said:**
> i have Pidgin 2.5.2 in Ubuntu 8.10 Intrepid Ibex.  If you enable the backports repository will it upgrade you to the latest version?

System -> Administration -> Software Sources click on the Updates tab, then Hardy-Backports

i did that, restarted and then did sudo apt-get update and it didn't help.

---

### Post by Smaydie on 2008-12-22
> **atngplusultra said:**
> try opening Synaptic, doing a "complete removal," then reinstalling altogether, to the newest version? I've done that.

i did the complete removal by opening Synaptic, right clicked the check boxes for pidgin and pidgin-data and clicked compete removal, each had another package connected (to pidgin was gfire and to pidgin-data was libpurple) after they were highlighted for complete removal i clicked apply and it seemed as though it was working and then it looked the same after it was done seemingly working. I'm not familiar with Synaptic, so it may have worked it may have not. But nothing has seemed to change.

---

### Post by atngplusultra on 2008-12-22
> **Smaydie said:**
> i did the complete removal by opening Synaptic, right clicked the check boxes for pidgin and pidgin-data and clicked compete removal, each had another package connected (to pidgin was gfire and to pidgin-data was libpurple) after they were highlighted for complete removal i clicked apply and it seemed as though it was working and then it looked the same after it was done seemingly working. I'm not familiar with Synaptic, so it may have worked it may have not. But nothing has seemed to change.

now try to install Pidgin 2.5 (and all of the other packages that come with it) via Synaptic, hopefully, that will do something.

---

### Post by k3lt01 on 2008-12-24
> **InfectedWithDrew said:**
> That link she posted tells her to do just that.  Meaning, that's already been done.That link she posted isn't to the link I posted, meaning you haven't done what I suggested. The link I posted is to GetDeb not some blog. So again you will need to ***_completely_*** remove the current version of Pidgin (and its associated files)and not just remove so go to Synaptic and click ***_Completely Remove_*** and then do the same for the associated files. Download the new versions from GetDeb and install them. If then you have any trouble tell me you have already done it.

---


---
title: "Cant activate Broadcom STA driver after upgrading to 2.6.23 Kernel"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by houserparker on 2009-11-11
Can somebody please help? There are hundreds of cases of people no being able to activate broadcom STA driver but as usual nobody has found a satifactory solution.

I updated to 2.6.32 Kernel to get open source ATI drivers drivers working which worked but now i have tried everything and cant get the STA driver working again.

---

### Post by houserparker on 2009-11-11
Does anyone have any ideas. The drivers are installed i just cant activate it through the jockey gui. There must be a way of manually activating it through the terminal.

Thanks in advance.

---

### Post by thinktyler on 2009-12-04
Ya man I with you. This was a problem in the karmic BETA. I remember reading some sort of solution, but I became frustrated and uninstalled. I'll try and search it. Let me know if you find anything. I'm going to wonder in the IRC and see what I can find.

---

### Post by sandyd on 2009-12-04
```

gksudo gedit /etc/modules

```

add "wl"
on a few line.
save and restart

if that doesnt work, install bcm4xx-fwcutter.

---

### Post by dynamic.flare on 2009-12-05
can someone tell me if this worked for them?

---

### Post by andrew.46 on 2009-12-05
Hi houserparker,

I can be of little help here as I still use the older b43cutter method that carlee mentioned. But [a few people]("http://www.linuxquestions.org/questions/slackware-14/broadcom-bcm-4312-in-slackware-64-13-770837/") have found that wlan0 has been identified as eth1 when using the STA driver. This might be worth looking into?

Andrew

---

### Post by hackenpete on 2009-12-05
Hi,

I encountered the same problems but could fix it, with installing the package "bcmwl-kernel-source" from Lucid [http://packages.ubuntu.com/lucid/i386/bcmwl-kernel-source/download. ]("http://packages.ubuntu.com/lucid/i386/bcmwl-kernel-source/download")
After installing it, I upgraded to the newest 2.6.32 kernel and wifi worked. 
Good luck!

---

### Post by sandyd on 2009-12-05
some maintainer/developer updated the fwcutter package so that it downloads the wl source instead of the standard broadcom sources.
 
it installs wl since... jaunty? i think.
i could teach you the hard way bc i installed it using the hard way, but ill only do it if everything wont work.

---


---
title: "Fix graphics controller issue"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by flattoprn on 2010-09-25
I have dual boot Ubuntu and Windows.  Everything seems to be working fine except the graphics - the screen is very fuzzy.  I have searched for hours to fix this issue and tried several times but cannot get the correct drivers installed.  Here is the graphics info:
*-pci
          description: Host bridge
          product: System Controller Hub (SCH Poulsbo)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: System Controller Hub (SCH Poulsbo) Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             

Thank you for any help!

Be well.

---

### Post by mikewhatever on 2010-09-25
Check out the wiki page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

and the megathread for discussions:
[http://ubuntuforums.org/showthread.php?t=1229345&page=201&highlight=gma500](http://ubuntuforums.org/showthread.php?t=1229345&page=201&highlight=gma500)

---

### Post by sandyd on 2010-09-25
> **flattoprn said:**
> I have dual boot Ubuntu and Windows.  Everything seems to be working fine except the graphics - the screen is very fuzzy.  I have searched for hours to fix this issue and tried several times but cannot get the correct drivers installed.  Here is the graphics info:
*-pci
          description: Host bridge
          product: System Controller Hub (SCH Poulsbo)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: System Controller Hub (SCH Poulsbo) Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             

Thank you for any help!

Be well.
try this.
```

sudo add-apt-repository [B]ppa:lucazade/poulsbo-lucid-fix
sudo apt-get update
sudo apt-get install [/B]xserver-xorg-video-psb xpsb-glx                 psb-meta                  psb-kernel-source                  psb-firmwareppa-purge                 poulsbo-config                  libdrm-poulsbo
```

---

### Post by flattoprn on 2010-09-25
Sandy,
That fix completely hosed my system.  I can no longer log into Ubuntu - even the recovery mode doesn't work.

---

### Post by sandyd on 2010-09-25
> **flattoprn said:**
> Sandy,
That fix completely hosed my system.  I can no longer log into Ubuntu - even the recovery mode doesn't work.
then you have to use ppa-purge to remove it from either a livecd, or by pressing alt+f1 when you finish booting up.
```

sudo ppa-purge ppa:lucazade/poulsbo-lucid-fix[B][FONT=monospace]
[/FONT]
```
[/B]

---

### Post by flattoprn on 2010-09-25
Thanks for the replay - but due to my impatience I already tried to reinstall Ubuntu.  Of course due to my n00bness I have jacked up the disc and now cannot reclame some space.  I feel another posting coming up :-)

---

### Post by lucazade on 2010-09-26
> **flattoprn said:**
> Sandy,
That fix completely hosed my system.  I can no longer log into Ubuntu - even the recovery mode doesn't work.

What fix are you talking about??

---


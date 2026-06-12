---
title: "Running 8.10 and can't update"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by The_Proffessor on 2010-12-20
Ok, I haven't been able to update my OS for a month now. The repository address is wrong and I have no idea how to fix it. So 2 questions:

does 9.04 or any later versions support ATI graphics cards yet? or

What code do I put into the terminal to fix the dang repository so I can get updates again?

---

### Post by BbUiDgZ on 2010-12-20
is 8.10 still supported?
I run 8.04 for hardware support for a raddon x600 - this is more a ATI issue rather than a ubuntu issue. I'm sure if the ati drivers were open source we'd have full support in new versions of ubuntu.

You might want to consider changing for a nvidia card

---

### Post by The_Proffessor on 2010-12-20
crap, it's a laptop so I can't really upgrade the video card (so sayeth the folks at Geek Squad when I took it in there). The only really crappy part is I want to get addblocker for my firefox, to do that I need the latest version of firefox, and my add/remove application (which updates all my programs it seems) doesn't work without these new repository addresses. I can't update anything at all.

---

### Post by MooPi on 2010-12-20
You may want to try a newer version. What is the ATI card, ```
sudo lshw -C display
```

---

### Post by Sylos on 2010-12-20
Hello.
You could try and see if firefox have a .deb package on their website and try installing from that. You will probabbly encounter some unmet dependencies along the way but they may be resolvable with some googling. Only way is to try.

Also: the reason for the repo address being rejected is because the repos are shut down following end of life for that edition. I think this has now happened.

EDIT: They have a tarball located here that you could try to compile from.
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

EDIT 2: adding these repo entries may still work too (for firefox only)

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main

---

### Post by The_Proffessor on 2010-12-20
*-display               
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx

---

### Post by MooPi on 2010-12-20
It looks as if your at the end of the road for your video card and OS. Version 8.10 is no longer supported and Radeon Xpress 200M is not being supported on newer versions officially.

---

### Post by The_Proffessor on 2010-12-20
ugh...nothing to be done for my firefox besides go slogging back to Windows Vista then? le sigh...

---

### Post by MooPi on 2010-12-20
You can use a later version of Ubuntu but you'll have to depend on the opensource drivers which lack 3D acceleration. If you don't need that you'll be fine using 9.04 or later. I'd suggest going with 10.04 to get the longest window of support for your software. Version 9.10 seems to support your card best though.

---

### Post by mastablasta on 2010-12-20
why not first download Ubuntu 10.10 (for latest open source drivers) and try it in live session to see if it works ok or not.
 
EDIT: apparently 10.04 LTS version works better with your card, see here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1617994](http://www.uluga.ubuntuforums.org/showthread.php?t=1617994)
EDIT2: Some users had a great experience on Ubuntu 10.10 as well see here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1598976](http://www.uluga.ubuntuforums.org/showthread.php?t=1598976)
 
You will likely need to do a fresh install of the OS.
 
i don't know how good is support for ATI mobile cards, but my ATI rage 16MB worked just fine. i now changed it with newer (but sitll old and on opensoruce) Radeon 9600XT 256 MB.

---


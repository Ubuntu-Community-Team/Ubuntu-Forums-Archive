---
title: "bittorrent client &amp; program storage locations"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by DennyF on 2011-02-19
Since I'm new at this, I need to know how to set Deluge as my default BitTorrent client. Ubuntu wants to use Transmission but I prefer Deluge as it is fairly identical to the one used in Windows, which I'm used to, plus, it downloads a lot faster. And, yes, I mapped the port already. While we're at it, where does Ubuntu store programs? If I knew that, I could set the default via Firefox but I have no idea where Deluge is stored in the file system. Thanks for your "newbie" indulgence.

---

### Post by mikewhatever on 2011-02-22
The executables are usually stored in /usr/bin, so the path for deluge should be /usr/bin/deluge.

---

### Post by aeiah on 2011-02-22
firefox should obey your environment settings so you could do it another way. save a .torrent and right-click it, go to properties and set it to open with deluge by default.

---

### Post by seawolf167 on 2011-02-22
Just to add, you can locate where the binary has been placed with the *which *command

```
which deluge
```

this will search the directories in your PATH variable

---

### Post by DennyF on 2011-02-22
You guys are great, thanks so much. All these tips should get me on the fast track with Ubuntu/Linux. As an old DOSer, I was fairly adept at command line functions and the whereabouts of most programs and device drivers. Hope to get up to speed with this system ASAP. I find it a lot more efficient than Windows, which just keeps getting clunkier and clunkier, despite its Glam. Ubuntu really pumped new life into my old Pentium 4 - can't believe its the same machine, it's so fast now.

---


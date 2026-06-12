---
title: "Cleaned my video card, now NTLDR is missing"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by tweaked on 2011-09-02
All I did was clean the lint from my video card, I swear it's true!

Have been running this install of 10.04 for almost a year. It is setup dual boot with WIN7, which we have never used. 1 SATA drive. Today I removed my video card , reinstalled it and now I get "NTLDR is missing, press ctl-alt-del"
Seems GRUB is screwed up?

Crap, any ideas what happened?

---

### Post by lisati on 2011-09-02
Did you make a system recovery/rescue disk when you first got Win7?

---

### Post by tweaked on 2011-09-02
No. 

I really don't care about Windows, I am not even getting a grub menu when booting.

---

### Post by 2F4U on 2011-09-03
Is it possible that some cable got loose while removing or reinserting the graphics card? I would check all cables in the machine and in particular the cables attached to the hard drive.

---

### Post by tweaked on 2011-09-03
Yes, I did that. The hard drive shows up in bios. Tried multiple times. I'm thinking I had some problem with the video first few boots and probably hit the power switch at the wrong time, unable to see. Probably corrupted Grub.

---

### Post by oldfred on 2011-09-03
The ntldr missing is a windows boot error not related to grub. Did you change drive order and now BIOS is booting a Windows drive's MBR?

Post this from liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by lkraemer on 2011-09-03
> 
I'm thinking I had some problem with the video first few boots and........
If this was the case I'd bet your Video Card isn't seated properly.  Why not
remove it again and carefully re-seat it.  Then try booting.

lk

---


---
title: "ACL 888 sound card help?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Sgt Sc0rpi0n on 2009-01-21
I'm new to Ubuntu and I'm having trouble getting my OS to recognize my sound card. Another thread suggested I add:

```
options snd-hda-intel probe_mask=1
```

to the end of my alsa-base file.

When I tried to do that it tells me I don't have permissions to alter file.  How do I change permissions on this file to add the line.  

any suggestions?

---

### Post by handydan918 on 2009-01-21
> **Sgt Sc0rpi0n said:**
> I'm new to Ubuntu and I'm having trouble getting my OS to recognize my sound card. Another thread suggested I add:

```
options snd-hda-intel probe_mask=1
```

to the end of my alsa-base file.

When I tried to do that it tells me I don't have permissions to alter file.  How do I change permissions on this file to add the line.  

any suggestions?
Try 
```
sudo options snd-hda-intel probe_mask=1
```

---


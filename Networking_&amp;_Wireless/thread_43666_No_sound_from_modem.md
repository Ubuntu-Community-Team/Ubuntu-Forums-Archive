---
title: "No sound from modem"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by xoros on 2005-06-22
Well now that I have my nvidia 10de:00d9 modem working it connects fine but there never is any sound. 

I tried to change /etc/chatscripts/provider 
the line with ATDT i put ATL2DT (for medium volume)  

That still did not give me any modem sound.  

Any suggestions ?

---

### Post by xoros on 2005-06-22
After doing more digging I found I was getting this message in syslog: 
"semaphore is not ready for register 0x54"  which may be related to the sound problem...  odd though, I do have sound otherwise. 

This was suggested as a solution:

> In your /etc/hotplug/blacklist file, add snd-intel8x0m, then save and restart.

# alsaconf
again and then set my mixer settings:
# alsamixer
then
# alsactl store
again.

---

### Post by xoros on 2005-06-23
well snd-intel8x0m was already in there.  tried all the alsa settings too.  

still no sound from modem.

---


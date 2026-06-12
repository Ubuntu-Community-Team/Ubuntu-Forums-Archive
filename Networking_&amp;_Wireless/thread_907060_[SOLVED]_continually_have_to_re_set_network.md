---
title: "[SOLVED] continually have to re set network"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-09-01
Hi guys,

I jdid a clean install of Hardy onto my laptop a few days ago. I have a wireless connection to my router, with a static IP address on the laptop.

Since loading the new OS, whenever I boot for the first time, and try to connect it won't. I cannot ping the router at all. 

I open network manager, go to properties for the wireless network, delete out the WPA key, re enter it, then close the dialogue, It resets and away I go.

The stupid thing is, the key is not missing or anything when I go in, so why is the network not setting correctly?

Any solutions, very gratefully received, as she that rules is about to make me into a squeaky voiced old man, if I cannot put HER computer to rights. 

:lolflag::lolflag:

---

### Post by tropdoug on 2008-09-02
Bump

---

### Post by tropdoug on 2008-09-05
Bump bump

---

### Post by Iowan on 2008-09-05
I don't (yet) do wireless, but...
Gotta wonder if WPA key is somehow corrupt.

---

### Post by tropdoug on 2008-09-05
Don't think so, because the desktop machine is connected using the same WPA key and has no issues. The only difference is its hard wired to the router.

Its bizarre

---

### Post by jimmgunnz on 2008-09-05
hey there troupdog...

i have a weird wireless setup as well.  i get mine to work every time tho, through a little manual configuration trickery i stumbled upon.  i have my home network saved as a setting, with the encryption key and all.  the weird thing is, it never works right away for me either.  however, i also have a setting that is for roaming mode saved.  

here's the weirdness.

i need to just toggle.  i change the setting to roaming and let it do its thing.  then i change the setting back to my home network and let it reconfigure its settings and BAM!!  internet.  

it certainly doesn't make any sense, but it's worked every time for me.  i dunno if you'd have the same luck, but it kinda sounds like the same type of thing... it just needs to reconfigure itself.  it would at least save you from having to re-enter your key every time...

.

---

### Post by jimmgunnz on 2008-09-05
make that  *tropdoug.... whoa dyslexia

sorry =]

---

### Post by tropdoug on 2008-09-06
whats in a name lol. 

Jimmgunnz that works as well, so it seems that there is an issue with some setups for wireless on Hardy. I did not have the issue on gutsy. 

I wonder if one of the wireless guru's here might try to help? 

Just in case - what sort of router and model are you using?

---

### Post by jimmgunnz on 2008-09-06
my router is a linksys wireless g, model is wrt54g...

yeah, there's definitely some weird buggyness happening.  
this is the first version i've tried though, so i've nothing to compare it to.
but hey, from the looks of it, we're lucky to achieve wireless at all =]
there seem to be TONS of issues.
just many functioning properly as well, but definitely tons of issues.
that would be pretty rad if there was a fix though!

---

### Post by tropdoug on 2008-09-07
Seems that there have been a lot of people viewing this, but ony you have answered. Perhaps this is a bug that needs a different forum. I am going to ask for help in the general forum, to see if we can get an answer. 

Your router is different to mine, I am using a D-Link. VOIP router so the issue is not in the router type. 

Lets see what we can find out.

Douglas

---

### Post by tropdoug on 2008-09-07
Hey Jim

I think I found a solution, the problem appears to be with the default network manager, if you replace it with Wicd the problem disappears. 

Follow the instructions here ```
http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04
```

the only thing I did not do was set for an auto login, as I dislike the loss of security that an auto login entails. 

Have fun with Linux, it's a fantastic system, and a great community.

Douglas

---


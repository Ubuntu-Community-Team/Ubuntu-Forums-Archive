---
title: "unable to detect my new wireless gateway"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by akkad on 2009-04-15
i replaced my old wireless gateway with a new one, i gave the same SSID name to the new wireless network, now i can not detect my wireless network where i can detect other networks except my own, i have a dual boot system so i booted to windows where i was able to connect to the new gateway so it is working, but it seems i have a problem on ubuntu 8.10, i think it might be the gnome network manager cause i used to have some hangs and network problems from gnome network tool, so far i tried "iwlist scanning" and as i told it detected all network except my new gateway, so what do u suggest people ??

---

### Post by mikewhatever on 2009-04-15
What do you mean by wireless gateway? Did you replace your router? One cause of the problem you describe, when all other networks are detected but yours, is the wireless channel. It could be that the new gateway, whatever that is, uses the channel undetectable by the wireless driver in Ubuntu. Try a different channel and see what happens.

---

### Post by akkad on 2009-04-15
how to use another channel?
to be more clearer by what i meant by gateway, simply i was using linksys wireless router, then i brought a new siemens one.

---

### Post by akkad on 2009-04-15
like it used to be happened, it is gnome network manager problem, i removed and installed wicd where its working like a charm.

---


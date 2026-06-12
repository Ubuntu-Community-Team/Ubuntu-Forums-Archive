---
title: "WiFi WEP connection"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by kikapu on 2008-04-25
Hi again.

I downloaded today 8.04 and run it as a Live CD. I want to check that everything is ok before i actually install it permanently. So, i tried to connect to my wireless AP but with no luck. Ubuntu recognizes my wireless card, it shows me the available APs just fine and it asks me for the credentials. So my AP wants a WEP key 128 bits Hex and has an Authentication of type "Open". So i give it to the respective box but it keeps asking me the same thing all over again.

If i go to the "network" at the menu, i can see the network box that display "wireless", "wired" and "modem" connections.
I tried both to set "wireless" to roaming mode and i saw the above behavior. I also tried to give the static ip and DNS that i use in Windows just fine but i cannot connect to it.

I am sure i am doing something wrong here, can anyone helpme with this ? Ori i am not supposed to these things by just running from Live CD (with no changes yet) ?

Thanks (again) for any help!

Ah, my card is an "Intel wireless WiFi L"ink 4965AGN

---

### Post by kikapu on 2008-04-26
Anyone ?? Am i the only person who has problem like this ?
Does Unbuntu have any problems with WEP security or the specified card ?

---

### Post by sbrbot on 2008-04-26
Come on, what you're expecting answer on your question after a minute for distro which is only a day old!?

---

### Post by kikapu on 2008-04-26
> **sbrbot said:**
> Come on, what you're expecting answer on your question after a minute for distro which is only a day old!?

I think that's not the case...I see many other that are complaining for this even from the beta cycle, so it's not an "one minute" problem but several months...

---

### Post by Tom--d on 2008-04-26
It might be WEP which is doing it. 

I had that problem. 
Try manual configuration. That worked for me :) But I think you need to restart tho. On the LiveCD all the changed data is lost. 

There are other ways around this.
Try that at first and see what happenes.

---

### Post by kikapu on 2008-04-26
> **Tom--d said:**
> It might be WEP which is doing it. 

I had that problem. 
Try manual configuration. That worked for me :) But I think you need to restart tho. On the LiveCD all the changed data is lost. 

There are other ways around this.
Try that at first and see what happenes.

Thanks for the help! I was suspecting that by using the Live CD only (and not using an installed OS) will not allow me to do much for this problem.
I already tried (by using Live CD) manual configuration with no luck. I mean, i give static IP, DNS servers, WEP key but it doesn't work..It keeps asking me for a "passphrase"

I will first try the one you said about WEP. I will change it to see. To what i should change it to, WPA AES Key ??

Thanks again!

EDIT: What exactly is "Roaming Mode" in a network connection ??

---


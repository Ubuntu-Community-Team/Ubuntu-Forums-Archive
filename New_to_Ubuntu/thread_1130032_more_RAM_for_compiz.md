---
title: "more RAM for compiz"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-19
Is there any way I can allot more RAM for compiz effects?

---

### Post by Paqman on 2009-04-19
Compiz effects are done through your graphics card. So if you can't get the effects you want, that's the place to look for the bottleneck.

---

### Post by 3rdalbum on 2009-04-19
The Compiz program itself automatically allocates memory as required, just like all programs on all modern operating systems.

Having said that, the memory on your graphics card is much more important to Compiz than your regular memory. If you have an old card, it might be time to look at an upgrade. Or, if your card uses regular desktop DDR2 memory, it might be time to upgrade to one that uses "GDDR" style memory that is designed for graphics cards.

---

### Post by LesterPalooza on 2009-04-19
> **Paqman said:**
> Compiz effects are done through your graphics card. So if you can't get the effects you want, that's the place to look for the bottleneck.

So if I cant get the effects I want, I what?

---

### Post by ELD on 2009-04-19
> **LesterPalooza said:**
> So if I cant get the effects I want, I what?

If you can't get the effects you want it could be a driver issue or your graphics card not supported/too little memory on it.

What card do you have?

---

### Post by LesterPalooza on 2009-04-19
> **ELD said:**
> If you can't get the effects you want it could be a driver issue or your graphics card not supported/too little memory on it.

What card do you have?

NVidia GeForce 8200M G

---

### Post by ELD on 2009-04-19
Hmm have you installed the nvidia drivers via the restricted drivers manager?
That card should be able to handle compiz fine, i had a mich lower nvidia card a while back (a 7 series) and that handled it.

Edit:
System -> Administration -> hardware drivers

---

### Post by LesterPalooza on 2009-04-19
Yes those hardware drivers are enabled and upgraded to version 180 (for NVidia)

when I close and maximize firefox or any other full screeen program, compiz lags like hell... i set the close animation to burn.

---

### Post by 5nak3 on 2009-04-19
could it be a simple mistake of setting the burn effect to last for too long?

I had that problem a while back, i accidentally set the burn effect to last for 500ms and i was wondering why it wasn't working.

If you right click the close effect in the compiz config manager and select to edit it, and set the duration much lower e.g. 100 - 150ms will that sort out the problem?

---

### Post by LesterPalooza on 2009-04-19
> **5nak3 said:**
> could it be a simple mistake of setting the burn effect to last for too long?

I had that problem a while back, i accidentally set the burn effect to last for 500ms and i was wondering why it wasn't working.

If you right click the close effect in the compiz config manager and select to edit it, and set the duration much lower e.g. 100 - 150ms will that sort out the problem?

Reduced animation time from 300 ms to 150 ms. It helped reduce the close animation lag. But the problem is still there...

I noticed that animations go really really smooth when the process "compiz.real" is on the top of my process list (highest memory user to lowest). Is there any way I can always put compiz.real on top of that process list? High Priority maybe?

---

### Post by 3rdalbum on 2009-04-19
In the settings for Burn, you should reduce the number of fire particles or turn off the smoke. Or both.

Burn is a very intensive effect, I'm not surprised that your 8200M is struggling.

---


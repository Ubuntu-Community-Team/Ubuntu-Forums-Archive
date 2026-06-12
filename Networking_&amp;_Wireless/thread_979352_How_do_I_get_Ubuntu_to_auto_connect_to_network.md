---
title: "How do I get Ubuntu to auto connect to network?"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Matthew Wiebelhaus on 2008-11-11
I have to connect to my network by selection connect to a hidden network even though it is not hidden. It is secured. When I log in or turn on my computer how can I get ubuntu to automatically connect?

---

### Post by frankleeee on 2008-11-11
> **Matthew Wiebelhaus said:**
> I have to connect to my network by selection connect to a hidden network even though it is not hidden. It is secured. When I log in or turn on my computer how can I get ubuntu to automatically connect?

Use the manual set up and do not set it to roam in network manager.

---

### Post by Matthew Wiebelhaus on 2008-11-11
> **frankleeee said:**
> Use the manual set up and do not set it to roam in network manager.

How would I go about doing that, Ive just installed Ubuntu I havent used it in over a year?

---

### Post by coolethan on 2008-11-11
in the top right hand corner there should be two little computer looking things right or left click it i think its right and a little options list will appear below it should say manual set up. click that and then under one of the tabs there should be a click box with roam in network beside it. if it is checked uncheck it and set it to automatic something or other. hope this helps

---

### Post by Matthew Wiebelhaus on 2008-11-13
> **coolethan said:**
> in the top right hand corner there should be two little computer looking things right or left click it i think its right and a little options list will appear below it should say manual set up. click that and then under one of the tabs there should be a click box with roam in network beside it. if it is checked uncheck it and set it to automatic something or other. hope this helps

I dont have ethier of those, im using Ubuntu 8.10 is there any other way?

---

### Post by frankleeee on 2008-11-13
> **Matthew Wiebelhaus said:**
> I dont have either of those, im using Ubuntu 8.10 is there any other way?

I have not been able to get either of my laptops to auto connect to my home network in Intrepid, it seems the network manager does not offer the manual setting like the Hardy and earlier distributions. So I just let it use roam and sign in with a key every time I turn them on. I tried wicd (but found it to be buggy on my inspiron 4100),when the network manager applet disappeared and wouldn't reload the applet. So I reloaded network manager and now it works fine, I think probably because wicd removed it completely, and I also changed the 
/etc/network/interfaces to 
auto lo
iface lo inet loopback 

This was still in this gedit menu when I reinstalled the network manager, which now works perfectly so far. Here is the wicd link, but it doesn't do a autostart every time at least when I tried it.
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by coolethan on 2008-11-13
i found using roam mode on 8.04 lagged my computer a little bit. maybe it's my computer, it originally ran window$ 98 *shudder* and its BIOS fails the cutoff by at least 10 years but it runs really great.

---

### Post by frankleeee on 2008-11-13
> **coolethan said:**
> i found using roam mode on 8.04 lagged my computer a little bit. maybe it's my computer, it originally ran window$ 98 *shudder* and its BIOS fails the cutoff by at least 10 years but it runs really great.

Roam runs fast in intrepid on my 2 laptops.

---

### Post by fballem on 2008-11-13
Right click on the two-computer thingie, then select edit connections from the menu. Click on the adapter, then select the Edit button. This should give you the range of options that you can use.

---

### Post by frankleeee on 2008-11-13
> **fballem said:**
> Right click on the two-computer thingie, then select edit connections from the menu. Click on the adapter, then select the Edit button. This should give you the range of options that you can use.

That worked for me, I have several open networks besides my encrypted, and the computer would go straight for the open, which I now have edited to not auto. Thanks

---

### Post by coolethan on 2008-11-13
> **frankleeee said:**
> Roam runs fast in intrepid on my 2 laptops.

its not that it really laged my comp in any significant way but it did lag the mouse a little bit, the mouse would freeze on my screen periodically when i tried to move it and then jump to where i moved it and then 5 minutes later do the same thing.

---

### Post by frankleeee on 2008-11-14
> **coolethan said:**
> its not that it really laged my comp in any significant way but it did lag the mouse a little bit, the mouse would freeze on my screen periodically when i tried to move it and then jump to where i moved it and then 5 minutes later do the same thing.

I don't ever use a mouse on my laptops so I haven't noticed any difference. are you using a wireless mouse.

---

### Post by coolethan on 2008-11-14
> **frankleeee said:**
> I don't ever use a mouse on my laptops so I haven't noticed any difference. are you using a wireless mouse.

no wireless mouse, i'm still pretty old school with with my wired mouse, it's not even optical either. haha but i don't need to set roam on anyways so it doesn't bother me.

---


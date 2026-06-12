---
title: "Setting Up a Netgear WG111v2 (ndisgtk not there)"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Dishon on 2008-05-31
I have just loaded Ubuntu 8LTS as a dual boot to test it.

However, I tried to follow the documentation for using a Windows driver for my wireless card and it said to "Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager)."

This object is not listed under ALL. Is there a loction where a I can get missing objects and where should I load save on the Ubuntu file structure?

Thanks

---

### Post by sennep on 2008-06-04
The ubuntu cd has to be in the computer, and you might have to enable the cd as a source for getting ndisgtk. Inside Synaptic, you can find some preferences somewhere that let's you set what can be used as software sources, inside that menu you should enable the ubuntu CD. Do that and try to search for ndisgtk again.

---

### Post by Dishon on 2008-06-10
Thanks.

I got the ndisgtk loaded and the wireless card working. Well when I say working, I can see the other wireless networks in the surrounding area but I can't see mine. I had a quick look at the router 13 and 15 but must have missed it so I'll read it next time I get five minutes.

My router is a Neatgear DG834Gv3. The SSID was hidden but is now visable and my laptop and the laptop this is dual booted from can both see and connect to it.

---

### Post by sennep on 2008-06-13
the wg111v2 is a tricky one unfortunately. I have only been able to make it work in 7.10, but for some strange reason the excact same method to make work in 7.10 doesn't work in 8.04. It might work with WEP though, I have only tried with WPA. If you figure out how to make it work in 8.04 then please post the solution.

Some people have run into problems with hidden networks and ndiswrapper, so the general advice is to make sure the network is not hidden.

---


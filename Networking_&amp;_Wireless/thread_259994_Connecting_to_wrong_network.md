---
title: "Connecting to wrong network"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Sionide on 2006-09-18
How do I make sure my network-manager connects to my wireless AP and only mine?

There are a couple of others in the neighbourhood, 'belkin54g' and 'linksys' and for some reason - perhaps because I have successfully connected to these networks before ( ;) ) whenever I lose connetivity with my own AP, it automatically connects to the next available one out of belkin or linksys which obviously means I lose Internet. :(

Is there any way to make it "forget" about those other networks and automatically try and connect back to my own AP which it will always be able to connect to... Hrm.

I liked the older versions of network-manager much better, the list doesn't even come up anymore with my access point on - I always have manually input the ESSID which is rubbish. Aaaanyway, how can I make it "forget" other networks??

---

### Post by hat403781 on 2007-12-21
I am bumping this thread because I am having the same problem. My wireless network has WEP protection on it, and my neighbors does not. When I boot my computer, it will always automatically connect to my neighbors, rather than asking me for my password and then connecting to mine. Is there any way I can blacklist his wireless router so mine will be the default?

Edit: I am using Feisty

---

### Post by arron on 2007-12-21
Same problem here, can anyone help?

---

### Post by hat403781 on 2007-12-21
I think I have found a solution to this problem. I went into the following directory:

~/.gconf/system/networking/wireless/networks

In this directory is a file called %gconf.xml (which is empty for me), and a bunch of directories which have the same names as the wireless networks that I have connected to. In each of the directories is a %gconf.xml file that has info on the wireless network with that name. I simply deleted the directory corresponding to the network that I didn't want it to automatically connect to. Please back up this directory if you decide to delete it. It seems to have worked for me, but I am not sure if this is safe because I don't know if this directory is referenced from any other config files. If anyone else on this forum could advise on this, please do.

---


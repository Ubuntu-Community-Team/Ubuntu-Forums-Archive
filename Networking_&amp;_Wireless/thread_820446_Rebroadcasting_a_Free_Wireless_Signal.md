---
title: "Rebroadcasting a Free Wireless Signal"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by DocHolliday2006 on 2008-06-06
Hi. I'm moving to an apartment in a downtown area where wireless internet is given away free to the public. The signal reaches the front window of my apartment but dies not far inside.

I was wondering if there was a way to pick up the signal and rebroadcast it from a wireless router to the rest of my apartment, even though I don't have control of the signal, so that I can use it for my ubuntu computers and such.

Is this doable?


How would I go about it? What would I need to buy?

Thanks.

---

### Post by chili555 on 2008-06-06
I use a Linksys WAP54G which has a repeater mode. With no encryption, all you need do is supply the MAC address of the device broadcasting the wireless signal. You can determine this when you are connected. *iwconfig* will show the address of the access point you are associated with:> ESSID:"2WIRE118"
Mode:Managed Channel=6 Access Point: 12:34:56:78:90:00
---snip---I got mine inexpensively on Ebay.

---

### Post by rickyjones on 2008-06-06
> **DocHolliday2006 said:**
> Hi. I'm moving to an apartment in a downtown area where wireless internet is given away free to the public. The signal reaches the front window of my apartment but dies not far inside.

I was wondering if there was a way to pick up the signal and rebroadcast it from a wireless router to the rest of my apartment, even though I don't have control of the signal, so that I can use it for my ubuntu computers and such.

Is this doable?


How would I go about it? What would I need to buy?

Thanks.

Linksys is one company that creates a very simple wireless extender. If memory serves right then all you need to do is plug in the power, plug in a CAT5 cable to get to the web interface, then configure the SSID/Security/Etc.... Then just let it do its thing.

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130267578138&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7813839789B57](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130267578138&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7813839789B57)

Hope this helps!

-Richard

---

### Post by DocHolliday2006 on 2008-06-06
And this would work with having it extend a wireless network that it run by a city? It's free and I don't need a password to access it, but I don't have control over it. 

> **rickyjones said:**
> Linksys is one company that creates a very simple wireless extender. If memory serves right then all you need to do is plug in the power, plug in a CAT5 cable to get to the web interface, then configure the SSID/Security/Etc.... Then just let it do its thing.

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130267578138&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7813839789B57](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130267578138&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7813839789B57)

Hope this helps!

-Richard

---

### Post by DocHolliday2006 on 2008-06-06
Thanks. I I may try this. 

> **chili555 said:**
> I use a Linksys WAP54G which has a repeater mode. With no encryption, all you need do is supply the MAC address of the device broadcasting the wireless signal. You can determine this when you are connected. *iwconfig* will show the address of the access point you are associated with:I got mine inexpensively on Ebay.

---


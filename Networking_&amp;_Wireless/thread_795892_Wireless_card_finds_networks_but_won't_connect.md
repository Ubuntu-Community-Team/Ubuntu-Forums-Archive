---
title: "Wireless card finds networks but won't connect"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by bschultzjames on 2008-05-15
I'm a complete and total n00b at this whole ubuntu thing...but I WILL not go back to windows.  

My wireless card see's my wireless network, but when I enter the encryption code [which I know is CORRECT] the connection just sits there and doesn't actually connect.  I know the router works because when I run XP on my other machines they connect to the wireless just fine.  


Any advice would be helpful...even if you point me to another forum thread.



.b

---

### Post by Master Chief on 2008-05-15
Wrong encryption type selected, or MAC address filter active in access point?

---

### Post by bschultzjames on 2008-05-15
I tried both encryption types.  Neither work.  Also, I don't have any MAC stuff so I don't think that's a problem...


any suggestions?


Thanks,
.b

---

### Post by Master Chief on 2008-05-15
> **bschultzjames said:**
> I tried both encryption types.  Neither work.  Also, I don't have any MAC stuff so I don't think that's a problem...

You mean WEP (Wired Equivalent Privacy) and WPA (Wi-Fi Protected Access)?

Please note that there's WPA and WPA2 using different encryption types (TKIP vs AES/CCMP).

MAC is short for "Media Access Control" see also:
[http://en.wikipedia.org/wiki/Media_Access_Control](http://en.wikipedia.org/wiki/Media_Access_Control)

In other words, your router/access point might only allow certain MAC addresses (example: 00:01:43:XX:XX:XX) and block all others.

---

### Post by bschultzjames on 2008-05-15
Problem solved!!! Thanks for clearing up that MAC thing...I feel kind of stupid now to realize you weren't talking about apple stuff.  

When you were referring to encryption, I was thinking of the wrong thing.  I actually DID have my encryption set to 128 bit pass code, when it needed a hexadecimal pass code.  


Thanks a lot, I'm replying to this through wireless...woo!


.b

---

### Post by Master Chief on 2008-05-16
> **bschultzjames said:**
> Problem solved!!! ...

Thanks a lot, I'm replying to this through wireless...woo!
.b

You're welcome.  Have fun.

Tip: Change the default ssid of your AP (access Point) to a unique name and use a strong encryption with ditto (long) key to block others from using your AP and do things that might get you into (legal) trouble!

---


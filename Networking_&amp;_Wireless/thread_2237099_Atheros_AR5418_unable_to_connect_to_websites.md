---
title: "Atheros AR5418 unable to connect to websites"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by belpolaris on 2014-07-30
After installing Ubuntu 14.04 and Mint 17-Cinnamon, (currently Ubuntu) I  have been having a problem with my wireless network connection failing  to connect to websites. I can ping my router, DNS provider, and websites  (both using IP and DNS entries) and I can do a telnet GET on port 80 of  websites and I get information. Yet I cannot use a browser.  Additionally, my wired network card works fine, and I am perfectly able  to connect via that method.

A notable "feature" of this situation is that I can connect to another  nearby network that uses WEP without issue - I only seem to experience  the problem on my WPA2-personal network. I have attached the wireless  script output, and would appreciate any information or assistance that  can be brought to bear.

[SOLUTION] Thanks to [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar1043629_1.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1043629")                                                                                     [**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629") for providing the fix:

Ensure that your Wireless Access Point/Router is using AES (CCMP) encryption instead of TKIP if you are using a WPA2 security setting. It is more secure, and better supported.

---

### Post by varunendra on 2014-07-31
Can you explain the different subnets on Ethernet vs Wireless interfaces please? Are they connecting to different networks?

Plus an important abnormality - your router is using WPA2 with TKIP - a non-standard combination. Please change the algorithm from TKIP to AES (CCMP) in the router. Check the router's manual if you need help on that.

---

### Post by belpolaris on 2014-07-31
I thank you for responding to my request for assistance.

> **varunendra said:**
> Can you explain the different subnets on Ethernet vs Wireless interfaces please? Are they connecting to different networks?

The networks are different, but connect to the same internet connection. The difference was an intentional design decision of the network owner.

> **varunendra said:**
> Plus an important abnormality - your router is using WPA2 with TKIP - a non-standard combination. Please change the algorithm from TKIP to AES (CCMP) in the router. Check the router's manual if you need help on that.

The WAP is separate from the router (I also don't deal with its configuration, so I will consult with the one who does.) Windows boxes and android devices seem to handle the network just fine. From what I saw from a quick google search it looks like TKIP may be sub-optimal, but well supported. Can you clarify whether your suggestion to change this is just about security, or if there is some issue with that combo that causes issues with the implementionation of WPA2 in my install?

---

### Post by varunendra on 2014-07-31
Not just security, it is also not the standard which may confuse the driver. With WPA, the drivers expect TKIP, with WPA2, drivers expect AES (CCMP). While some routers allow mixing them (even AES with WPA, which doesn't even support AES), it is recommended to keep the settings as per standards to avoid problems.

A detailed discussion on these standards (my own interpretation of terms, may be incorrect) : [http://ubuntuforums.org/showpost.php?p=12817442](http://ubuntuforums.org/showpost.php?p=12817442)

In particular, from [http://en.wikipedia.org/wiki/CCMP#Security](http://en.wikipedia.org/wiki/CCMP#Security) -
> **CCMP is the standard encryption protocol for use with the WPA2 standard** and is much more secure than the WEP protocol and TKIP protocol of WPA.

My personal belief and opinion about "Why Windows and Android works if..." has also been described in the post linked above. It talks about Win7 only, but same reasons apply to Android market as well.

---

### Post by belpolaris on 2014-08-01
> **varunendra said:**
> Plus an important abnormality - your router is using WPA2 with TKIP - a non-standard combination. Please change the algorithm from TKIP to AES (CCMP) in the router. Check the router's manual if you need help on that.

After consulting with the owner of the WAP, this was PRECISELY the setting that fixed the problem. Thank you!

---

### Post by varunendra on 2014-08-01
You're welcome! Its so nice to have yet another confirmation. :)

---


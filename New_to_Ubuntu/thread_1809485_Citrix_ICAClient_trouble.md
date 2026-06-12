---
title: "Citrix ICAClient trouble"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Polar67 on 2011-07-21
Hi Y'all.

Having made an attempt at an OS "without a Bill" for the second time i've been trying to get citrix ICAClient to function proberly.
I've installed Citrix Reciever using this excellent guide:

[https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")

The installation went fairly trouble free & Citrix Reciever started up without any error msg.

From there however it went downhill.

I started Firefox 5 and tried to log in to the company workspace. The attached screendump ssl_vpn shows the result. As you can see I seem to have insufficient privilige. No i don't. There's nothing wrong with my rights. when i'm on a travel to small village offices i log on the same way using a stationary computer running a Suse Linux.

I then started Citrix Reciever and tried to enter the URL manually. The attached screendump client_error told me that there was a security certificate missing. This I downloaded an exported it to /usr/lib/ICAClient/keystore/cacerts. The result was first a Firefox crash but when tried again i got the ssl_vpn message again.

An aqquaintance of mine gets the same message on firefox using Windows. This leads me to believe that perhaps it's Firefox that's got issues. A Firefox support search came up fairly dry though. Otherwise i love whats been done to Natty. last time i made an attempt was Gutsy.

Please advise.
Regards
ELO

---

### Post by Polar67 on 2011-07-22
No one??

Please!!

I really need this to work. Any input is welcome.

Regards
ELO

---

### Post by BigCityCat on 2011-07-23
there is a guide in tutorials that should get you up and running. Let me find the link.

I followed this and got it going. I'm no expert but this worked for me.

[http://ubuntuforums.org/showthread.php?t=1105855&highlight=citrix](http://ubuntuforums.org/showthread.php?t=1105855&highlight=citrix)

---


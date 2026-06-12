---
title: "Wireless WEP to dash or not to dash?"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by tomduffy on 2006-08-28
Can somebody clear this up for me, should my WEP key be entered with dashes or not  I.E. ****-****-** or **********. Also does it need to be preceded with S:. I can get a connection to the network using an ethernet cable but not wireless. I have used Ndiswrapper and I am using a BlueNext device which works fine with windows. I am new to this but I am intending not to add to Mr Gates fortune any further.

---

### Post by ddales on 2006-08-29
No dashes

The s: is only for ASCII codes which most people use, without it you can enter the hex code 

I haven't been able to get WEP working with my card but that's probably because of the firmware.  SMC2802W V2  (known problem though)

---

### Post by tormod on 2006-08-29
It seems like some drivers would like colons between pairs of hex digits like this: 0a:87:33:ae:b4

---


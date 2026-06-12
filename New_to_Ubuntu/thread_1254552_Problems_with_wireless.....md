---
title: "Problems with wireless...."
date: 2009-08-31
forum: New to Ubuntu
---

### Post by wolfturn on 2009-08-31
i have ubuntu 9.04. i just clean installed it over an old windows xp. but for some reason, the wireless internet doesn't want to work, i plugged in my wireless adaptor USB, and then it automaticly detected my wifi, i typed in my WEP key, and it connected. (i got excited), then, when i open up firefox, and typed in google in the address, it said no address found, i tried messenger, and it just kept trying to connect for a LOOONG time. Any ideas whats going on? this is my first time working with ubuntu, so i'm trying to get this started.

---

### Post by mapes12 on 2009-08-31
Right click the Network Manager icon. It's the one with your wifi signal strength with 4 bar columns in your bottom r/h corner next to the date. Then "Connection Information". Then Applications>Accessories>Take screen shot. "Grab the current window" It will be saved to your desktop. Post it back here. You will need to go towards the bottom of the new thread to "attach files" under the additional options section. Mine looks like the attached.

---

### Post by wolfturn on 2009-09-01
Ok, Hopefully this is what you asked for. I just took the whole screen, hope you don't mind. If you need another with just that one window,(i have no idea why you would need that..) just tell me, and i'll take another.
 
Edit: I use a belkin Wireless Router, in case that means anything.

---

### Post by LewRockwell on 2009-09-01
you need to check and confirm your dhcp stuff

routers usually hand out individual machine IP addresses like 192.168.1.114

.

---

### Post by mapes12 on 2009-09-02
> **wolfturn said:**
> Ok, Hopefully this is what you asked for. I just took the whole screen, hope you don't mind. If you need another with just that one window,(i have no idea why you would need that..) just tell me, and i'll take another.
 
Edit: I use a belkin Wireless Router, in case that means anything.Looks to me like your internal LAN is OK. Do you have any other machines that are connected to your router, wifi or ethernet? If so tell us what you have.

The problem would appear to be getting outside your LAN to the internet. Who is your ISP? You should be able to access your routers set up screens. In your browser address bar type [http://192.168.2.1](http://192.168.2.1)

You need to look for an IP address assigned to your router/modem from your ISP it will be 4 sets of numbers separated by "."

---


---
title: "Strange Network Monitor behavior"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by dabugas on 2007-08-28
I have an new HP 530 running Feisty and can connect to my router at home with WiFi with no problems, except that for some reason the Network Monitor applet gives me this error when I click on it:

"Could not find information on interface 'eth1:avahi' in /proc/net/dev"

On my Feisty desktop (with a different card) I have no such problem. Since WiFi works on the laptop, I am only worried for problems down the line.

According to lspci my my network controller is an Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Any ideas?

---

### Post by spd106 on 2007-08-28
It's a fairly harmless bug, there's nothing to worry about as long as you have a connection. 

The X:avahi interfaces are created when the dhcp client fails to connect to a dhcp server. So it self-assigns an address for you instead. This is same case as in XP when it says "you have limited or no connectivity".

---

### Post by dabugas on 2007-08-28
Thanks for the info.

I was worried because this happens every time, while in Windows (as far as I can recall) this would only happen every once in a while. It was not, in other words, a replicable scenario.

---


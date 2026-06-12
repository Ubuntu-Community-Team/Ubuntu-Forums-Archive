---
title: "Problems Intel 4965 AG"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by andreselsuave on 2008-08-21
Hi there, 
I'm experiencing problems with my Intel "PRO/Wireless 4965 AG or AGN Network Connection" ... The driver recommended in the Sticky post in this forum "Supported wireless card list" is iwl4965, which I am currently using. However, sometimes when I turn the computer on (HP Compaq 8710p) the network manager displays no Wireless points within range (while my other computers are working with wireless). 
I have tried to manual configuration because apparently network manager is sometimes buggy, but it hasn't worked for me
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

That is why im suspecting it is a driver problem... what can I do?

Thanks for your help in advance

---


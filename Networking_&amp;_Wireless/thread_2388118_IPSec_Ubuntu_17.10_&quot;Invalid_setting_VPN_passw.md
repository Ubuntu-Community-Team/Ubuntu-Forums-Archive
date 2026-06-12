---
title: "IPSec Ubuntu 17.10 &quot;Invalid setting VPN: password is too short&quot;"
date: 2018-03-28
forum: Networking &amp; Wireless
---

### Post by lifeboy on 2018-03-28
When using the GUI (network-manager-strongswan) to create a connection, the "Add" button is greyed out, although all the fields are correctly populated.

When I start "sudo nm-connection-editor", I can see in the terminal the message "Invalid setting VPN: password is too short" which is nonsense.  My password is valid and 16 character in length.  I experimented with lengths and only once I enter 20 characters does it allow me to save.  Now, firstly, this is a bug since there should at least be a notification of some sort in the network-manager client, but worse, who uses a more than 20 character password??

Furthermore, despite select "pre-shared key" there is nowhere where that key can be entered.  Did anybody even do some testing on this plugin?  

[ATTACH=CONFIG]279119[/ATTACH]

---

### Post by vladkras on 2018-09-30
Same problem with Ubuntu 18.04 bionic
I've installed strongswan and network-manager-strongswan from main repo
but when I'm trying to create new IPsec/IKEv2 connection the "Save" button is greyed out and shows a hint
Invalid setting VPN: password is too short

It seems this line [https://github.com/strongswan/strongswan/blob/1b671669212bd3b46301dc842ae63be6775c2508/src/frontends/gnome/properties/nm-strongswan.c#L137](https://github.com/strongswan/strongswan/blob/1b671669212bd3b46301dc842ae63be6775c2508/src/frontends/gnome/properties/nm-strongswan.c#L137) is responsible for this.

And I also don't see an input fro pre-shared key

(I use lxde and all packeages are up to date)

---

### Post by giondo on 2019-05-12
same issue here may 2019
any update on this? did anyone found the solution?

Thanks in advance

---


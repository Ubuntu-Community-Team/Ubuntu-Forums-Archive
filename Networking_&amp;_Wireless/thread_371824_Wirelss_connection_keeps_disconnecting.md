---
title: "Wirelss connection keeps disconnecting"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by Bez625 on 2007-02-27
Im using network-manager and wpa-supplicant to connect to my home network but a while the connection just drops and wont reconnect. It says something about waiting for the network key so im not sure if there is a problem with the key chain. Anyone have any suggestions on how to make this more stable?

Cheers,

Bez

---

### Post by Metaljaz on 2007-02-27
Informational link which may have your answer:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by jasonbrisbane on 2007-02-27
Hi,

Can I please add a "Me too..."?

I have had my wireless AP open and working for four days constantly (the weekend was good!) but closed the connection when I was sure the IP details were ok and tried to configure WPA-Supplicant.

It connects when I reboot but NEVER when I follow the manual instrcutions (ie: sudo wpa_supplicant -c/etc/wpa_supplicant.conf . . . . . -dd)
Now I've found that when the DHCP lease expires the system doesnt pick it back up again - exactly like the situation with Bez625!
:confused: 

Now I havent added :

ap-scan 2

to the wpa_supplicant file - I will shortly due to lack of anything else to try...

Does anyone have a solution that they have found to work?

Regards,
Jason Brisbane
Ubuntu Newbie

---


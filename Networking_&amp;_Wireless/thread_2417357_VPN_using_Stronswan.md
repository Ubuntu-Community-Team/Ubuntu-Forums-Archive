---
title: "VPN using Stronswan"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by gkarwchan on 2019-04-22
Hi 
I am using Strongswan to connect to my client vpn network.
I setup the vpn as the client documentation using (EAP).
I am able to login to the vpn, as it is asking every time to verify using my mobile Application "Microsoft authenticator" (it is setup with 2 facator authentication)
But my browser or my ping cannot reach any resource on that network.

When I do :
journalctl -f

I keep receiving this message repeatedly over and over thousand times


<my computer name> charon-nm[4641]: received packet: from <ip address> [4500] to 172.20.0.100[54781] (72 bytes)
<my computer name> charon-nm[4641]: 10[ENC] parsed INFORMATIONAL request 356 [ ]
<my computer name>  charon-nm[4641]: 10[ENC] generating INFORMATIONAL response 356 [ ]
<my computer name>  charon-nm[4641]: 10[NET] sending packet: from 172.20.0.100[54781] to <some ip address> [4500]

---


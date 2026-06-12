---
title: "[SOLVED] Cisco VPN client: Lan access Disabled"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by jujulj on 2008-07-02
hi,

I installed Cisco VPN client using the instructions given [here]("http://projects.tuxx-home.at/?id=cisco_vpn_client")

It compiles and runs correctly but when I'm connected, I loose my internet connection (I can still use skype or pidgin though).

A solution for    was proposed in [that thread]("http://ubuntuforums.org/archive/index.php/t-430136.html"), but it seems not to work for the latest client version (vpnclient-linux-x86_64-4.8.01.0640-k9).

Any suggestion?

Thank you

jujulj

---

### Post by ilrudie on 2008-07-02
Unless I don't understand what you are getting at the "LAN Access Disabled" message is actually because its routing all of your traffic through the VPN connection.  You can probably overcome this by adding a route to hosts and nets that you don't want to go through the VPN using the ```
route add
``` command.  Run ```
man route
``` for more information and you probably should not overwrite the default route.  

Correct me if this is not what you are asking for and I will try to assist you further.

---

### Post by jujulj on 2008-07-02
Thanks a lot ilrudie.
Once connected to the VPN, I added the route seen when not connected and it works!

---

### Post by ddimit on 2011-04-28
because im begginer can you be more specified about that  because i have the same problem and i cannot make it work:(

---


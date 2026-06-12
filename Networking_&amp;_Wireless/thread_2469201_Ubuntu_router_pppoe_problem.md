---
title: "Ubuntu router pppoe problem"
date: 2021-11-22
forum: Networking &amp; Wireless
---

### Post by tourguy on 2021-11-22
I had a functional ubuntu router A, using pppoe, isc-dhcp-server, masqdns.

Problem happened when I tried transfering to openmediavault(Debian). I configured a new build on another drive and used almost the same configuration as my working router before replacing old drivewith this new one(say it router B) on the router. Everything is fine except that I can't access internet. Ifconfig showed that I got a reserved IP from provider. How I know that? Because I dialed my provider and they told me my broadband keeps using wrong password dialing. They also told me if dialing with wrong password, it will succeed, but with a reserved IP, which is exactly what happened in my scenario. They decide to change password for me. That's when the weirdest thing happened.


My old ubuntu router A worked fine before the password change. During testing router B, I switched router A back online and it worked as usual. After the password change, I once again switched back to router A. As you can see, it dialed with old password and of course it would fail, ending up with a reserved IP just as what happened to router B. I realized that immediately and changed new password for router A, but nothing good happens. Router A continues to get reserved IP. I checked account/password file countless times, still no luck.

My provider told me that my broadband keeps using wrong password after the password change. It seems that ubuntu and Debian is sending wrong password through pppoe though the file is correct. Also, I tried normal router and they are fine, with old password or new one.

I used pppoeconf to configure the router. It's the file /etc/ppp/chap-secrets that saved broadband information.

---


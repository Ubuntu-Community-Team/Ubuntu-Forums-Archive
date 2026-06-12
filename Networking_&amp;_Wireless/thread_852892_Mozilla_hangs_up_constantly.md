---
title: "Mozilla hangs up constantly"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Infatuas on 2008-07-08
I have tried the following fixes

1. open mozilla, about:config disable ipv6 their by setting to true.

2. opening /etc/modprobes.d/aliases setting alias net-pf 10 off; net-pf 10 ipv6 off and alias ipv6 off.

3. I have also added blacklist ipv6 to the blacklist file

I go to a website it works next second it hangs up and says cannot display page. I know it isn't something as simple as rebooting my router, i've eliminated that and cabling as any potential issue. Any ideas? I really want to continue to use mozilla.

Thanks,

---

### Post by thetechguyz on 2010-04-23
I wanted to post this because I had a horrible issue with Mozilla Firefox hanging each time I typed in a web address. 

Symptom: Website load would hang and status at the bottom of the browser would say Looking up ... Would last nearly a minute then the page would load.

Cause: IPv6 enabled

Fix: Disable IPv6 by setting true in about:config Firfox

This was done easily because of the thread started by the guy above.

THANK YOU!

---

### Post by jordilin on 2010-04-23
You can always re do your .mozilla profile in your $HOME. Back it up before redoing it though, just in case.

---


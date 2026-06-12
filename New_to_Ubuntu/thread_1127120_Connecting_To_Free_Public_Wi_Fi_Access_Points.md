---
title: "Connecting To Free Public Wi Fi Access Points"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Kensoi on 2009-04-16
Hi. I'm New To Ubuntu & Wireless.

I'm Just Wondering If There Are Any Problems Connecting To Free Wi Fi & What The Best Settings Are & Practices  ?

I Don't Have Any Problem With My Using Wireless At Home With WEP Key.

Just Wanting To Find Out If There Are Any Specific Settings For Using Free Public Access Wi Fi.

Thanks Ken

---

### Post by kpkeerthi on 2009-04-16
I'd enable firewall (ufw/iptables) when I'm "roaming" and not behind a router.

---

### Post by Penguin Guy on 2009-04-16
For new Linuxers I would advise firestarter GUI for iptables. It does the same thing but uses a **G**raphical **U**ser **I**nterface rather than **C**ommand **L****i**ne.

---

### Post by freak42 on 2009-04-16
If your wifi at home works fine, then I don't see any problems connecting to public wlans.

---

### Post by Kensoi on 2009-04-16
Thanks For That. I Have Firestarter Enabled. So I Shouldn't Have Any Problems. Just Checking.

Ken

---

### Post by kpkeerthi on 2009-04-16
Firestarter is outdated and is no longer maintained. Ubuntu comes with [ufw]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html"). Try [gufw]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") if you need a GUI.

---


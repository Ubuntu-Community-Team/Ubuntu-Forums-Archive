---
title: "Ufw Vs Firestarter-which is better &amp; why?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by D1Knight on 2010-03-03
Hello. Like the title says.;) I appreciate the help. Thanks.:)

---

### Post by Enigmapond on 2010-03-03
ufw is the firewall in Ubuntu. Firestarter is just a front-end to set rules and is also a dead programme and you don't need it, uninstall it. If you use the terminal and just type..

```
sudo ufw enable
```

This will enable the firewall and deny all incoming by default and will start each time you boot. If you need to change any rules, install gufw which is a simple front-end for ufw and is great/

---

### Post by cariboo on 2010-03-03
UFW/GUFW is better than Firestarter, as Firestarter is hasn't been updated since 2005, the Debian maintainer adds bug fixes, but that is about all.

---

### Post by D1Knight on 2010-03-03
> **Enigmapond said:**
> ufw is the firewall in Ubuntu. Firestarter is just a front-end to set rules and is also a dead programme and you don't need it, uninstall it. If you use the terminal and just type..

```
sudo ufw enable
```

This will enable the firewall and deny all incoming by default and will start each time you boot. If you need to change any rules, install gufw which is a simple front-end for ufw and is great/

Well that answers that.;) I thank you kindly.:)

---

### Post by D1Knight on 2010-03-03
> **cariboo907 said:**
> UFW/GUFW is better than Firestarter, as Firestarter is hasn't been updated since 2005, the Debian maintainer adds bug fixes, but that is about all.

Thanks for your response.:)

---

### Post by egalvan on 2010-03-03
> **Enigmapond said:**
> ufw is the firewall in Ubuntu. Firestarter is just a front-end to set rules and is also a dead programme and you don't need it, uninstall it. I


ufw is not a firewall.
ufw is a "front-end" for the iptables and netfilter.

Yes, firestarter is basically abandoned. It has not been updated in several years, and has been deprecated in favor of ufw.

---

### Post by Enigmapond on 2010-03-03
> **egalvan said:**
> ufw is not a firewall.
ufw is a "front-end" for the iptables and netfilter.

Yes, firestarter is basically abandoned. It has not been updated in several years, and has been deprecated in favor of ufw.

Yes sorry...my mistake in terms...thank you..:)

---

### Post by D1Knight on 2010-03-03
> **egalvan said:**
> ufw is not a firewall.
ufw is a "front-end" for the iptables and netfilter.

Yes, firestarter is basically abandoned. It has not been updated in several years, and has been deprecated in favor of ufw.

Thanks for the clarification.:) I appreciate you.

---

### Post by werty2010 on 2011-02-10
isn't a pity for a such a good program(at least i have the impression...newbe) to end like this?

---

### Post by MaxWebXperienZ on 2013-05-03
I tried to set up a WHITELISTING firewall with direct rules in Iptables and Gufw.. might take me months to fully get it right.. with Firestarter it could not be easier. I hope that Firestarter is around for a very long time...

---

### Post by overdrank on 2013-05-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


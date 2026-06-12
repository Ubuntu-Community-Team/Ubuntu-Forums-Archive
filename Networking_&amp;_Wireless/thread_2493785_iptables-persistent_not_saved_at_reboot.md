---
title: "iptables-persistent not saved at reboot"
date: 2023-12-25
forum: Networking &amp; Wireless
---

### Post by matthys on 2023-12-25
Hello,

Bit new to this, so sorry to ask but;
 I installed iptables-persistent and saved the rules using:
sudo /sbin/iptables-save > /etc/iptables/rules.v4
sudo /sbin/ip6tables-save > /etc/iptables/rules.v6

And indeed the rules are there, but I noticed they do not change after reboot.
Meaning the rules are from the one time I saved them manually and are not saved before reboot.
Making new rules are lost after reboot...

Is there anything I have to configure? Did I miss something here?

Currently using Ubuntu 22.04.3 LTS

---

### Post by The Cog on 2023-12-25
That's right. iptables-persistent loads whatever is configured in iptables.rules when the machine boots. It does not save any other changes that you made directly into the active configuration. You have to manually save after any changes that you want to keep. So if you royally mess up the current rules (not uncommon), a reboot will get you back to a known state.

---

### Post by matthys on 2023-12-26
So better to ask, how do I save and restore automagically as iptables-persistent is not doing this (as I had hopped)?

Just one more note: I did read about netfilter-persistent (part of iptables-persistent) and it says:

**netfilter-persistent** uses a set of plugins to load, flush and save netfilter rules at boot and  halt  time.

Does this mean it should be save at shutdown (halt) or reboot?

---

### Post by The Cog on 2023-12-28
> I did read about netfilter-persistent
Read it again. netfilter-persistent (which you did not ask about) has a save option to **tell it to** save the current configuration:
[https://manpages.ubuntu.com/manpages/xenial/man8/netfilter-persistent.8.html](https://manpages.ubuntu.com/manpages/xenial/man8/netfilter-persistent.8.html)

---


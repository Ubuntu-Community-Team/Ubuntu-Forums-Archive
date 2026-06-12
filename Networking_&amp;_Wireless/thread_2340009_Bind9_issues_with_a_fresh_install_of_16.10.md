---
title: "Bind9 issues with a fresh install of 16.10"
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by bearlake on 2016-10-14
Hi good folks.

Using UbuntuGnome 16.04 and bind9 with no issues.

Did a fresh installed of UbuntuGnome 16.10 and added the bind9, set my DNS to 127.0.0.1 and had no Internet after restarting bind9.

Disabled the DNS 127.0.0.1 and everything is working as it should.

Checked my settings between 16.04 and 16.10 and they are the identical.

Anyone find a work around for this yet?

Thanks

---

### Post by bearlake on 2016-10-15
Friendly bump.

---

### Post by Rustan on 2016-10-16
thesame problem

```
Oct 16 10:05:30 kubuntu systemd-resolved[785]: Using system hostname 'kubuntu'.
Oct 16 10:05:58 kubuntu systemd-resolved[785]: Switching to fallback DNS server 8.8.8.8.
Oct 16 10:06:29 kubuntu systemd-resolved[785]: Switching to system DNS server 193.34.172.1.
Oct 16 10:07:19 kubuntu systemd-resolved[785]: Switching to system DNS server 8.8.8.8.
Oct 16 10:39:07 kubuntu systemd-resolved[785]: Switching to system DNS server 127.0.1.1.
Oct 16 10:39:09 kubuntu systemd-resolved[785]: Switching to system DNS server 193.34.172.1.
Oct 16 10:44:58 kubuntu systemd-resolved[785]: Switching to system DNS server 8.8.8.8.
Oct 16 10:44:58 kubuntu systemd-resolved[785]: Switching to system DNS server 127.0.1.1.
Oct 16 10:50:39 kubuntu systemd-resolved[785]: Switching to system DNS server 193.34.172.1.
Oct 16 11:11:45 kubuntu systemd-resolved[785]: Switching to system DNS server 8.8.8.8.
Oct 16 11:26:51 kubuntu systemd-resolved[785]: Switching to system DNS server 127.0.1.1.
Oct 16 11:33:45 kubuntu systemd-resolved[785]: Switching to system DNS server 193.34.172.1.
Oct 16 11:33:49 kubuntu systemd-resolved[785]: Switching to system DNS server 8.8.8.8.
Oct 16 11:39:09 kubuntu systemd-resolved[785]: Switching to system DNS server 127.0.1.1.
Oct 16 11:40:05 kubuntu systemd-resolved[785]: Switching to system DNS server 193.34.172.1.
```

when this happens "Switching to system DNS server 127.0.1.1" Internet disappears
because
```
DNS_PROBE_FINISHED_NXDOMAIN
```
how to fix it?

---

### Post by Rustan on 2016-10-16
possibly linked to this bug
[https://github.com/systemd/systemd/issues/4175](https://github.com/systemd/systemd/issues/4175)

---

### Post by bearlake on 2016-10-16
Thanks for the link Rustan, Will follow it up shortly.

---

### Post by bearlake on 2016-10-18
The work around was found here.

[https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382](https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382)

Post #3

Post #5 where its marked as **The workaround.**

---


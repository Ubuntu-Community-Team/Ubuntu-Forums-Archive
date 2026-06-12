---
title: "Who is Kubuntu contacting and why?"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by mibadt on 2006-11-12
Hi,
I'm on a (fresh installed) Kubuntu Edgy (32b).
dmesg shows (at its en) 3 identical trials to connect UDP to some IP address which were all rejected by my firewall.
Yet, I wonder, is this OK? What should I do to eliminate these trials?

TIA


----------copy of one trial out of dmesg-------------
DROPPED IN= OUT=eth0 SRC=10.0.0.1 DST=82.211.81.145 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1024 DPT=123 LEN=56
--------------------------------end--------------------------

---

### Post by bjd on 2006-11-12
That's NTP time synchronisation. It sets your computer clock to the right time.

---

### Post by mibadt on 2006-11-12
Thanks!:)

---


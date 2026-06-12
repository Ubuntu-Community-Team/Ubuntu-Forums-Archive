---
title: "56k problem (not newbie)"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by neclepsio on 2006-11-30
Hi everyone.
I've a problem with my 56k softmodem from when, for some strange reason, the entire network configuration was wiped out. In that occasion, I had to rewrite even the hosts file because, not containing localhost, some programs didn't work (first of all gnome-settings-daemon).
Now, I can connect with gnome-ppp, I get the IP and other settings from the remote server, but I cannot surf. I cannot even ping my own address. No packets activity is signaled in connection statistics. In practice, the requests to the internet are not routed through the modem.
Can you help me?

Thank you,
Ignazio

---

### Post by PennYanPete on 2006-11-30
Hi neclepsio

I am a newbie, so just a thought here.

Did that "for some strange reason" bork gnome-ppp? Maybe uninstall gnome-ppp and reinstall, if you have not already done so.

PYP

---

### Post by neclepsio on 2006-12-01
Thank you, but that disn't solve my problem.

Anyway, I solved it. In /etc/network/interfaces, under "iface pp0..." ther was "provider ppp0" instead of "provider wvdial". I hope this can help some other.

Ignazio

---


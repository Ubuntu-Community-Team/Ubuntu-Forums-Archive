---
title: "Winmodem (works is SuSE not Ubuntu)"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by ShaneR on 2005-07-07
Strange problem.  As the title suggests, my win modem won;t work in ubuntu but works great in SuSE.  I've looked how the connection is established in SuSE and Ubuntu, and the procedure looks the same.

They only differences I see are:

1)Suse makes a symlink between Modem0 and /dev/ttLTMO
2) Suse renames device ppp0 to Modem0

Since SuSe appears to use wvdial (kinternet as the GUI), I'm thinking  I should be able to get wvdial working in Ubuntu.  I'm just outta ideas right now.  I've set up /etc/wvdial.conf with what appears correct settings for the modem.  tried with and without stupid mode. But, it dials out tries to establish a connection and then exits with code 10.

Anyone have an idea? I feel I'm missing something very simple here...

Thanks :)

---

### Post by fizgig on 2005-07-07
My webpage might help you:
[http://mattsmith.hostmatrix.org/zx5078cl/main.html](http://mattsmith.hostmatrix.org/zx5078cl/main.html)

Go to the modem section.

---


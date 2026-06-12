---
title: "Modem won't configure, PPP says Modem Busy"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by sabersong on 2008-09-13
Hi.

I'm trying to solve this problem by telephone for my parents, who recently switched to Kubuntu (Gutsy) because they were sick of Windows.

I walked them through the installation, told them how to change the modem to a Conexant RD02-D490 that I sent them, along with the Linuxant HSF drivers.  Building the drivers went fine, but when we ran hsfconfig, it gave the standard warning about not having HDA support, then quit.  When we ran KPPP (they're using Kubuntu), we get "Modem Busy".  Keep in mind that I'm 750 miles from the computer, and my parents know enough to be able to get online with Windows. All that said, can anyone offer any help here?

---

### Post by sabersong on 2008-09-13
I forgot to mention that we've tried rebooting, rebuilding the drivers and running the configuration tool again, all with the same results.  At present, the parents are without internet access of any kind.

---

### Post by ModelM on 2008-09-13
That message might mean that there's an old lock file laying around making it seem as if the modem is in use. Have a look in /var/lock for a file called (probably) modem & delete it if you find one, then try it again.

---


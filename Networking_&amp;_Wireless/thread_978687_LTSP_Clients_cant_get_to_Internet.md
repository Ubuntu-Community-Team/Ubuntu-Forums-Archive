---
title: "LTSP Clients cant get to Internet"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by saythein on 2008-11-11
I installed Ubuntu 8.10 Alternate with the Install LTSP Server option. My machine has two NICs, one to our network and one to a switch. The switch has 4 LTSP clients. They boot fine, but they are unable to get to the internet. I have no edited any configurations, everything is default. Can someone please let me know what I need to do to get internet access on my thin-clients? Thank you

---

### Post by Coreigh on 2008-11-11
I am not familiar with LTSP directly but it sounds like a routing problem. Try these:
[https://wiki.edubuntu.org/ThinClientHowtoNAT]("https://wiki.edubuntu.org/ThinClientHowtoNAT")
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring")
[https://help.ubuntu.com/community/UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

---

### Post by superprash2003 on 2008-11-11
are the clients able to ping the ubuntu machine?

---

### Post by saythein on 2008-11-25
I was able to get this working. There was a problem in my NIC configs. I had to manually edit the config file rather than change the settings in the system-administration-networking menu. After that everything ran 100%

---


---
title: "how to activate wireless for wireshark"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by jhazard112 on 2010-11-09
I have recently installed wireshark on my laptop. and I need to activate my wireless card to work with it...unfortunately I am unsure on how to do this...any help would be much appreciated.  I am Ubuntu 10.04 Lucid Lynx with an MSI RT2573...please let me know if you can help.

---

### Post by toekneewood on 2010-11-09
Right click the icon and select "Add this launcher to panel".  Then right click it and put "gksudo" in front of the command.  This will allow you to run in sudo

---

### Post by toekneewood on 2010-11-09
> **jhazard112 said:**
> I have recently installed wireshark on my laptop. and I need to activate my wireless card to work with it...unfortunately I am unsure on how to do this...any help would be much appreciated.  I am Ubuntu 10.04 Lucid Lynx with an MSI RT2573...please let me know if you can help.
did you manage to get wireshark working?

---

### Post by uRock on 2010-11-09
Running Wireshark as root is a bad idea. [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)

> Linux

Running Wireshark (or any other network capture/analyzer, for that matter) on Linux needs root privileges. Therefore, you have to have root privileges when starting Wireshark, else you can't capture data. Please note that you don't have to login as root when starting your computer, you can use su(1) or sudo(8) for that purpose. However, this remains unsecure as the dissectors, the parts of Wireshark which parse the captured data, run with root privileges as they did before. A much safer solution would be to su(1) to root, then use the bundled dumpcap to dump the data (for example, you can evoke dumpcap by using "dumpcap -w ./dumpfile", which will dump the packets to the file "dumpfile" in the current working directory. See "dumpcap -h" for details). You could also use tcpdump for this purpose. The advantage of this solution is, while dumpcap/tcpdump still run as root, you can run Wireshark as a ordinary user and load the data you captured previously, so effectively this is kinda "privilege separation by hand".

Setting network privileges for dumpcap

1. Ensure your linux kernel and filesystem supports File Capabilities and also you have installed necessary tools.

2. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap"

3. Start Wireshark as non-root and ensure you see the list of interfaces and can do live capture.

---


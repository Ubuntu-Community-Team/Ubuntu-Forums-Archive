---
title: "how to (1) share folder, (2) printer"
date: 2004-12-13
forum: Networking &amp; Wireless
---

### Post by Sorin Paliga on 2004-12-13
OK, at the university of Bucharest Ubuntu behaves OK on a quite old PC. Could you calmly instruct me how to (1) make Ubuntu share the HP 970 cxi connected to the PC, and an iMac aside should print too (worked fine with previous MDK 10.1 replaced by Ubuntu); (2) how to share a folder for the whole network.
Note: all samba components installed, and the network is correctly displayed in NAUTILUS.

---

### Post by Alessio on 2004-12-14
[QUOTE=Sorin Paliga]OK, at the university of Bucharest Ubuntu behaves OK on a quite old PC. Could you calmly instruct me how to (1) make Ubuntu share the HP 970 cxi connected to the PC, and an iMac aside should print too (worked fine with previous MDK 10.1 replaced by Ubuntu); (2) how to share a folder for the whole network.
Note: all samba components installed, and the network is correctly displayed in NAUTILUS.[/QUOTE]
 I'm in the same situation with an HP 930 :(

---

### Post by gheorghe_pop on 2004-12-14
For the second problem there is a ubuntu starter guide at http://ubuntuguide.org/index.html(it worked for me).
Try it for the folder isue and maybe you could  find there something to help you with the printer.

---

### Post by p!=f on 2004-12-14
Hi to Bucharest.

(2) to share a printer:
* Add your printer using ie. [http://localhost:631/admin](http://localhost:631/admin)
* Open your /etc/samba/smb.conf file and comment out [printers] share
* Then, just restart Samba and add the Linux printer to a Windows machine as you would any other Window's shared printer. The printer name will be the same name specified in the /etc/printcap file such as lp.

Your configuration may vary. If you experience any problems, feel free to post it here so we can tweak it to make it work.

---


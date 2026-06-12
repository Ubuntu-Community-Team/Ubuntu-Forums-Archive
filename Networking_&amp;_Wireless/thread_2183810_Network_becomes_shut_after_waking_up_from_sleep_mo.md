---
title: "Network becomes shut after waking up from sleep mode (Lubuntu 13.10)"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by LubLearner on 2013-10-26
Hi.

When I wake up the computer from sleep mode, Lubuntu 13.10 32 bits shows this message at the top right corner of the screen: the network has been shut (It is a translation). And I must reboot the computer to get access to internet. This has been happening since it was upgraded from 13.04 to 13.10.

The computer uses an ethernet connection and it has not got any wireless adapter.

What might the problem be? How could I fix it?

---

### Post by LubLearner on 2013-10-26
The computer also blocks internet when I put it in hibernate mode, which I have just checked.

---

### Post by vasa1 on 2013-10-26
You may also want to ask at [http://www.facebook.com/groups/lubuntu.official/](http://www.facebook.com/groups/lubuntu.official/). It seems to be where a lot of Lubuntu support questions are being asked and answered.
Of course, the questions and answers there are not accessible without an account and are not accessible to search engines :)

---

### Post by Toz on 2013-10-26
You may just need to unload and reload the ethernet driver through the suspend/resume process. What does the following command, entered in a terminal window, return:
```
lspci -k | grep -iA2 ethernet
```

---

### Post by LubLearner on 2013-10-27
lspci -k | grep iA2 ethernet returns:

```
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
        Kernel driver in use: 8139too
```

The computer has an old modem too I do not use.

If I type "ifconfig" when there is not internet, the command does not detect the ethernet connection (eth0). It only returns some lines of information about "lo        Link encap:Bucle local" I do not know what it might be. Then, if I type "ifconfig -a", the command detects both devices (eth0 and lo). However the information about eth0 is diferent from the case with internet.

If there is internet, "ifconfig" says about eth0 (I have hidden some codes for privacy):
```
eth0      Link encap:Ethernet  direcciónHW [deleted device MAC]  
          Direc. inet:[deleted IP]  Difus.:[deleted IP]  Másc:[deleted IP]
          Dirección inet6: [deleted inet6 code] Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1638 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1782 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:884948 (884.9 KB)  TX bytes:224193 (224.1 KB)
```

If there is not internet, "ifconfig -a" says about eth0 (I have hidden the MAC for privacy):
```
eth0      Link encap:Ethernet  direcciónHW [deleted device MAC]  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:15480 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:13634 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:15147049 (15.1 MB)  TX bytes:1906687 (1.9 MB)
```

The "ip link" command detects "lo" and "eth0" with or without internet, but its message changes.

If there is internet, "ip link" returns:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN mode DEFAULT qlen 1000
    link/ether [deleted device MAC] brd ff:ff:ff:ff:ff:ff
```

If there is not internet, "ip link" returns:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT qlen 1000
    link/ether [deleted device MAC] brd ff:ff:ff:ff:ff:ff
```

---

### Post by Toz on 2013-10-27
Lets try this first. From a terminal window...

1. With root privlidges, create a pm-utils hook:
```
sudo -i leafpad /etc/pm/config.d/modules
```
...enter your password when prompted.

2. Copy/paste the following:
```
SUSPEND_MODULES="8139too"
```

3. Save the file.

4. Try suspending again. 

If it doesn't work, can you please post back:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated, and:
```
cat /var/log/syslog | grep PM:
```
...and post back the results.

---

### Post by LubLearner on 2013-10-27
How can I tell Lubuntu that the file is a script for shell? I might name it "modules.sh" and mark it as executable, but the script files in similar folders have not got any extensions


> **vasa1 said:**
> You may also want to ask at [http://www.facebook.com/groups/lubuntu.official/](http://www.facebook.com/groups/lubuntu.official/). It seems to be where a lot of Lubuntu support questions are being asked and answered.
Of course, the questions and answers there are not accessible without an account and are not accessible to search engines :)

I'd rather ask in these forums than in a social network, but I will write it down in case I need it.

---

### Post by Toz on 2013-10-27
> **LubLearner said:**
> How can I tell Lubuntu that the file is a script for shell? I might name it "modules.sh" and mark it as executable, but the script files in similar folders have not got any extensions
Its not really a script - its a configuration directive that will be read by pm-utils as it processes the suspend/hibernate action. The file is fine as it is. We can see if its been properly processed by reviewing the /var/log/pm-suspend.log file and searching for the 75modules section (towards the end of the file).

---


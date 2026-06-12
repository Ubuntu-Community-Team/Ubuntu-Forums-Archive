---
title: "allow wait time before second command"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by john_r on 2011-02-09
I am trying to make a launcher on the Desktop with 2 commands. The first command is connecting to a VPN, the second command is connecting to the print server in that VPN. I need the second command to wait about 20 seconds before trying to connect, in order to allow the first command to fully execute.

If anyone can help me, I would appreciate it!!!!

This is what I have in the launcher's command line so far:

sh -c "/opt/cisco/vpn/bin/vpnui & sh Desktop/"pc-client-linux.sh""

---

### Post by PunkLV on 2011-02-09
```
#!/bin/bash
sh -c /opt/cisco/vpn/bin/vpnui 
sleep 20s
sh Desktop/pc-client-linux.sh
```
save as **name.sh**
in launcher propeties, where you are currently trying do:
*sh /paht/to/name.sh*

---

### Post by john_r on 2011-02-09
That worked! Is there any way that rather than waiting 20 seconds, it could just automatically type in the password for the VPN, and then run the pc-client-linux.sh directly after the VPN is connected?


The 20 seconds was only to allow me enough time to type in the password, and allow the VPN to connect.

Thanks!

---

### Post by PunkLV on 2011-02-09
Doesn't the **vnpui** have an option to parse the login :: passw combo right from the start?

I assume you use **vpnc** - Cisco-compatible VPN client and if I am right you may find this helpful [http://linux.die.net/man/8/vpnc](http://linux.die.net/man/8/vpnc)

---

### Post by Primefalcon on 2011-02-09
sorry misread the condition....

---


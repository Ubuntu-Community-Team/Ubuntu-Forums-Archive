---
title: "WPA not working after restart"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by bbmak on 2007-08-04
Hi,
I am using xubuntu 7.04
After restarting the box, my wpa connection is dead. 
I have to restart my network to have my wpa connection back.

Are there anyway to fix this problem?

---

### Post by noob12 on 2007-08-04
Do you mean from a suspended state or a clean boot?

---

### Post by bbmak on 2007-08-04
clean reboot
but when i restart /etc/init.d/networking    it works again.

> bbmak@ubuntu:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                                         [ OK ]


---

### Post by noob12 on 2007-08-04
OK.  And can you elaborate on "WPA not working".

Are you using NetworkManager to configure your wireless or have you got manual entries in 
/etc/network/interfaces and wpa_supplicant.conf?

Can you post the output of 

> 
dmesg


And when you're in the "WPA not working" condition, can you grab the output of

```

ifconfig -a

lshw -C network

ps -ef | grep wpa_supplicant

iwconfig

iwlist scan

```

and save it to post it after you restart networking.

---


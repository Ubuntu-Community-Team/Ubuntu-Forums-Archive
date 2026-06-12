---
title: "http://localhost domain name unusable after installing new adsl router"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by Parapan on 2017-05-02
Hello,

I have Apache installed and the server directory index was accessible using [http://localhost](http://localhost) before I recently installed a new Dlink ADSL2+ Modem+Router . Now the apache web server contents are only accessible using the address [http://127.0.0.1](http://127.0.0.1) in the web browser. Using [http://localhost](http://localhost) displays a "403 Forbidden (nginx)" message. When I unplug my ethernet cable from the PC and restart networking , [http://localhost](http://localhost) can once again be used to access the web server.

I have tried assigning a new domain name 'localwebserver' in the /etc/hosts file to 127.0.0.1 but then the browser displays a message "Critical error: no domain selected!"


My **/etc/hosts** file :
```

127.0.1.1 avinash-ubuntu
127.0.0.1 localhost
127.0.0.1 localwebserver

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


My** /etc/network/interfaces** file
```

auto lo eth0

iface lo inet loopback

iface eth0 inet dhcp

```

How can I get localhost to display the apache server contents? Haven't found any option on the modem config page that is related (to my knowledge)

Thanks

---


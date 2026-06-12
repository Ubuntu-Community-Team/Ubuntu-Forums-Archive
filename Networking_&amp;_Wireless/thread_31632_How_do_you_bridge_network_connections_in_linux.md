---
title: "How do you bridge network connections in linux"
date: 2005-05-04
forum: Networking &amp; Wireless
---

### Post by i_know_tim on 2005-05-04
I have a linux box (running ubuntu) and a windows machine. The linux box has 2 network cards in it that are installed correctly. I am connected to a network which gives me access to the internet. I want to be able to connect my windows machine to one of the network cards on my linux box and the other two my single nerwork port in my room. The network uses dhcp and it would be preferable if both pc's used the networks dhcp server.

I know how to do this in windows easily but i can't do it in linux. In windows you just select the two network connections and click bridge and it's just like both computer are connected to a switch. 

How do you do this in linux though? I had a little bit of an idea how to do it in Gentoo linux but that doesn't work on the old b&w g3 mac i am using as a linux box. Does anyone have any ideas on how to do this? I really couldn't be bothered buying a switch to do this.

---

### Post by banadushi on 2005-05-04
Install bridge-utils, then in /etc/network/interfaces put:
```

iface br0 inet dhcp
    bridge_ports all

```
You can then ifup br0, it will get an IP and act as a normal interface as well as all physical interfaces act as switch ports.

---

### Post by i_know_tim on 2005-05-04
Ok i'm new to Ubuntu and i'm having trouble installing bridge-utils. I can't find it in the list of packages in package manager and i can't install it using the command line either. I get the error Couldn't find package bridge-utils.

---

### Post by Fab on 2005-05-04
[QUOTE=i_know_tim]Ok i'm new to Ubuntu and i'm having trouble installing bridge-utils. I can't find it in the list of packages in package manager and i can't install it using the command line either. I get the error Couldn't find package bridge-utils.[/QUOTE]
 enable the extra repos -> ubuntuguide.org

---

### Post by i_know_tim on 2005-05-08
[QUOTE=Fab]enable the extra repos -> ubuntuguide.org[/QUOTE]

thanks problem solved. i just installed it manually but now i have to work out why it keeps restarting by itself every now and then

---

### Post by i_know_tim on 2005-05-10
ok. my ubuntu machine keeps restarting and i have no idea why but i'll work that out later. The problem is when it does the network bridge doesn't come back up. where can i put 'ifup br0' so the network comes back up on reboot.

---


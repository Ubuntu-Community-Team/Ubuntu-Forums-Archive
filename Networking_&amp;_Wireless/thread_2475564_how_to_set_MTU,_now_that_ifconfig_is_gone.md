---
title: "how to set MTU, now that ifconfig is gone"
date: 2022-06-01
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2022-06-01
how to set MTU, now that *ifconfig* is gone and *ip* command doesn't do it?

---

### Post by ajgreeny on 2022-06-01
If you have network-manager installed you can set a specific MTU in that.

I'm sure it must also be possible by editing a config file somewhere but I'm not using Linux to type this so can't search for anything on this machine.

---

### Post by Skaperen on 2022-06-01
> **ajgreeny said:**
> If you have network-manager installed you can set a specific MTU in that.

I'm sure it must also be possible by editing a config file somewhere but I'm not using Linux to type this so can't search for anything on this machine.

i'm using a script to set up a tunnel when it is needed and it needs to set a few things on the local end of the tunnel.  so, i need to set it as a command.  it was previously doing it with *ifconfig* but that is not found in 20.04 (not going to 22.04, yet).

---

### Post by &amp;KyT$0P# on 2022-06-01
Not sure if this would be a solution or not, but you can still install [FONT=Courier New]ifconfig[/FONT] -
```
sudo apt-get install net-tools
```

---

### Post by ajgreeny on 2022-06-02
Yes, it looks as if ifconfig can still do this in 22.04 so I will be surprised if it's not also possible in 20.04.
From ***man ifconfig ***
```
 mtu N  This parameter sets the Maximum Transfer Unit (MTU) of an interface.
```

---

### Post by TheFu on 2022-06-02
```
# ip link set em1 mtu 9000
```

Inside the netplan.yaml files ...
```
network:
  version: 2
  renderer: networkd
  ethernets:
    # Configure MTU
    em0:
      match:
        macaddress: 00:e0:aa:bb:cc:dd
      mtu: "9000"
```

---

### Post by mIk3_08 on 2022-06-03
> **Skaperen said:**
> how to set MTU, now that *ifconfig* is gone and *ip* command doesn't do it? What is the difference setting up MTU to your local router and to your desktop machine? Is there any differences between the two? How it benefit to your machine? Regards and Cheers.

---

### Post by TheFu on 2022-06-03
> **mIk3_08 said:**
> What is the difference setting up MTU to your local router and to your desktop machine? Is there any differences between the two? How it benefit to your machine? Regards and Cheers.

Yes. There is a difference and there are many reasons to use a non-default MTU.  Plenty of web articles explain that. Look up "jumbo frames" to get started.

---

### Post by mIk3_08 on 2022-06-04
> **TheFu said:**
> Yes. There is a difference and there are many reasons to use a non-default MTU.  Plenty of web articles explain that. Look up "jumbo frames" to get started. Ah... i see. Thanks a lot TheFu

---

### Post by TheFu on 2022-06-04
Sometimes VPNs also need a non-standard MTU to work correctly.

---

### Post by Skaperen on 2022-06-18
> **TheFu said:**
> Sometimes VPNs also need a non-standard MTU to work correctly.

very true.  this is the "why" in my case.

i got an answer on Linux Questions on how to do it in the *ip* command, which was not in its man page.  i should have just up and tried the command as it is so obvious.  but in this case i checked the man page first, even though i've seen many cases of bad man pages.

[https://www.linuxquestions.org/questions/linux-networking-3/command-to-set-mtu-on-an-interface-that-is-not-ifconfig-4175712881/](https://www.linuxquestions.org/questions/linux-networking-3/command-to-set-mtu-on-an-interface-that-is-not-ifconfig-4175712881/)

---


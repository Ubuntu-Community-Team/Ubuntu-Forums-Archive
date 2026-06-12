---
title: "I cannot see my router in my LAN (wired network)"
date: 2020-04-15
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2020-04-15
Hello

I was navigating the internet without problem with a static IP address previously configured by means of updating /etc/netplan/[01-netcfg.yaml]("http://01-netcfg.yaml") in a computer with Lubuntu [18.04]("http://18.04") 

After trying to change to a new static IP address by means of updating again the file /etc/netplan/[01-netcfg.yaml]("http://01-netcfg.yaml") with a new static IP adress, I cannot even see the router with [192.168.1.1]("http://192.168.1.1"). I tried to change that to the old ip static adress but I cannot even see the router either by doing so now. Before having this problem I could see my static IP address by typing ```
ip addr show
``` in the terminal. But no static IP address gets displayed anymore after typing this command.

The current content of /etc/netplan/[01-netcfg.yaml]("http://01-netcfg.yaml") is:
> # This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      addresses: [192.168.1.141/24]
      gateway4:  192.168.1.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]

The current output of the command ip addr show is:

```
ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens33: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:19:21:45:79:c4 brd ff:ff:ff:ff:ff:ff

```

As you can see no static IP address gets displayed now after typing ip addr show.

I already made sure the ethernet cable is correctly connected both at the computer side and at the router side.

Would anyone be so nice to tell me any tip about why I cannot see my router at 192.168.1.1 by means of the LAN and why I do not see the static ip address with  any more?


Thanks in advance

---

### Post by thosecars822 on 2020-04-15
I changed the port of the router where the ethernet cable gets connected and I saw the green light of the port started blinking back again. For some reason it did not blink before that even though I had already tried by changing the cable from port to port to at least 3 different ports of the router.
I do no know how but the problem got solved somehow by unplugging and plugging again the ethernet cable to the ethernet ports of the router.

Just for the sake of getting to know the reason why the ethernet connection did not work, I tried connecting the ethernet cable to each of  the router ports now and I discovered there is one port in which there is not green light blinking after connecting the cable and I do not get ethernet connection at the computer either. Anyway I do not think that was the problem I had because I did not use that particular port before and I did not change the cable when I had the problem described in my first post.

---

### Post by The Cog on 2020-04-15
NO-CARRIER means there's a problem with the physical connection - cable fallen out, other end switched off, or something low-level like that.

Edit: Ah, you fixed it while I was typing. Good. Thanks for the update.

---


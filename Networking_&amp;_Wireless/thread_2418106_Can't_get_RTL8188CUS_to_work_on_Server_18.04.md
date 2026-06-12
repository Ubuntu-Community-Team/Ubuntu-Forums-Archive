---
title: "Can't get RTL8188CUS to work on Server 18.04"
date: 2019-05-01
forum: Networking &amp; Wireless
---

### Post by russdirks on 2019-05-01
I've got a USB Wifi device with chipset RTL8188CUS in a computer which dual-boots to either 16.04 Desktop or 18.04 Server.  Wifi works fine in the Desktop with no special config required, but I can't get it to work under the Server.

Info script : [http://paste.ubuntu.com/p/GQJ7DP3gT6/](http://paste.ubuntu.com/p/GQJ7DP3gT6/)


I tried the following .yaml config in /etc/netplan, but no joy:

```

network:
  version: 2
  renderer: networkd
  wifis:
    wlx40a5ef0c9bfe:
      dhcp4: yes
      dhcp6: no
      access-points:
        "ddddd":
          password: "pppppp"
```

Can anybody help me?

---

### Post by russdirks on 2019-05-01
Here's the output of the 'rfkill' command.  It wasn't installed when I ran the info script:

```

0: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```

---

### Post by russdirks on 2019-05-01
I got it working!  Turns out I need to install the wpasupplicant package.

---


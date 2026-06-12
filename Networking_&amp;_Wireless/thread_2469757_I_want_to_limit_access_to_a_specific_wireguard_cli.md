---
title: "I want to limit access to a specific wireguard client using UFW."
date: 2021-12-08
forum: Networking &amp; Wireless
---

### Post by wh33t on 2021-12-08
So I have a wireguard client that will connect into my server (ubuntu-server 20.04lts), they'll connect in on 10.0.0.3. When they connect in I only want them to be able to access a single IP address and a single port number on that ip address. 

Here is what my UFW status looks like right now, it doesn't work as expected, the client can still access any resource in the 192.168.0.x subnet. 

```
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     LIMIT       Anywhere
42069                      LIMIT       Anywhere
192.168.0.253 80           ALLOW       10.0.0.3
Anywhere                   DENY        10.0.0.3
22/tcp (v6)                LIMIT       Anywhere (v6)
42069 (v6)                 LIMIT       Anywhere (v6)
```

What am I doing wrong here? Any tips in the right direction greatly appreciated.

---

### Post by #&amp;thj^% on 2021-12-08
Have look here: [https://www.procustodibus.com/blog/2021/05/wireguard-ufw/](https://www.procustodibus.com/blog/2021/05/wireguard-ufw/)
You haven't mentioned who, what, and where you've done things, so sorry if you if you have seen it before.

---

### Post by wh33t on 2021-12-08
> **1fallen said:**
> Have look here: [https://www.procustodibus.com/blog/2021/05/wireguard-ufw/](https://www.procustodibus.com/blog/2021/05/wireguard-ufw/)
You haven't mentioned who, what, and where you've done things, so sorry if you if you have seen it before.

Aye, I read over that earlier. That's not quite what I'm looking for though. 

I read the rules I have in place and has everything I want in it, it just doesn't work. It has a single explicit rule that says what I want to allow, and then denies everything else from that one IP. It just doesn't work. I don't get it. 

Appreciate the response though.

---

### Post by #&amp;thj^% on 2021-12-08
Give me some time I'm on machine I can't mess with ATM.
I use firewalld though. :)
```
System:
  Host: me-Standard-PC-i440FX-PIIX-1996 Kernel: 5.4.0-1007-fips x86_64 
  bits: 64 Desktop: MATE 1.24.0 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) 
  v: pc-i440fx-6.1 serial: <superuser/root required> 
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: ArchLinux 1.14.0-1 
  date: 04/01/2014 
CPU:
  Topology: 12-Core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64 
  type: MCP L2 cache: 6144 KiB 
  Speed: 2994 MHz min/max: N/A Core speeds (MHz): 1: 2994 2: 2994 3: 2994 
  4: 2994 5: 2994 6: 2994 7: 2994 8: 2994 9: 2994 10: 2994 11: 2994 12: 2994 
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
  Display: x11 server: X.Org 1.20.11 driver: none 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.0.3 
Audio:
  Device-1: Intel 82801FB/FBM/FR/FW/FRW High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-1007-fips 
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge 
  driver: piix4_smbus 
  Device-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter 
  driver: 8139cp 
  IF: ens3 state: up speed: 100 Mbps duplex: full mac: 52:54<snip>
Drives:
  Local Storage: total: 23.30 GiB used: 7.20 GiB (30.9%) 
  ID-1: /dev/sda vendor: QEMU model: HARDDISK size: 23.30 GiB 
Partition:
  ID-1: / size: 21.38 GiB used: 7.16 GiB (33.5%) fs: ext4 dev: /dev/dm-0 
  ID-2: swap-1 size: 980.0 MiB used: 46.3 MiB (4.7%) fs: swap dev: /dev/dm-1 
Sensors:
  Message: No sensors data was found. Is sensors configured? 
Info:
  Processes: 274 Uptime: 1h 23m Memory: 1.94 GiB used: 1.32 GiB (68.3%) 
  Shell: bash inxi: 3.0.38 
```

---

### Post by Doug S on 2021-12-11
UFW is just a front end for iptables. While UFW generated iptables rule sets are difficult and annoying to follow, maybe that is where to look. Please post the output for "sudo iptables -xvnL".

---

### Post by The Cog on 2021-12-11
I prefer looking at the output of [FONT=Courier New]**sudo iptables-save -c**[/FONT] to look at this kind of problem. You don't miss anything then, and it's in the format you would use to re-enter the rules.

One thing I would point out that after changing the firewall rules won't break any already-established connections. A rule change can only prevent new connections. This is because firewall rules almost always include a clause that permits "established" connections.

---

### Post by #&amp;thj^% on 2021-12-14
> **The Cog said:**
> I prefer looking at the output of [FONT=Courier New]**sudo iptables-save -c**[/FONT] to look at this kind of problem. You don't miss anything then, and it's in the format you would use to re-enter the rules.

One thing I would point out that after changing the firewall rules won't break any already-established connections. A rule change can only prevent new connections. **_This is because firewall rules almost always include a clause that permits "established" connections._**

Agreed :)

---


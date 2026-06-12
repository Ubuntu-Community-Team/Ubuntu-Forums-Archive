---
title: "Aspire 5560 BCM57785 wired network not working"
date: 2023-02-05
forum: Networking &amp; Wireless
---

### Post by ak87 on 2023-02-05
Hi,

I just installed Ubuntu 20.04 server on old laptop (Acer Aspire 5560) and can't get wired network working.
I have looked at so many posts with similar problem and tried different stuff for couple of days now, nothing works, so I decided to start this thread.

What i learned is that the chip is NetLink BCM57785.

Running "lshw -C network" shows me that "*-network DISABLED" and that the driver is tg3 v3.137
Checking "ip a" shows that the enp1s0f0 is down.

Trying to bring it up using "ip a link set enp1s0f0 up" does not bring it UP

I have been banging my head with this so long and hope someone has a solution or a good way to troubleshoot this issue.

Thanks!

---

### Post by chili555 on 2023-02-05
In the server edition, networking is configured in netplan. Let's take a look. Please run and post:

```
cat /etc/netplan/*.yaml
```

---

### Post by ak87 on 2023-02-05
network:
    version: 2
    renderer: networkd

---

### Post by ak87 on 2023-02-05
Sorry about the indentations. Writing from phone as i have no internet on that laptop and can't copy paste

---

### Post by jeremy31 on 2023-02-05
Can you use USB tethering with the phone?

---

### Post by chili555 on 2023-02-05
Please do:

```
sudo nano /etc/netplan/*.yaml
```

Amend the file to:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0f0:
      dhcp4: true

```Netplan is very specific about indentation and spacing. Please proofread carefully twice. Save (Ctrl+o followed by Enter) and exit (Ctrl+x).

Follow with:

```
sudo netplan generate
sudo netplan apply
```

You will probably connect immediately but it might take a reboot.

---

### Post by ak87 on 2023-02-06
Hi again,

This didn't seem to work, even after reboot.

Here is the output of "sudo netplan --debug apply"

[ATTACH=CONFIG]291714[/ATTACH]

I also noticed that the reboot took much longer after this change and saw a message that read:
"A start job is running for Wait for network to be Configured (1min 44s / no limit)"

---

### Post by chili555 on 2023-02-06
Network Manager?? It is not installed by default in the server edition of Ubuntu and, therefore, I assume you installed it later. Or is this actually a desktop installation? Or, even worse, a server that you attempted to convert to a desktop installation?

Having both an explicit netplan configuration *and* Network Manager sets up a conflict that we'll need to unravel.

Please clarify.

---

### Post by ak87 on 2023-02-06
This is ubuntu server 20.04 legacy, as i didnt want live install, because of no internet access

---

### Post by ak87 on 2023-02-06
I think i misunderstood the live image thing.
Will reinstall and do ubuntu 20.04 live server and try again.

---

### Post by chili555 on 2023-02-06
> **ak87 said:**
> I think i misunderstood the live image thing.
Will reinstall and do ubuntu 20.04 live server and try again.Excellent. Please check out the netplan file and you may need to amend it as above. It should work, even in the live session.

---

### Post by ak87 on 2023-02-06
> **chili555 said:**
> Network Manager?? It is not installed by default in the server edition of Ubuntu and, therefore, I assume you installed it later. Or is this actually a desktop installation? Or, even worse, a server that you attempted to convert to a desktop installation?

Having both an explicit netplan configuration *and* Network Manager sets up a conflict that we'll need to unravel.

Please clarify.

I reinstalled using Ubuntu 20.04 Live Server image and tried the steps again. 
The output is still same (with NetworkManager stuff)

---

### Post by chili555 on 2023-02-06
> Ubuntu 20.04 Live Server image 

May I see the download link?

Let's try another method. Assuming that the interface is still enp1s0f0, please do:

```
sudo dhclient enp1s0f0
```

Did you connect?

---

### Post by ak87 on 2023-02-07
> **chili555 said:**
> May I see the download link?

Let's try another method. Assuming that the interface is still enp1s0f0, please do:

```
sudo dhclient enp1s0f0
```

Did you connect?

I used this link:
[https://releases.ubuntu.com/20.04.5/ubuntu-20.04.5-live-server-amd64.iso](https://releases.ubuntu.com/20.04.5/ubuntu-20.04.5-live-server-amd64.iso)

Here is a screengrab of the installed version:
[img]https://i.imgur.com/E7kEPvq.jpg[/img]

I tried running 
```
sudo dhclient enp1s0f0
```

but nothing happened.

Here is the output for
```
sudo dhclient -v enp1s0f0
```

[img]https://i.imgur.com/okqizgN.jpg[/img]

---

### Post by chili555 on 2023-02-09
Sorry, I have no further useful suggestions.

---


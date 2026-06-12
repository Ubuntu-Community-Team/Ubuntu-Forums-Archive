---
title: "ifconfig acting strange, so close to having wireless work..."
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by epud on 2007-04-21
I installed my drivers for my WUA-1340 using ndiswrapper. Then when I write:

```
iwlist wlan0 scan
```

i get the output

```
wlan0       No scan results
```

I have noticed however that if I write

```
ifconfig wlan0 down
```

followed by

```
ifconfig wlan0 up
```

for a few seconds it shows me:

```
Scan completed:
Cell 01: - Adress: (then an address here)
               ESSID: linksys
               ... etc.
```

What is wrong? Why won't it stay configured?
Thanks

---

### Post by epud on 2007-04-21
Now I am wondering if it is at all picking up the signals from the router. How do I check if the wireless USB is at all picking up any signals?

Thanks

---

### Post by epud on 2007-04-21
Nobody knows what is wrong? :(

---

### Post by Nellephant on 2007-04-22
I have much the same problem with a Netgear USB adaptor and an Orange Livebox

After 12 hours I have managed to get Ubuntu to recognise my Netgear adaptor (using ndiswrapper and Windows drivers) but when I scan for the Livebox with 'iwlist scan' it produces no results

So near and yet so far....anyone any suggestions?? :confused:

---

### Post by chili555 on 2007-04-22
In 'scan' there is generally a default timeout of two seconds. Your card may not be able to go through 11 or 13 channels, in two seconds, depending on where it randomly was when you started. So it gives, "No scan results." Sometimes this can be solved by just trying three or four times.

Also, from man iwlist:>  Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results. So, you really want to do:```
**sudo** iwlist eth1 scan
```

---

### Post by epud on 2007-04-22
When doing that I get:
```
eth1      Interface doesn't support scanning.
```

The Ethernet cable connection is working fine.

Actually, what would be the next step for me to take to get my wireless working?

I have tried ```
iwlist wlan0 scan
``` other places and it is picking up the signals when I do what is explained in the first post.

What should the network settings be set at? what is the difference between wlan0 and wmaster0? Should I have roaming mode enabled?

Thanks

---

### Post by chili555 on 2007-04-22
Sorry if I wasn't clear. I expected you would substitute your wireless interface if it wasn't eth1. Also, as I tried to point out, the scan command should be run with 'sudo.'

---

### Post by epud on 2007-04-22
I have been using sudo. Sorry for not writing that. Even as a super user / using sudo I am still getting the same resonse (no scan results.) That is after changing it to wlan0 too.

Thank you for you help so far!

---

### Post by okey666 on 2007-10-02
I have the same problem with my NetGear WG311TGE PCI card. I use the madwifi drivers.

---


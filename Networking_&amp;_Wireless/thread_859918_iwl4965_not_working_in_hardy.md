---
title: "iwl4965 not working in hardy"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by sebast on 2008-07-15
Hi,

I've been looking around for hours now but can't seem to find how to make my wireless work for my iwl4965 card. It just doesn't show up in Network manager like it doesn't exist.

I upgraded to Network-manager-0.7 svn to see if it makes a difference, but the problem stays to same.

here is my sudo lshw:

```
   *-network
        description: Network controller
        product: PRO/Wireless 4965 AG or AGN Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:02:00.0
        version: 61
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: driver=iwl4965 latency=0 module=iwl4965
```

lsmod lists that:

```
iwl4965               105844  0 
```

But here is what iwconfig says:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

I've been looking in the forums but straight and easy to follow answers are hard to find. I tried installing the compat-wireless package but it doesn't make any difference, I still have the same problem.

The wired connection works fine but no wireless at all.

Any help is appreciated. I don't have a lot of experience with wireless and network connections under Linux so that's why I tried things that seem pretty random to me (network-manager 0.7 and compat-wireless) without knowing if and how it would fix the problem.

---

### Post by sebast on 2008-07-15
I was still looking on the Internet and came across this project: [www.intellinuxwireless.org]("http://www.intellinuxwireless.org/") which seem to give a solution for the exact driver I have.

However, it's not clear how to install and use it at all and I don't really get it.

---

### Post by sebast on 2008-07-15
Is there a easy way to make this driver work with NDISwrapper instead of the regular driver since nothing seems to work?

---

### Post by shift0 on 2008-07-16
i also cannot get my 4965agn working in hardy.  tried everything, any help?

---

### Post by nickel on 2008-07-25
I am new to Hardy as of today and I'm having the same issue with the intel 4965 agn wifi.  My iwconfig gives the same no wireless extension.  Any help would be greatly appreciated.

cheers

---

### Post by chili555 on 2008-07-25
Is everyone's switch in the right position?```
sudo cat /var/log/messages | grep switch
```Also, have you installed *backports*? There is evidently an improved driver in there.```
sudo apt-get install linux-backports-modules-hardy-generic
```You might also note that Network Manager will not activate your wireless as long as there is a working connection through ethernet. So, please detach the wire before you continue your efforts to connect wirelessly.

I fear some on this forum blame a Network Manager issue on the driver, install a different driver, find that it still doesn't work, try ndiswrapper, find that it still doesn't work, and give up. I think, in many cases, it's a problem other than the driver.

---

### Post by Creap on 2008-08-02
> **chili555 said:**
> You might also note that Network Manager will not activate your wireless as long as there is a working connection through ethernet. So, please detach the wire before you continue your efforts to connect wirelessly.
Still, you should be able to **see** any available networks and at least your network card even when connected via ethernet, right?

Installing backports helped me getting to the point of wlan0 showing up in iwconfig, but in lshw -C network it shows up as *-network DISABLED...

---

### Post by chili555 on 2008-08-02
> in lshw -C network it shows up as *-network DISABLEDThis is often a sign the wireless switch on your laptop is moved to 'off.' Check with:```
sudo cat /var/log/messages | grep switch
```

---

### Post by Creap on 2008-08-02
> **chili555 said:**
> This is often a sign the wireless switch on your laptop is moved to 'off.' Check with:```
sudo cat /var/log/messages | grep switch
```
```
Aug  2 13:38:45 munin kernel: [   17.294008] SMP alternatives: switching to UP code
Aug  2 13:38:45 munin kernel: [   30.965822] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug  2 13:41:18 munin kernel: [  123.360371] iwl4965: Radio disabled by HW RF Kill switch
Aug  2 13:41:38 munin kernel: [  129.839409] iwl4965: Radio disabled by HW RF Kill switch
Aug  2 15:43:45 munin kernel: [   18.417610] SMP alternatives: switching to UP code
Aug  2 15:43:45 munin kernel: [   20.051490] ACPI: EC: non-query interrupt received, switching to interrupt mode

```
Nothing happens when doing Fn + F2 (my software switch) or switching the hardware switch.. My other Fn + FX keys works OOB.. :-\

---


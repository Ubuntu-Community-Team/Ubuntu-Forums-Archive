---
title: "Network setup issues. No IPv4"
date: 2022-07-18
forum: Networking &amp; Wireless
---

### Post by johndid on 2022-07-18
Hi everyone,

My Lubuntu 19.20 runs on a VM. I don't know whether I modified or changed something (maybe it is last update's fault), but at the next boot my linux machine doesn't seem to be able to connect to my LAN network, and thus internet as well.

I see such a nm-tray icon in my tray bar:

[https://imgur.com/qdF6hEI](https://imgur.com/qdF6hEI)


I tried to restart the network service:

[B]sudo systemctl restart NetworkManager.service

[/B]I then checked its status


[B] sudo systemctl restart NetworkManager.service

[/B]```

....
Active: active (running) since Sun 2022-07-17 11:24:40 CEST; 1min 4s ago
....

```


and the **ip a** command:

```
ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:9e:xx:57 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::xxc:29ff:fe9x:cd57/64 scope link 
       valid_lft forever preferred_lft forever
```

It seems that it can't get an IP.

Could you please help me figure this problem out and fix it?
Thanks

---

### Post by TheFu on 2022-07-18
Is this a virtual machine?
Is the DHCP server working?

---

### Post by johndid on 2022-07-18
> **TheFu said:**
> Is this a virtual machine?
Is the DHCP server working?

The dhcp server runs on my home router (a Mikrotik device). I have other virtual machines running in VMware workstation which haven't this type of issue.
Thanks

---

### Post by TheFu on 2022-07-18
> **johndid said:**
> The dhcp server runs on my home router (a Mikrotik device). I have other virtual machines running in VMware workstation which haven't this type of issue.
Thanks

Lubuntu 19.20 doesn't exist.  The releases happen in April (04) or October (10) for all Ubuntu flavors.  All 19.xx and 21.xx releases are out of support.  20.04 (most releases) and 22.04 releases are still supported.
So, the first thing is to install a supported OS.

Or say the real release and get the thread moved to the "Other Unsupported OS" subforum.

I've had a *network doesn't work* issue with 1 virtual machine and was never able to figure out the root cause. It would start working about a week later. This happened a few times over a 6 month period. At the same time, 10+ other VMs on the same system didn't have any network issues at all. None.  
 I moved the VM do a different system and it has been working on that one for over 3 years now ... including after changing the underlying hardware from a Pentium (2015) to a Ryzen CPU last fall. I didn't install/reinstall the OS, just swapped out the MB+CPU.  I haven't seen the same issue again.

I was not using VMware Workstation with these issues.  I use KVM as the hypervisor and manually create a bridge/PCIe passthru for the NIC. Also, I don't use DHCP, but use static IPs manually setup on-the-OS inside the VM.

General troubleshooting requires that we simplify and test, then repeat until the smallest root cause can be isolated.  To that end, my suggestion would be to setup a static IP inside the VM and don't use DHCP.  If that solves it, great. You have a workable solution and have removed an external dependency that isn't needed anyway.
If that doesn't fix the issue, we've just learned that it is likely internal to the OS and can look at other aspects like ensuring the virtual hardware presented are all standard - like using virtio for network and disk controllers.  Reinstalling the guest additions (required after every new kernel), stuff like that.

---

### Post by johndid on 2022-07-19
> **TheFu said:**
> Lubuntu 19.20 doesn't exist.  The releases happen in April (04) or October (10) for all Ubuntu flavors.  All 19.xx and 21.xx releases are out of support.  20.04 (most releases) and 22.04 releases are still supported.


.10. Typo of course.


> 

...


General troubleshooting requires that we simplify and test, then repeat until the smallest root cause can be isolated.  To that end, my suggestion would be to setup a static IP inside the VM and don't use DHCP.  If that solves it, great. You have a workable solution and have removed an external dependency that isn't needed anyway.
If that doesn't fix the issue, we've just learned that it is likely internal to the OS and can look at other aspects like ensuring the virtual hardware presented are all standard - like using virtio for network and disk controllers.  Reinstalling the guest additions (required after every new kernel), stuff like that.



I didn't know that reinstalling the guest additions are required after every new kernel.

Thanks

---

### Post by TheFu on 2022-07-19
> **johndid said:**
> .10. Typo of course.

There are no supported xx.10 releases of Ubuntu today.
I provided a bunch of other ideas. Please try them and report back what was done and the result.

---

### Post by guiverc on 2022-07-19
Lubuntu 21.10 is EOL

Link for Lubuntu 21.10 - [https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/)
A general Ubuntu 21.10 notice - [https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/](https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/)
Warning notice for Ubuntu 21.10 - [https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/](https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/)

*I've not responded before as 19.20 (20th month?) made no sense. Also note  updates too makes little sense as few changes occur during the *[I]last days (week+) of a releases supported life, so the queues of any proposed packages reach end users rather than being dropped as happens at EOL.  Thus I'd assume it's user created issue if within the last week+
[/I]

---


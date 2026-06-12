---
title: "Ubuntu 16.04 on Toshiba dynabook: No network devices available"
date: 2017-02-14
forum: Networking &amp; Wireless
---

### Post by martillu on 2017-02-14
Dear all,
I just installed ubuntu 16 on a Toshiba dynabook and upgraded the kernel to 4.9. However, I don't get the wireless to work (I am posting this from another laptop). I get the message "No network devices available" 

Doing ```
sudo lshw -C network yields:
*-network UNCLAIMED     
   description: Network controller
   product: Intel Corporation
   vendor: Intel Corporation
   physical id: 0
   bus info: pci@0000:01:00.0
   version: 78
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress cap_list
   configuration: latency=0
   resources: memory:c8000000-c8001fff
```

I also did:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
which was said in another thread to work but in my case it didn't

I guess the drivers are not there or not working. Any idea what is wrong?

---

### Post by jeremy31 on 2017-02-14
Post results for ```
lspci -nnk | grep -iA2 net
```

---

### Post by martillu on 2017-02-14
Here is the output:
```
01:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0110]
    Kernel modules: iwlwifi
```

---

### Post by slickymaster on 2017-02-14
@martillu:
Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in your posts. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by jeremy31 on 2017-02-14
Does it work after ```
sudo modprobe iwlwifi
```

---

### Post by martillu on 2017-02-14
Thank you for the suggestion...but no, it doesn't work (I even tried restarting the laptop)
(and sorry for not using the code tags before. I will do so in the future)

I also did:
```
dmesg | grep iwl
[    4.551199] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    4.556549] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    4.556763] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    4.556787] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    4.556796] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    4.556805] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[    4.556815] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-21.ucode failed with error -2
[    4.556823] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8265-20.ucode failed with error -2
[    4.556825] iwlwifi 0000:01:00.0: no suitable firmware found!

```

There is something fishy here....

---

### Post by martillu on 2017-02-14
Hey!
I downloaded somewhere else:
```

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.162_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.162_all.deb)

```
copied on Desktop of the laptop with no wifi and then did:
```

cd ~/Desktop
sudo dpkg -i linux-firmware_1.162_all.deb

```
After rebooting....it worked like a charm!!

Your clues help me a lot. Thank you!

---

### Post by slickymaster on 2017-02-14
Great everything is working now.

Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that this thread provides a working solution.

---


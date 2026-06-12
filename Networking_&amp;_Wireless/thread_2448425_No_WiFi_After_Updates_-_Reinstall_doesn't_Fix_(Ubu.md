---
title: "No WiFi After Updates - Reinstall doesn't Fix (Ubuntu 18.04)"
date: 2020-08-07
forum: Networking &amp; Wireless
---

### Post by ishmael3 on 2020-08-07
[SIZE=2]Greetings;[/SIZE]

[SIZE=2]I installed Ubuntu 18.04 on an  HP-Stream-Laptop-11 about a year ago (single boot). Working great until the latest update.[/SIZE]

[SIZE=2]Immediately after update restart there was no wifi access. I could find no cause for problem so reinstalled 18.04 (from same live USB as first installation). But, after several reinstall attempts, still no wifi!
[/SIZE]
[SIZE=2]Interestingly, Wifi works great when machine is booted from the live USB, and works during the install. Then, after restart... no wifi![/SIZE]

[SIZE=2]My first idea was that it had something to do with "MOK generation and signing," which I don't really understand, but think that I followed the procedure correctly as stated [here.]("https://wiki.ubuntu.com/UEFI/SecureBoot") (I don't remember how the MOK step went on the install a year ago. There were no MOK notices after the recent update.)[/SIZE]

[SIZE=2]Any help greatly appreciated. The laptop has no ethernet capability, only wifi (when working!). I would like to keep secure boot rather than going legacy -- in case that seems like the issue.  [/SIZE]

[SIZE=2]If it helps, "sudo lshw -c network" returns the following:[/SIZE]

```

[SIZE=2]admin-user@tiny-blue:~$ sudo lshw -c network[/SIZE]
[SIZE=2]  *-network DISABLED         [/SIZE]
[SIZE=2]       description: Wireless interface[/SIZE]
[SIZE=2]       product: Realtek Semiconductor Co., Ltd.[/SIZE]
[SIZE=2]       vendor: Realtek Semiconductor Co., Ltd.[/SIZE]
[SIZE=2]       physical id: 0[/SIZE]
[SIZE=2]       bus info: pci@0000:01:00.0[/SIZE]
[SIZE=2]       logical name: wlo1[/SIZE]
[SIZE=2]       version: 00[/SIZE]
[SIZE=2]       serial: 40:5b:d8:44:42:0b[/SIZE]
[SIZE=2]       width: 64 bits[/SIZE]
[SIZE=2]       clock: 33MHz[/SIZE]
[SIZE=2]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/SIZE]
[SIZE=2]       configuration: broadcast=yes driver=rtw_pci driverversion=5.4.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11[/SIZE]
[SIZE=2]       resources: irq:124 ioport:1000(size=256) memory:91100000-9110ffff[/SIZE]

```

[SIZE=2] "sudo lspci -nnk | grep 0280 -A3" returns:[/SIZE]

```

[SIZE=2] admin01@tiny-blue:~$ sudo lspci -nnk | grep 0280 -A3[/SIZE]
[SIZE=2] 01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822][/SIZE]
[SIZE=2]     Subsystem: Hewlett-Packard Company Device [103c:85f7][/SIZE]
[SIZE=2]     Kernel driver in use: rtw_pci[/SIZE]
[SIZE=2]     Kernel modules: rtwpci[/SIZE]

```

"rfkill list all" returns:

  ```
  
  admin01@tiny-blue:~$ rfkill list all
  1: phy0: Wireless LAN
      Soft blocked: yes
      Hard blocked: no
  3: hci0: Bluetooth
      Soft blocked: no
      Hard blocked: no
  
```  
  
[SIZE=2] WiFi worked great until the recent update. Still works fine if running Ubuntu from live USB.  Any help greatly appreciated. (Really wanting to do this without going to legacy mode.)  [/SIZE]

[SIZE=2]Thanks much.[/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by jeremy31 on 2020-08-07
Have you tried a BIOS reset?

---

### Post by stevermann on 2020-08-07
> **ishmael3 said:**
> 
[SIZE=2] WiFi worked great until the recent update. Still works fine if running Ubuntu from live USB.  Any help greatly appreciated. (Really wanting to do this without going to legacy mode.)  [/SIZE]


[B]I AM NOT AN EXPERT

[/B]But this really sounds like a driver problem.

I would try running "sudo lspci -nnk | grep 0280 -A3" on both the normal boot and the USB boot and compare the outputs.
And, now we are completely out of my knowledge scope.  I have absolutely no clue how to install or update drivers in Linux.

When you fix this, please report back to the forum. I am sure others will want to know how you fixed it.

---

### Post by chili555 on 2020-08-08
>  admin01@tiny-blue:~$ rfkill list all
  1: phy0: Wireless LAN
      [COLOR="#FF0000"]Soft blocked: yes[/COLOR]
      Hard blocked: no
  3: hci0: Bluetooth
      Soft blocked: no
      Hard blocked: no

Soft blocked:Yes suggests that the Airplane Mode is set to On in Network Manager. Please switch it off.

---

### Post by ishmael3 on 2020-08-08
Hello,

Thanks, folks, for reading and responding!
 
 chili555 -- I don't know why that soft block was there. Airplane mode was definitely off. I ran  "rfkill list all" again this morning as part of comparison suggested by stevermann and there were no blocks. See comparison below.
 
 jeremy31 -- Can you explain what you're meaning by a "BIOS reset" and why it might apply? Searching the phrase pulls up several different procedures.
 
 stevermann -- I was intending to do that comparison. Here's the results; one set when booted to "live USB" (wifi working), and other set booted to "installed system" (no wifi).
 

 Booted from "live USB:"   "[FONT=Ubuntu]sudo lspci -nnk | grep 0280 -A3" and "rfkill list all" (YES wifi)[/FONT]
 
 ```

 [FONT=Ubuntu]ubuntu@ubuntu:~$ sudo lspci -nnk | grep 0280 -A3[/FONT]
 [FONT=Ubuntu]01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822][/FONT]
 [FONT=Ubuntu]    Subsystem: Hewlett-Packard Company Device [103c:85f7][/FONT]
 [FONT=Ubuntu]    Kernel driver in use: rtw_pci[/FONT]
 [FONT=Ubuntu]    Kernel modules: rtwpci[/FONT]
 
  [FONT=Ubuntu]ubuntu@ubuntu:~$ rfkill list all[/FONT]
 [FONT=Ubuntu]0: hci0: Bluetooth[/FONT]
 [FONT=Ubuntu]    Soft blocked: no[/FONT]
 [FONT=Ubuntu]    Hard blocked: no[/FONT]
 [FONT=Ubuntu]1: phy0: Wireless LAN[/FONT]
 [FONT=Ubuntu]    Soft blocked: no[/FONT]
 [FONT=Ubuntu]    Hard blocked: no[/FONT]
 [FONT=Ubuntu]ubuntu@ubuntu:~$ [/FONT] 
 
```
 
 [FONT=Ubuntu]Booted from "installed system:"  "sudo lspci -nnk | grep 0280 -A3" and "rfkill list all" (NO wifi)[/FONT]
 
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ lspci -nnk | grep 0280 -A3[/FONT]
 [FONT=Ubuntu]01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822][/FONT]
 [FONT=Ubuntu]    Subsystem: Hewlett-Packard Company Device [103c:85f7][/FONT]
 [FONT=Ubuntu]    Kernel driver in use: rtw_pci[/FONT]
 [FONT=Ubuntu]    Kernel modules: rtwpci[/FONT]
  
 [FONT=Ubuntu]admin01@tiny-blue:~$ rfkill list all[/FONT]
 [FONT=Ubuntu]0: hci0: Bluetooth[/FONT]
 [FONT=Ubuntu]    Soft blocked: no[/FONT]
 [FONT=Ubuntu]    Hard blocked: no[/FONT]
 [FONT=Ubuntu]1: phy0: Wireless LAN[/FONT]
 [FONT=Ubuntu]    Soft blocked: no[/FONT]
 [FONT=Ubuntu]    Hard blocked: no[/FONT]
 
```
 

 [FONT=Ubuntu]But here's what might be the most interesting, a comparison of "sudo lshw -c network" booted  "live" vs booted "installed:[/FONT]
 
 [FONT=Ubuntu]Booted from "live USB:"  "sudo lshw -c network" (YES wifi)[/FONT]
 
 ```

 [FONT=Ubuntu]ubuntu@ubuntu:~$ sudo lshw -c network[/FONT]
   [FONT=Ubuntu]*-network                 [/FONT] 
        [FONT=Ubuntu]description: Wireless interface[/FONT]
        [FONT=Ubuntu]product: Realtek Semiconductor Co., Ltd.[/FONT]
        [FONT=Ubuntu]vendor: Realtek Semiconductor Co., Ltd.[/FONT]
        [FONT=Ubuntu]physical id: 0[/FONT]
        [FONT=Ubuntu]bus info: pci@0000:01:00.0[/FONT]
        [FONT=Ubuntu]logical name: wlo1[/FONT]
        [FONT=Ubuntu]version: 00[/FONT]
        [FONT=Ubuntu]serial: 40:5b:d8:44:42:0b[/FONT]
        [FONT=Ubuntu]width: 64 bits[/FONT]
        [FONT=Ubuntu]clock: 33MHz[/FONT]
        [FONT=Ubuntu]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
        [FONT=Ubuntu]configuration: broadcast=yes driver=rtw_pci driverversion=5.0.0-23-generic firmware=N/A ip=192.168.254.25 latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT]
        [FONT=Ubuntu]resources: irq:16 ioport:1000(size=256) memory:91100000-9110ffff[/FONT]
 
```
 
 [FONT=Ubuntu]Booted from "installed system:"  [FONT=Ubuntu]"sudo lshw -c network"[/FONT][FONT=Ubuntu] (NO wifi)[/FONT][/FONT]
 
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ sudo lshw -c network[/FONT]
 [FONT=Ubuntu][sudo] password for admin01: [/FONT] 
   [FONT=Ubuntu]*-network DISABLED        [/FONT] 
        [FONT=Ubuntu]description: Wireless interface[/FONT]
        [FONT=Ubuntu]product: Realtek Semiconductor Co., Ltd.[/FONT]
        [FONT=Ubuntu]vendor: Realtek Semiconductor Co., Ltd.[/FONT]
        [FONT=Ubuntu]physical id: 0[/FONT]
        [FONT=Ubuntu]bus info: pci@0000:01:00.0[/FONT]
        [FONT=Ubuntu]logical name: wlo1[/FONT]
        [FONT=Ubuntu]version: 00[/FONT]
        [FONT=Ubuntu]serial: 40:5b:d8:44:42:0b[/FONT]
        [FONT=Ubuntu]width: 64 bits[/FONT]
        [FONT=Ubuntu]clock: 33MHz[/FONT]
        [FONT=Ubuntu]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
        [FONT=Ubuntu]configuration: broadcast=yes driver=rtw_pci driverversion=5.4.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11[/FONT]
        [FONT=Ubuntu]resources: irq:123 ioport:1000(size=256) memory:91100000-9110ffff[/FONT]
 
```
 
 [FONT=Ubuntu][FONT=Ubuntu]I[/FONT][FONT=Ubuntu] see a number of differences in the "configuration" sections of the last comparison but I do not know if they are significant, or (if they ARE important) where to go from here. 

[/FONT][FONT=Ubuntu] Thanks in advance for any advice or help offered.[/FONT][/FONT]

---

### Post by ishmael3 on 2020-08-10
Greetings,

I am in way over my head here, but it's looking like stevermann maybe has it right.  
 
 I'm finding a number of recent posts (and some not so recent) about wifi problems from Linux users whose machines use Realtek network devices [FONT=Ubuntu]like mine, [/FONT][FONT=Ubuntu]or similar. [/FONT] 
 
 [FONT=Ubuntu]And s[/FONT][FONT=Ubuntu]pecifically[/FONT][FONT=Ubuntu] finding recent posts about a bug concerning certain Realtek drivers [[like here]("http://https://answers.launchpad.net/ubuntu/+question/691415")]  that may be the same as mine.  Frankly, I am unclear about my exact driver designation (is it only "rtw_pci" or something else more precise?).[/FONT]
 
 [FONT=Ubuntu]Anyway, here's my simple-minded analysis -- please correct and advise:[/FONT]
 

 [FONT=Ubuntu]The[/FONT][FONT=Ubuntu] system operates with different Kernel[/FONT][FONT=Ubuntu]s[/FONT][FONT=Ubuntu] depending on whether [/FONT][FONT=Ubuntu]it is booted[/FONT][FONT=Ubuntu] from the Live USB or from the Installed System[/FONT][FONT=Ubuntu].[/FONT][FONT=Ubuntu]:[/FONT]
 
 **Kernel-- LIVE                                  (WiFi working)**
 ```

 ubuntu@ubuntu:~$ uname -r
 5.0.0-23-generic
 
```

 **Kernel-- LOADED                   (WiFi NOT working)**
 ```

 admin01@tiny-blue:~$ uname -r
 [FONT=Ubuntu]5.4.0-42-generic[/FONT]
 
```
 

 [FONT=Ubuntu]The same driver appears to be used either way,[/FONT][FONT=Ubuntu] but I'm not sure about that[/FONT][FONT=Ubuntu] ([/FONT][FONT=Ubuntu]is "driverversion=5.0.0-23-generic" really a different driver from "[/FONT][FONT=Ubuntu]driverversion=5.4.0-42-generic[/FONT][FONT=Ubuntu]"?[/FONT][FONT=Ubuntu])[/FONT][FONT=Ubuntu]:[/FONT]
 
 **Driver - LIVE                                (WiFi working)**
 ```

 [FONT=Ubuntu]ubuntu@ubuntu:~$ sudo lshw -c network[/FONT]
   [FONT=Ubuntu]*-network  [/FONT] 
   [FONT=Ubuntu]...              [/FONT] 
 [FONT=Ubuntu]driver=rtw_pci driverversion=5.0.0-23-generic[/FONT]
 
```
 
 **Driver - LOADED                 (WiFi NOT working)**
 ```

 admin-user@tiny-blue:~$ sudo lshw -c network
   *-network DISABLED   
    ...    
 [FONT=Ubuntu]broadcast=yes driver=rtw_pci driverversion=5.4.0-42-generic[/FONT]
 
```
 
 [FONT=Ubuntu]
So[/FONT][FONT=Ubuntu], [/FONT][FONT=Ubuntu]I'm thinking[/FONT][FONT=Ubuntu], if drivers ARE the same, can I[/FONT][FONT=Ubuntu] regain WiFi by[/FONT][FONT=Ubuntu] just[/FONT][FONT=Ubuntu] rolling back to a previous kernel [/FONT][FONT=Ubuntu](if that's [/FONT][FONT=Ubuntu]even [/FONT][FONT=Ubuntu]possible[/FONT][FONT=Ubuntu] -- I am reading that [/FONT][FONT=Ubuntu]this [/FONT][FONT=Ubuntu]may be [/FONT][FONT=Ubuntu]more difficult with 18.04[/FONT][FONT=Ubuntu] than with 16.04[/FONT][FONT=Ubuntu])[/FONT][FONT=Ubuntu]? [/FONT] 
 
 [FONT=Ubuntu]And,[/FONT][FONT=Ubuntu] if the L[/FONT][FONT=Ubuntu]IVE [/FONT][FONT=Ubuntu]version driver[/FONT][FONT=Ubuntu] IS different[/FONT][FONT=Ubuntu], c[/FONT][FONT=Ubuntu]an [/FONT][FONT=Ubuntu]I roll that back also?[/FONT]
 
 [FONT=Ubuntu]I don't know if I'm on the right track here[/FONT][FONT=Ubuntu]. Also I[/FONT][FONT=Ubuntu] am only a basic command line user. [/FONT][FONT=Ubuntu]An opinion and s[/FONT][FONT=Ubuntu]ome guidance would be greatly appreciated.[/FONT]
 
 [FONT=Ubuntu]Remember that the machine has no internet capabilities at the moment[/FONT][FONT=Ubuntu] -- [/FONT][FONT=Ubuntu]which would[/FONT][FONT=Ubuntu]n't[/FONT][FONT=Ubuntu] seem [/FONT][FONT=Ubuntu]to be[/FONT][FONT=Ubuntu] a problem since (apparently) I already have whatever [/FONT][FONT=Ubuntu]is needed[/FONT][FONT=Ubuntu] to make a working[/FONT][FONT=Ubuntu] WiFi[/FONT][FONT=Ubuntu] system![/FONT]
 
 [FONT=Ubuntu]Also[/FONT][FONT=Ubuntu] wondering,[/FONT][FONT=Ubuntu] if rolling back [/FONT][FONT=Ubuntu]does solve[/FONT][FONT=Ubuntu] this problem, will the problem just reappear again at every new system update?[/FONT]
 
 [FONT=Ubuntu]T[/FONT][FONT=Ubuntu]hanks![/FONT]

---

### Post by chili555 on 2020-08-10
> The same driver appears to be used either way, but I'm not sure about that (is "driverversion=5.0.0-23-generic" really a different driver from "driverversion=5.4.0-42-generic"?):

Quite possibly it has been updated in four kernel versions.

> *-network DISABLED   

This is likely the real problem; why is it 'DISABLED'? At first, it appeared to be Airplane Mode but that is evidently not the case.

> Frankly, I am unclear about my exact driver designation (is it only "rtw_pci" or something else more precise?).

The exact name of the driver is, indeed, rtwpci. Learn more:

```
modinfo rtwpci
```

When significant events occur, they are recorded by the system in a message log. You can (but please don't) read the log with:

```
dmesg
```

It is much more productive to read the message log and only see lines related to your problem, instead of sorting through the hundreds of lines in the entire log. Therefore, I suggest that we look at lines about the driver, rtwpci and the interface, wlo1.

```
dmesg | grep -e rtw -e wlo
```

As a bit of a hunch, let's also look at:

```
cat /etc/netplan/*.yaml
```

Once we see what the system says here, we'll be in a better position to offer a solution.

---

### Post by ishmael3 on 2020-08-10
Hi, chili55,
 
 Thank you for suggested ways to proceed -- and for the brief explanations of the commands! Here are the results:
 
 **modinfo rtwpci**
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ modinfo rtwpci[/FONT]
 [FONT=Ubuntu]filename:       /lib/modules/5.4.0-42-generic/kernel/drivers/net/wireless/realtek/rtw88/rtwpci.ko[/FONT]
 [FONT=Ubuntu]license:        Dual BSD/GPL[/FONT]
 [FONT=Ubuntu]description:    Realtek 802.11ac wireless PCI driver[/FONT]
 [FONT=Ubuntu]author:         Realtek Corporation[/FONT]
 [FONT=Ubuntu]srcversion:     69885917D4A4AF9C677E63B[/FONT]
 [FONT=Ubuntu]alias:          pci:v000010ECd0000D723sv*sd*bc*sc*i*[/FONT]
 [FONT=Ubuntu]alias:          pci:v000010ECd0000C822sv*sd*bc*sc*i*[/FONT]
 [FONT=Ubuntu]alias:          pci:v000010ECd0000B822sv*sd*bc*sc*i*[/FONT]
 [FONT=Ubuntu]depends:        mac80211,rtw88[/FONT]
 [FONT=Ubuntu]retpoline:      Y[/FONT]
 [FONT=Ubuntu]intree:         Y[/FONT]
 [FONT=Ubuntu]name:           rtwpci[/FONT]
 [FONT=Ubuntu]vermagic:       5.4.0-42-generic SMP mod_unload [/FONT] 
 [FONT=Ubuntu]signat:         PKCS#7[/FONT]
 [FONT=Ubuntu]signer:         [/FONT] 
 [FONT=Ubuntu]sig_key:        [/FONT] 
 [FONT=Ubuntu]sig_hashalgo:   md4[/FONT]
 [FONT=Ubuntu]parm:           disable_msi:Set Y to disable MSI interrupt support (bool)[/FONT]
 
```
 
 **dmesg | grep -e rtw -e wlo**
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ dmesg | grep -e rtw -e wlo[/FONT]
 [FONT=Ubuntu][    5.500074] rtw_pci 0000:01:00.0: Direct firmware load for rtw88/rtw8822c_wow_fw.bin failed with error -2[/FONT]
 [FONT=Ubuntu][    5.500084] rtw_pci 0000:01:00.0: failed to request firmware[/FONT]
 [FONT=Ubuntu][    5.513163] rtw_pci 0000:01:00.0: Firmware version 5.0.0, H2C version 14[/FONT]
 [FONT=Ubuntu][    6.113068] rtw_pci 0000:01:00.0 wlo1: renamed from wlan0[/FONT]
 [FONT=Ubuntu][    8.583610] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][    8.645707] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][    8.647650] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   19.010460] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   19.012005] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   29.022288] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   29.023779] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   39.018813] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   39.020445] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   49.027984] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   49.029963] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   59.022940] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][   59.024410] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2077.334445] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2077.367562] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2077.369449] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2088.020988] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2088.022507] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2098.028843] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2098.030267] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2108.020962] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2108.022581] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2118.019447] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2118.020991] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2128.021268] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 2128.023020] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3346.428408] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3346.457498] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3346.459041] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3357.024103] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3357.026899] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3367.029105] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3367.031842] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3377.019029] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3377.020518] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3387.021965] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3387.023547] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3397.024154] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 [FONT=Ubuntu][ 3397.025959] rtw_pci 0000:01:00.0: failed to wait firmware completion[/FONT]
 
```
 
 I can't interpret all that, but I Googled "[FONT=Ubuntu]failed to wait firmware completion" and found a lot of very recent hits that seemed to have Realtek-driver-issue written all over them![/FONT]
 
 **cat /etc/netplan/*.yaml**
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ cat /etc/netplan/*.yaml[/FONT]
 [FONT=Ubuntu]# Let NetworkManager manage all devices on this system[/FONT]
 [FONT=Ubuntu]network:[/FONT]
   [FONT=Ubuntu]version: 2[/FONT]
   [FONT=Ubuntu]renderer: NetworkManager[/FONT]
 
```
 
 I won't try to guess the next step. I'll wait to hear what you think. Thanks much for the help.

---

### Post by chili555 on 2020-08-11
> Direct firmware load for rtw88/rtw8822c_wow_fw.bin failed with error -2Does the firmware file exist on your system?

```
sudo updatedb
locate rtw8822c_wow_fw.bin
```If you find it, ideally in /usr/lib/firmware, check its size and permissions:

```
ls -al /usr/lib/firmware/rtw88/rtw8822c_wow_fw.bin
```Ideally, you'll see:

```
-rwxr-xr-x 1 root root 138720 Jul 15 09:11 /usr/lib/firmware/rtw88/rtw8822c_wow_fw.bin
```If you do *NOT* find it, let's see what version of linux-firmware is insrtalled:

```
sudo dpkg -s linux-firmware | grep Version
```We hope it is 1.187.2. If it is not 1.187.2, then:

```
wget [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.187.2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.187.2_all.deb)
sudo dpkg -i linux-firmware*.deb

```
Reboot and show us again:

```
dmesg | grep -e rtw -e wlo
```

> Thank you for suggested ways to proceed -- and for the brief explanations of the commands! I am always happy to explain as we go along to those new Ubuntians who are curious and intrepid. Sadly, a great many posters here just want the simple command to spring the wifi to life.

----------

Reference: [https://askubuntu.com/questions/1262009/lost-my-wifi-connection-after-running-last-ubuntu-update/1262183#1262183](https://askubuntu.com/questions/1262009/lost-my-wifi-connection-after-running-last-ubuntu-update/1262183#1262183)

---

### Post by ishmael3 on 2020-08-11
chili555,
 
 Thanks again for the help. I am looking forward to going through those commands and learning what's going on. Looks interesting. Unfortunately today is looking kind of crazy for me so it will likely have to wait for tomorrow. (I see a "wget" command in there... remember, my machine is a bit limited in internet access at the moment.)
 
 Cheers

---

### Post by chili555 on 2020-08-11
> I see a "wget" command in there... remember, my machine is a bit limited in internet access at the moment.You can always download it from some other computer and transfer it on a USB key.

---

### Post by ishmael3 on 2020-08-12
Greetings,

Thanks, again. Here's that info -- as much as was available.
 > 
 [COLOR=#000000] Direct firmware load for rtw88/rtw8822c_wow_fw.bin failed with error -2[/COLOR]
 [COLOR=#000000] Does the firmware file exist on your system?[/COLOR]
 
 [COLOR=#000000]**locate rtw8822c_wow_fw.bin**[/COLOR]
 
 [COLOR=#000000]No hits for that full string, so apparently it does not exist. However, if it means anything, very similar ones does esist:[/COLOR]
 
 [COLOR=#000000]**locate rtw88**[/COLOR]
 ```

  [COLOR=#000000]admin01@tiny-blue:~$ locate rtw88[/COLOR]
  [COLOR=#000000]/lib/firmware/rtw88[/COLOR]
  [COLOR=#000000]/lib/firmware/rtw88/rtw8822b_fw.bin[/COLOR]
  [COLOR=#000000]/lib/firmware/rtw88/rtw8822c_fw.bin[/COLOR]
  [COLOR=#000000]...[/COLOR]
  [COLOR=#000000](long list continues)[/COLOR]
 
```
 
> 
  If you find it, ideally in /usr/lib/firmware, check its size and permissions:

 As noted, the file didn't exist. And it seems there is no "/usr/lib/firmware" directory, only "/lib/firmware."
 > 
   If you do NOT find it, let's see what version of linux-firmware is insrtalled:
 
 **sudo updatedb**
 
 Nothing returned for that command.
 
 [FONT=Ubuntu]**sudo dpkg -s linux-firmware | grep Version**[/FONT]
 
 ```

 [FONT=Ubuntu]admin01@tiny-blue:~$ sudo dpkg -s linux-firmware | grep Version[/FONT]
 [FONT=Ubuntu]Version: 1.173.9  [/FONT] 
 
```
 
 [FONT=Ubuntu]So... that's a lot of negative results! It's sounding to me like I need to update firmware -- or rather install *new* firmware -- which seems to be available [here]("http://anduin.linuxfromscratch.org/sources/linux-firmware/rtw88/") .[/FONT]
 
 [FONT=Ubuntu]I will be looking into how to do that via a USB rather than a direct internet connection. [/FONT] 
 [FONT=Ubuntu]Also looking into rolling back the kernel, which sounds like a temporary fix -- maybe a reasonable solution unti Linux restores firmware that made previous kernal work. [/FONT] 
 
 [FONT=Ubuntu]I'm not sure whether, after installing new firmware, a new kernel update would just wipe out any additional driver additions (?).[/FONT]
 
 [FONT=Ubuntu]I'm just starting to learn about the distinctions between "kernels" and "firmware."  I am understanding that they are updated together with any new kernel. It's seeming to me that the most recent kernel just mistakenly was missing a driver that had been previously included, so hoping that will be corrected in upcoming updates. [/FONT] 
 
 [FONT=Ubuntu]Thanks again for any guidance offered. (I am not loosing interest in this project -- really appreciate the help -- but am expecting life to be hectic for a time so a response could be slow.) 

Thanks!
[/FONT]

---

### Post by chili555 on 2020-08-12
> It's sounding to me like I need to update firmware -- or rather install new firmware -- which seems to be available here .
I will be looking into how to do that via a USB rather than a direct internet connection.

Download it on some other computer; simply click here:

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.187.2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.187.2_all.deb)

Drag and drop it to a USB key. Insert the USB key into the Ubuntu computer. Drag and drop it from the USB key to the desktop of the Ubuntu computer. Install it from the terminal:

```
cd ~/Desktop
sudo dpkg -i linux-firmware*.deb

```
Reboot.

> I'm not sure whether, after installing new firmware, a new kernel update would just wipe out any additional driver additions (?).

Very, very unlikely, but in the one in a million chance it does, simply select the earlier kernel version at the GRUB menu and boot into it. [https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time) Then we'll sort it out and file a bug report.

> I'm just starting to learn about the distinctions between "kernels" and "firmware." I am understanding that they are updated together with any new kernel. It's seeming to me that the most recent kernel just mistakenly was missing a driver that had been previously included, so hoping that will be corrected in upcoming updates.

Doubtful. I suspect that, for some reason, the firmware package didn't get updated from 1.173.9 to 1.187.2 when you upgraded to Ubuntu 20.04. We're doing that now. Typically, firmware is updated only by additions, not deletions.

> Also looking into rolling back the kernel, which sounds like a temporary fix -- maybe a reasonable solution unti Linux restores firmware that made previous kernal work.

I doubt this will be needed.

---

### Post by ishmael3 on 2020-08-14
chili555, many thanks for your help and patience. I followed your last instruction for installing "linux-firmware_1.187.2_all.deb". WiFi is restored. And, after initial restart, a lengthy update, and another restart all continues working. (I will mark thread "solved" when I figure out how!)
 
 A few observations from the process that were interesting, and might be useful to someone working through a similar issue:
 
 At  first, after installing the new firmware, I thought the process had failed because "**locate rtw8822c_wow_fw.bin**" still returned nothing. Then I was really puzzled when (using GUI nautilus) I simply looked into "/lib/firmware/rtw88" and there the file was! (It had NOT been there before installing the new firmware BTW.) It just couldn't be seen by "**locate**."Out of curiosity I ran the following:  
 
  **ls /lib/firmware/rtw88**
 ```

 admin01@tiny-blue:~$ ls /lib/firmware/rtw88
 README  rtw8723d_fw.bin  rtw8822b_fw.bin  rtw8822c_fw.bin  **rtw8822c_wow_fw.bin**
 
```
 The file DOES show up listed as part of that directory, but, in the command terminal, that file alone is highlighted in green, showing it must be special for some reason!
 
 The "README" file was also not there before the new firmware. Here is what that file says:
 
 **README**
 ```

 [FONT=Ubuntu]rtw88 firmware[/FONT]
 [FONT=Ubuntu]================[/FONT]
 
  [FONT=Ubuntu]This repository contains firmware images supported by Realtek's wireless[/FONT]
 [FONT=Ubuntu]driver rtw88. And some of the devices run with more than one firmware[/FONT]
 [FONT=Ubuntu]file. Basically, a "normal" firmware is necessary to be downloaded to[/FONT]
 [FONT=Ubuntu]the device.[/FONT]
 [FONT=Ubuntu]And another is called "wowlan" firmware, it should be loaded when a[/FONT]
 [FONT=Ubuntu]device is going to suspend. Which means driver will "re-download/swap"[/FONT]
 [FONT=Ubuntu]the firmware image. The wowlan firmware contains wake up functions that[/FONT]
 [FONT=Ubuntu]can recognize specific events and send a wake up signal to device if[/FONT]
 [FONT=Ubuntu]needed, and the system will resume to running state. During resume,[/FONT]
 [FONT=Ubuntu]driver will then swap the normal firmware back, return to running state.[/FONT]
 
  [FONT=Ubuntu]If any distros or platforms do not require wowlan feature, they can[/FONT]
 [FONT=Ubuntu]_only_ pick the normal firmware. And everything still works fine,[/FONT]
 [FONT=Ubuntu]except that the device cannot be waken from the wireless NICs.[/FONT]
  
 [FONT=Ubuntu]Currently supported devices with corresponding firmwares:[/FONT]
  
 [FONT=Ubuntu]RTL8822BE[/FONT]
     [FONT=Ubuntu]rtw8822b_fw.bin[/FONT]
  
 [FONT=Ubuntu]RTL8822CE[/FONT]
     [FONT=Ubuntu]rtw8822c_fw.bin[/FONT]
     [FONT=Ubuntu]rtw8822c_wow_fw.bin[/FONT]
 
```
  [FONT=Ubuntu]Wikipedia has a long article on "[/FONT]Wake-on-LAN." I am not sure of the significance of the [FONT=Ubuntu]**rtw8822c_wow_fw.bin** file to my original problem. That file was not present while running Ubuntu from a live USB drive, and WiFi was working. Also, the file  **rtw8723d_fw.bin** was added to the "/lib/firmware/rtw88" directory with the new firmware.[/FONT]
 
 [FONT=Ubuntu]I am the first to admit that I don't understand exactly what caused, or what cured my WiFi problem. But, installing the new firmware DID fix it. [/FONT] 
 
 [FONT=Ubuntu]I have one follow-up for chili555 if you're still with me: How did you know that my existing  firmware version was not correct, and how did you then determine what new firmware version I should Install? Was it just the latest available for 18.04... or linked to kernel version... or something else?[/FONT]
 
 [FONT=Ubuntu]Thanks for all the help![/FONT]

---

### Post by chili555 on 2020-08-14
> At first, after installing the new firmware, I thought the process had failed because "locate rtw8822c_wow_fw.bin" still returned nothing. The utility 'locate' scans an index that you must create, although I suspect that the system updates the index at some period automagically, but it is not instant. When you make new changes, it is not instantly present in the old index. [https://linux.die.net/man/1/locate](https://linux.die.net/man/1/locate)

To force a rebuild of the index, do:

```
sudo updatedb
```It takes a few moments, please be patient.

Now try again:

```
locate rtw8822c_wow_fw.bin
```

Now it appears.

> How did you know that my existing firmware version was not correct, and how did you then determine what new firmware version I should Install? Was it just the latest available for 18.04... or linked to kernel version... or something else?
I knew because a useful diagnostic technique is to check the message log for warnings, errors, etc. about your driver. It clearly said it wanted the firmware chunk and, when you searched for it, it wasn't present. When I searched my own system for it, it was present. I therefore recommended that you install linux-firmware 1.187.2, the same as on my system.

BOOM! Your wireless works and Chili's a genius!!

---


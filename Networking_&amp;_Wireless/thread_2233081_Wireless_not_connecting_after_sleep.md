---
title: "Wireless not connecting after sleep"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by asearle on 2014-07-06
Hi Everyone,

I have Ubuntu 14.04 running wireless and connecting fine after an initial boot.

However, if I go into sleep mode and then try to connect, the available networks are visible and the system tries to connect to the last valid connection but then simply times out without connecting.  In order to be able to re-connect I need to re-boot ... which is a absolute pain!

Some time ago I had a problem where wireless was not available after sleep and solved it with this command ...

nmcli nm sleep false

But this time wireless is available (command returns "already awake") so the problem must be something different.

I thought I might be my wireless router but I have tried it in other locations and the problem remains the same.

If anyone can help me diagnose this, then I would be most grateful.

Many thanks,
Alan Searle

Cologne, Germany

---

### Post by kc1di on 2014-07-06
what wireless card and driver are  you using?
please post the output of the following command:
```
lspci 
```

---

### Post by asearle on 2014-07-06
Below is the output from lpci.

Any tips would be most gratefully received.

Many thanks,
Alan

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7400G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
```

---

### Post by varunendra on 2014-07-06
Please open a terminal (Ctrl-Alt-T) and run the following command to create a configuration file -
```
echo 'SUSPEND_MODULES="$SUSPEND_MODULES ath9k"' | sudo tee /etc/pm/config.d/modules
```
Note that there is a double-quote mark (") immediately followed by a single-quote mark (') after "ath9k". Better copy-paste the entire line to avoid typing mistakes.

This will create a file 'modules' in /etc/pm/config.d directory, containing a single line -
```
SUSPEND_MODULES="$SUSPEND_MODULES ath9k"
```
It is supposed to remove the driver 'ath9k' before going to suspend, and reload it as soon as it returns from suspend. Some modules need to be reloaded to work properly after a suspend - resume cycle.

If this doesn't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by asearle on 2014-08-10
Hallo Varan,

Many thanks for the tip (creating the "modules" file) but unfortunately I still have the problem:

1. Wireless connects fine when I first boot
2. After a suspend (all suspends) wireless is still active and all sources are visible
3. Wireless tries to connect to the source of my last successful connection (repeatedly) but fails to connect.
4. After a reboot the connection is successful again

This is driving my so much arround the bend that I am mostly using a wired connection now  :-(

Is this maybe a known problem with my laptop (which has given me lots of headaches), a Samsung Series5?

I installed the tracking tool that you suggested (output below) so it would be a great help if you (or comeone) could take a look.

Many thanks,
Alan Searle

[ATTACH]255375[/ATTACH]

---

### Post by varunendra on 2014-08-11
Hello asearle,

I can see a few 'usual' settings that are sometimes problematic.

First, something I'm just curious about - Do you really get _good_ speeds when the wifi is working? I'd be surprised if you get above 54 Mb/s, because your router is using TKIP encryption algorithm which theoretically limits the traffic speed to 54 Mbps.

So regardless of the negotiated connection speed (which appears to be 115.6 Mbps in the report), I doubt if you can go above 54 Mbps transfer speed. Can you do a test on speedtest.org and report back the results?

Now, skipping a couple of usually 'obvious' suggestions, I want you to try an experimental solution seeing the nature of your problem and comparing it with a recently solved thread. Please try the script suggested in this post and let us know if it solves your problem too - [http://ubuntuforums.org/showpost.php?p=13084268](http://ubuntuforums.org/showpost.php?p=13084268)

If not, we'll try a few other 'usual' things which could possibly help. The above script tries to disable the "network-manager" service while going to sleep/hibernate, and resume it at wake-up/resume. If your problem is the same - that is, network manager failing to suspend/resume properly - the above solution should work.

Please try, and report back the result.

**PS:**
I personally don't think it can be anything specific to Samsung or any particular model of it (unless it is happens with Windows too, which these machines are specifically designed for).

---

### Post by asearle on 2014-08-17
Hi Everyone,

I finally fixed the problem using the solution suggested by "Shrodi" here ...

[http://ubuntuforums.org/showthread.php?t=2218043](http://ubuntuforums.org/showthread.php?t=2218043)

Scroll down to find his solution which involves creating this file ...

/etc/pm/sleep.d/wakenet.sh

Many thanks to all who posted on this subject!

Regards,
Alan

---

### Post by varunendra on 2014-08-17
> **asearle said:**
> I finally fixed the problem using the solution suggested by "Shrodi" here ...

[http://ubuntuforums.org/showthread.php?t=2218043](http://ubuntuforums.org/showthread.php?t=2218043)

Thanks for the feedback and sharing the solution with us Alan! :)

I believe it is just a confirmation of the "ifdown/up wlan0" solution mentioned here : [http://ubuntuforums.org/showpost.php?p=13099409](http://ubuntuforums.org/showpost.php?p=13099409) , which seems to be a better approach than killing a process _after_ wake up.

---


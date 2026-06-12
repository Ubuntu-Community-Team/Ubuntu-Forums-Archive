---
title: "Wifi not working out of the box in jammy jellyfish"
date: 2022-05-03
forum: Networking &amp; Wireless
---

### Post by aleph04 on 2022-05-03
I had this problem with 20.04 as well...after it upgraded to the 5.13 kernel, my wifi went out. Looks like it's gonna be the same thing for jammy jellyfish. I'm wondering, is there any way to fix this? I can ping localhost, that works but nothing else shows up. Here's a pastebin with that script:


[https://pastebin.com/veC2XM1L](https://pastebin.com/veC2XM1L)

---

### Post by chili555 on 2022-05-05
Is this a dual boot with Windows? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

May we see: ```
sudo dmesg | grep iwl
```

Thanks.

---

### Post by aleph04 on 2022-05-05
[https://pastebin.com/iY2ysy6n](https://pastebin.com/iY2ysy6n)

---

### Post by chili555 on 2022-05-05
> iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.Is your firmware file corrupted?

```
 ls -al /usr/lib/firmware/iwlwifi-QuZ-a0-jf-b0-71.ucode
```We hope the size is 1285188.

I am very suspicious about:

```
[    4.787130] iwlwifi 0000:00:14.3: Hardware error detected. Restarting.
```And that you said:>  after it upgraded to the 5.13 kernel, my wifi went out.I wonder if it is actually a hardware failure.

---

### Post by aleph04 on 2022-05-06
Ok, I ran 
 ls -al /usr/lib/firmware/iwlwifi-QuZ-a0-jf-b0-71.ucode```

[FONT=monospace][COLOR=#000000]-rw-r--r-- 1 root root 1285188 Mar 29 02:17 /usr/lib/firmware/iwlwifi-QuZ-a0-jf-b0-71.ucode

```
[/COLOR]
I ended up switching to kubuntu.... STILL can't get my wifi to work for nothing. Oh, I can ping localhost... and it returns [packets, so my hardware isn't failing. I dunno what to do.[/FONT]

---

### Post by aleph04 on 2022-05-06
Here's what needs to happen more than likely... I need to downgrade the kernel to 5.11. But I can't seem to get that to happen in Kubuntu. I hope I can get help here, because the kubuntu forums are absolutely dead. Right now I'm using USB tethering to connect to the internet and it's driving me crazy.

---

### Post by chili555 on 2022-05-06
> I can ping localhost... and it returns [packets, so my hardware isn't failing. If you are doing:```
ping -c3 localhost
```Or else:
```
ping -c3 127.0.0.1
```Then that has nothing at all to do with your Intel wireless hardware and certainly doesn't rule out failure of said Intel wireless hardware.

Sorry.

---

### Post by aleph04 on 2022-05-06
[FONT=monospace][COLOR=#000000]PING localhost (127.0.0.1) 56(84) bytes of data.[/COLOR]
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.034 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.036 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2039ms
rtt min/avg/max/mdev = 0.034/0.036/0.039/0.002 ms

How do you transmit packets without a wireless card? I was always of the opinion that if you could ping localhost, it indicated that your hardware was fine. But, I was able to get it working in 20.04 (It randomly just went out and I found out it definitely is the kernel... when I changed it to kernel 5.11, my wireless worked just fine. It's the kernel, it has to be incompatible with [/FONT][FONT=monospace][COLOR=#000000]Intel 6 AX201. I'm gonna try to get some drivers for it. If I could get the linux kernel 5.11 in kubuntu 22.04, I'd be in business. Can you help me with that?[/COLOR]
[/FONT]

---

### Post by aleph04 on 2022-05-07
Ok, here was my solution: 

[https://askubuntu.com/questions/1352653/intel-ax201-wi-fi-6-is-not-working-on-ubuntu-21-04](https://askubuntu.com/questions/1352653/intel-ax201-wi-fi-6-is-not-working-on-ubuntu-21-04)

You'll have tot edit some of the numbers around potentially. Then I used Ubuntu Mainline to download the 5.11 kernel, and grub-customizer to make that the default kernel to boot to.. Voila, fixed. Thanks for your help.

---

### Post by Skaperen on 2022-05-07
[FONT=monospace]> I was always of the opinion that if you could ping localhost, it indicated that your hardware was fine.[/FONT]

no.  success pinging localhost means that you local OS network stack is working.  that does not involve any hardware to go outside of that machine.  it means most of your CPU is fine.  it means much of your RAM is fine.  it means nothing about your wifi or the driver for the wifi.

if your wifi interface does not show up, then the initialization code in the driver failed.  the driver may have been "upgraded" in a way that did not account for your specific hardware (which the manufacturer may no longer be making and new drivers from them would no longer support).

tell us more about your hardware.  go into much detail for the network stuff.  is this a PC with plug-in cards?  is this a laptop?

can you use USB?  do you have a spare USB storage device big enough to install Kubuntu or Xubuntu on?  you could install an older system on a spare drive to have a way to test hardware and a copy of an older kernel in installed form.  can your BIOS boot from USB storage?

---


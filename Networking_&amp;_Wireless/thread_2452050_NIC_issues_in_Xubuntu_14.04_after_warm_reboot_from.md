---
title: "NIC issues in Xubuntu 14.04 after warm reboot from Windows - Dual boot"
date: 2020-10-15
forum: Networking &amp; Wireless
---

### Post by Monkadelicd on 2020-10-15
I've got a Dell Precision T5810 that is dual booting Windows 10 and Xubuntu 14.04. I know 14.04 is EOL but some software requires 14.04 still *cough* medical software *cough*. Xubuntu is the default option in Grub so when rebooting from Windows 10 the PC will reboot to Xubuntu. When this happens the NIC cannot communicate out the NIC port. If the PC is shutdown from Windows 10 and started backup into Xubuntu the NIC has no problems. Dell is hesitant to support anything related to Xubuntu since the workstation shipped with Windows 7.

I do see dhcpd sending out broadcast packets to get an IP but nothing is seen on the dhcp server in my router. There are link lights and flashes indicating traffic on the switchport and the NIC port on the workstation. I can ping 127.0.0.1

Dell's pre-boot diagnostics will fail the NIC if I reboot from Windows 10 into Xubuntu 14.04 then reboot and go directly to the pre-boot diagnostics. If I reboot Windows 10 and enter pre-boot diagnostics the NIC passes.

There are not differences in lsmod or dmesg for the networking between reboots when the NIC works and when it doesn't.

This issue is specific to the Dell Precision T5810. We have deployed dozens of T7810s and T7820s without an issue.

I can provide any necessary info needed if anyone can point me in the right direction.

Thank you

---

### Post by CelticWarrior on 2020-10-15
1. [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)
This is what you need if you want to keep using 14.04. Xubuntu 14.04 with ESM has no security updates since 2017 (flavors have only 3 years support). Using an unpatched OS connected to the internet is dangerous and if dealing with "medical software" and patients' sensitive data is tremendously irresponsible and even illegal in most countries. 

2. Your problem very likely has to do with Windows Fast Startup. Disable it. Also update BIOS/UEFI.

---

### Post by Monkadelicd on 2020-10-15
I appreciate your concern but all of our systems are FDA approved as medical devices and none are directly connected to the internet. We have hardened any known security flaws found in monthly penetration tests. Until working for this company I didn't understand why so many medical devices are running out of date software. After learning the process required by the FDA to get approval for each and every software update, I have an appreciation for what our developers and QA team have to endure as well as the hurdles our administration have to climb as far as fees and paperwork. 

I have disabled fast startup in Windows, I have ensured that WoL is enabled in Windows and BIOS. BIOS is on most recent version and all drivers are up-to-date using Dell's SupportAssist application. I've also tested with Intel's newer drivers for the i217-lm NIC. The NIC isn't disabled as often the case when this problem occurs on dual boot systems. When Windows disables the NIC the activity lights typically do not light up.

---

### Post by Monkadelicd on 2020-10-20
Dell is going to send me another motherboard. The only way I can imagine that working is if it's a newer revision. I'll update this post with the results once I've received and installed the new mobo.

---

### Post by chili555 on 2020-10-20
Is Wake-on-LAN enabled in Windws? If so, I suspect that Windows has control of and will not release the NIC. Please check and adjust as needed.

---

### Post by Monkadelicd on 2020-10-22
chili555, I double checked since I've reinstalled Windows and that didn't help. I just got in the replacement motherboard from Dell. I'll see if that does any good (it's doubtful) and report back here.

---

### Post by Monkadelicd on 2020-10-29
I've finally got everything setup with the new motherboard and I'm still having the same luck. It seems that sporadically the NIC will work after a warm reboot from Windows 10 but only very seldomly. The strange thing is that going directly into the pre-boot diagnostics from Windows 10, the NIC passes, but if I reboot to Xubuntu first then reboot to the pre-boot diagnostics, the NIC fails. What could Linux be doing that would stop the NIC from functioning correctly?

I'm going to try upgrading Xubuntu 14.04 to 16.04 or 18.04 to see if the problem exists there as well.

---

### Post by Monkadelicd on 2020-10-30
No dice with newer LTS releases. Its something with the drivers/firmware. Maybe we can get Dell to work with us on a fix. We've had to get custom kernel modules for MegaRAID SAS controllers in the past.

---


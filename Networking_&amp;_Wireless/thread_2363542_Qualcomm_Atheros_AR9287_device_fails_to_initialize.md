---
title: "Qualcomm Atheros AR9287 device fails to initialize on boot - wireless not working"
date: 2017-06-11
forum: Networking &amp; Wireless
---

### Post by zinclozenge on 2017-06-11
Basically, what seems to be happening is that ubuntu tries to load the ath9k driver on boot but then something happens and it errors, as seen in dmesg. As such, there's no wireless functionality at all and I'm only able to use a wired connection. I've also tried the card in my windows machine where it works perfectly out of the box.

Here's the output of the diagnostic script [https://paste.ubuntu.com/24833923/](https://paste.ubuntu.com/24833923/)

---

### Post by Hadaka on 2017-06-11
Hi please open a terminal and do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
then do..
```
sudo modprobe -rf eeepc_wmi
echo "blacklist eeepc_wmi | sudo tee /etc/modprobe.d/blacklist-eeepc_wmi.conf
```
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
thanks.

---

### Post by zinclozenge on 2017-06-11
> **Hadaka said:**
> Hi please open a terminal and do..

I just ran all of that and I didn't notice a change, so I rebooted and still no change. I did notice this here in dmesg though

[    0.853038] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.853054] ACPI: Executed 2 blocks of module-level executable AML code
[    0.855169] ACPI Error: Needed [Integer/String/Buffer], found [Region] ffff9b6f3e0ebe10 (20160930/exresop-425)
[    0.855176] ACPI Exception: AE_AML_OPERAND_TYPE, Could not execute arguments for [IOB2] (Region) (20160930/nsinit-412)

Seems like it's common error on boot with AMD Ryzen and Asus Prime B350 motherboard as seen here [https://bugzilla.redhat.com/show_bug.cgi?id=1443680](https://bugzilla.redhat.com/show_bug.cgi?id=1443680)

---

### Post by Hadaka on 2017-06-11
Hi, let's restore what was blacklisted since it made no difference.
please do..
```
sudo rm -rf /etc/modprobe.d/blacklist-eeepc_wmi.conf
sudo modprobe eeepc_wmi
```
The dmsg showed a reference to Region,Please re-run this command again.
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
thanks.

---

### Post by zinclozenge on 2017-06-12
> **Hadaka said:**
> Hi, let's restore what was blacklisted since it made no difference.
please do..

Just ran the commands and nothing happened again.

---

### Post by zinclozenge on 2017-08-08
The solution to this was updating the BIOS. I have an Asus Prime B350-Plus with Ryzen 7, and updating the bios fixed the issue. The ath9k driver is now correctly loaded on boot and I can now connect to wireless networks no problem.

---


---
title: "bluetooth connection with Nokia E50"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by serek on 2007-07-05
Hi all,

I'm using currently Ubuntu 7.04 and I'm having problem to set up connection between my laptop and my Nokia phone.

I've followed [https://help.ubuntu.com/community/BluetoothSetup?highlight=%28CategoryBluetooth%29]("https://help.ubuntu.com/community/BluetoothSetup?highlight=%28CategoryBluetooth%29") to set up bluetooth usb dongle on my laptop. Now bluetooth itself is working fine..I can use mouse without any problems. ```
hidd --search
``` connects mouse automatically.

Now I'm trying to set up connection with my phone. ```
hcitool scan
``` can see my phone. When I'm choosing "New paired device" on my Nokia I can see <my hostname> in the list of all bluetooth hosts. Then I'm trying to pair phone with laptop.. so far everything looks perfect.. I'm getting passcode request.. standard '1234' on the beginning (later on I'll change it). In few seconds I can see "Pairing with <my hostname> complete".

Now I have <my hostname> on the list of paired devices. And that's the point where problem begins. While I'm trying to connect my phone to the laptop in few seconds I'm getting response "Unsupported device: <my hostname>" and connection fails. Anyone know any particular reason? Maybe I'm doing something incorrectly or I've missed something important?

I'll appreciate any help with that. Thanks in advance.

Regards,
Sergiusz

---

### Post by gregh on 2007-08-30
any joy with this? I get this exact issue with a Nokia E65 and Feisty (with all updates)
Can pair just fine, but when I try to connect "unsupported device" is the message I get displayed on my phone.

-Greg

---

### Post by kelnage on 2007-09-18
I'm having this problem with a Nokia E61 and a PCMCIA Bluetooth adapter, so any help would be welcome :)

---


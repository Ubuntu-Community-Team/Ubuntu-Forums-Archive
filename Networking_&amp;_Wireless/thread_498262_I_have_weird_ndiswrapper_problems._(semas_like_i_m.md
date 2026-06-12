---
title: "I have weird ndiswrapper problems. (semas like i ma the one) i need some help please."
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Makcum on 2007-07-11
I have really weird problem. i was trying to find some info here on the forum or somewhere in internet but i couldn't get the answer.

after installing  ndiswrapper software and after installing my inf file through this software i can see the mac address of my wlan0 as "00:00:00:00:00:00" and i get the message by dmesg "ndiswrapper (iw_set_ap_address:629): setting AP mac address failed (00010003)" twice it appeared with normal mac addres but not anymore. and then also i get the message like wlan0: link is not ready
i have tried to reinstall it many times, nothing works.

could anybody help me with my problem?
thanks.

my configuration:
Laptop Acer aspire 5052
Ubuntu 7.04 64bit
wlan0: AR5007EG - I am using windows XP 64 bit driver to install through ndiswrapper.

/etc/networks/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

allow-hotplug wlan0 (this parrameter i can delete. The same situation with it or without)
auto wlan0
iface wlan0 inet dhcp

---

### Post by Makcum on 2007-07-11
I have found that there is a problem with ACPI.
i managed to make it with MAC address a few times again. and i was able to connect to the wifi access point.

i have noticed that if it says "ACPI: PCI Interrupt for device 0000:02:00.0 disabled" then wifi doesnt work, but when it says "ACPI PCI interrupt 0000:02:00.0[A] -> GSI 16 (level, low) - IRQ 16"  then wifi works great.

any ideas here? what can i do with this ACPI that it always will work ok?

because those methods what i am trying to do to make my wifi work are not really good.

thnaks for help.

---

### Post by kevdog on 2007-07-11
Can you post your entire or include as attachment the output of dmesg.  Most likely a quick change to your grub script will prevent this error.

---

### Post by Makcum on 2007-07-11
I have found what was the problem.. well actually i have found how to solve the problem

If after booting i switch to console and type TWICE  "rmmod ndiswrapper" then everything starts working.

i have tried to add two lines to /etc/rc.local 

/sbin/rmmod ndiswrapper
/sbin/rmmod ndiswrapper

exit 0

but it didnt work on startup. I still have to switch to console and type twice  rmmod ndiswrapper

if anybody knows how to solve this problem because it is not fan for me to switch every start to console and type that mistaerious command.

thank you.

---

### Post by kevdog on 2007-07-11
Yea but if you remove the ndiswrapper module, then your internet will not most lkely work. To permanently remove the module
sudo modprobe -r ndiswrapper

---

### Post by Makcum on 2007-07-11
Yeah, but the thing is that if i type "rmmod ndiswrapper" module is still there and i have internet and averything. And aslo i dont understand why i have to type twice. if i type once nothing works, but if i type twice i can see the mac address of my wifi card. that's weird actually. i need to automatize this thing.

oops no. i think i lied a bit... i think internet doest work.

i am sorry one more time. Internet works defenitelly.. i have just cheked it up.

I will try to attach output of dmesg

---

### Post by Makcum on 2007-07-11
here is my dmesg.log

---


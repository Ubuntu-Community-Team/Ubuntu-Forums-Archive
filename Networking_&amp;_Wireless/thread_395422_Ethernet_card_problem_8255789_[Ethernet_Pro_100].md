---
title: "Ethernet card problem 82557/8/9 [Ethernet Pro 100]"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by wsantoso on 2007-03-28
Hi there,

I installed 6.10 on my gateway solo 5300 laptop. Installation went fine except that network is not working.

lspci shows 00:0d.0 Ethernet Controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)

However ifconfig only shows the loopback adater, no eth0.
Same thing in system\networking and system\network tools

So far, I have looked around and tried:

Tried adding noapic to the boot file, didn't help.

Interestingly commenting out the blacklist eepro100 in /etc/modprobe.d enabled me to see eth0, but it wouldn't talk to my router (dhcp).

The network card is an internal xircom card, kernel is 2.6.17-10-generic

Any advices welcome. I would hate having to reinstall windows on this laptop, which I would have to if network doesn't work. :(

Regards,
Willson

---

### Post by chili555 on 2007-03-28
I suggest putting the blacklist back as it was, then:```
sudo rmmod -f eepro100
sudo insmod e100
sudo dhclient eth0
```If it works, I would *sudo gedit /etc/modules* to add:```
alias eth0 e100
```Let us know.

---

### Post by wsantoso on 2007-03-28
Which directory should I run that in? It just says ERROR: Removing 'eepro100': No such file or directory

Thanks

---

### Post by chili555 on 2007-03-28
The commands insmod, modprobe and rmmod can get sleepy once in a while. After *sudo updatedb*, which takes a while, do *locate eepro100.* On my machine, I get:```
/lib/modules/2.6.17-10-generic/kernel/drivers/net/eepro100.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/net/eepro100.ko
```and some other stuff. So we know the module eepro100 exists!

The question is, is it inserted now. Please do *lsmod | grep 100* and we will see if eepro100 0r e100 is inserted. What you may have to do is the blacklist restoration and the /etc/modules change and reboot to get rid of eepro100, if it's there. After reboot, retry *sudo dhclient eth0*

---

### Post by wsantoso on 2007-03-28
lsmod | grep 100 now returns
e100 38020 0
mii 6912 1 e100

---

### Post by chili555 on 2007-03-28
Wonderful. I think we are closing in on it. What does *sudo dhclient eth0* return?

---

### Post by wsantoso on 2007-03-28
sudo dhclient eth0 returns

SI0CSIFADDR: No Such Device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

---

### Post by wsantoso on 2007-03-28
dmesg revealed that EEPROM was corrupted

e100: 0000:00:0d.0: e100_eeprom_load: EEPROM corrupted
e100: probe of 0000:00:0d.0 failed with error -11

Any idea?

---

### Post by chili555 on 2007-03-28
Well, e100 is making life difficult today! Or in Oz, tonight. First, this is a well-documented problem: [http://www.google.com/search?q=e100_eeprom_load%3A+EEPROM+corrupted&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=e100_eeprom_load%3A+EEPROM+corrupted&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

I suggest you try, first, *sudo gedit /etc/modules* to add the bold text:```
alias eth0 e100 **eeprom_bad_csum_allow=1**
```It will probably take a reboot to see if it worked. Check *dmesg | grep e100* and check to see if eth0 appears in ifconfig. If so, *sudo dhclient eth0* If all this works and you get an IP address and get on line, go no farther!

If...sigh...this does not kick eth0 to life, then I suggest changing the relevant section of /etc/modprobe.d/blacklist to:```
# replaced by e100
# but e100 doesn't work!
blacklist e100
```and then change the relevant section of /etc/modules to:```
alias eth0 eepro100
```Reboot. Does eth0 *then* show up in ifconfig and respond to *sudo dhclient eth0*?

---

### Post by Missionary Man on 2007-03-28
Hi,

I'm having pretty much the same problem here, but it's probably happened for a different reason. I had a working Ubuntu system running on a P2B-N motherboard that developed a fault on its IDE connector.

I removed the HD and installed it into an identical MB but now the eth0 will not show up. I get the same errors as identified by the original poster, apart from the bad eeprom csum error.

Is it possible that my installation is looking to work with the old MAC address and can't cope with a new one?

How do I remove/reinstall the module or driver to get it to recognise the LAN port?

Thanks,

Adam

---

### Post by chili555 on 2007-03-28
M-Man-
Very good thinking! You are on the way to linux geek-dom.

Take a look in /etc/iftab and you will see your interface, perhaps eth0, bound to a MAC address. Open up a terminal and *sudo gedit /etc/iftab* and remove the eth0 line altogether. Reboot and post back to tell the lurking newbies if you got it fixed.

---

### Post by wsantoso on 2007-03-29
alias eth0 e100 eeprom_bad_csum_allow=1 didn't help.
blacklisting e100 and switching back to eepro100 shows eth0 but failed at dhclient eth0.
No DHCPOFFERS received
No working leases in persistent database - sleeping

dmesg shows
[17179599.104000] eth0: Invalid EEPROM checksum 0x0000, check settings before activating this device!
[17179599.104000] eth0: 0000:00:0d.0, 00:00:00:00:00:00, IRQ 10.
[17179599.104000]   Receiver lock-up bug exists -- enabling work-around
[17179599.104000]   Board assembly 000000-000, Physical connectors present:
[17179599.104000]   General self-test: passed.
[17179599.104000]   Serial sub-system self-test: passed.
[17179599.104000]   Internal registers self-test: passed
[17179599.104000]   ROM checksum self-test: passed (0xdbd8681d).
[17179599.104000] ACPI: PCI Interrupt 0000:00:08.0 [A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

I'll try the links thanks and please do not hesitate if you have any other suggestions to fix this.

oh and ifconfig shows

eth0  Link encap: Ethernet HWaddr 00:00:00:00:00:00 
UP BROADCAST MULTICAST MTU:1500 Metric: 1
-----

---

### Post by Missionary Man on 2007-03-29
Chili, you are "the dog"!

Thanks for the very quick pointer, which was spot on.

Changing motherboards meant that my MAC address was different. This is stored in /etc/iftab.

I went to that file and deleted the MAC reference and rebooted. This sorted out all my problems and brought eth0 back up again. My server is now working fine. (Well, not exactly, but that's another story and another post ...)

Thanks again,

Adam
:guitar:

---

### Post by berlinbrown on 2007-03-31
I am having the same issue in the exact same way.  I just got to the last couple of posts so I will try that.  The mac address is also hardcoded.  So We will see what happens if I remove that.

I did most everything above, except that when I do sudo dhclient eth0, I get the following:

Listening on LPF/eth0/00:00:00 ...

DHCPREQUEST on eth0 to 255.255.255.255 port 67

...etc
...etc

Any ideas.  At one point, I did something to get it to work, now when I reboot I get what I posted above.

---


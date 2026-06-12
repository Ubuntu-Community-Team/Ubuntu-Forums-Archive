---
title: "WLAN w/o ndiswrapper or wpa_supplicant?"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by wedj3092 on 2006-11-29
Hi there.

I used to have 6.06 Dapper and using this help page [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28AES%29%7C%28uses%29%7C%28the%29%7C%28encryption%29%7C%28AES%29%7C%28type%2C%29%7C%28network%29%7C%28your%29%7C%28TKIP%29%7C%28replace%29%7C%28with%29#auto](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28AES%29%7C%28uses%29%7C%28the%29%7C%28encryption%29%7C%28AES%29%7C%28type%2C%29%7C%28network%29%7C%28your%29%7C%28TKIP%29%7C%28replace%29%7C%28with%29#auto)
I had a perfectly stable, auto-connecting wireless network with WPA. It just took me (relative noob) several minutes of playing aroung in /etc/network/interfaces. I never *knew* back then that there is something like WPA-supplicant or ndiswrapper. I made my interfaces look something like

auto ra0 
iface ra0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1
pre-up iwconfig ra0 essid " myssid "
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=7
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK=xxxxxx
pre-up iwpriv ra0 set TxRate=0

and everything worked perfectly.

Recently, I installed Kubuntu 6.10 Edgy from scratch, partitioning/deleting my old Dapper-installation (no upgrade). I immediately went for the interfaces file, making it look like the old one again, but to no avail. Firstly, my wireless PCI card is not designated by Edgy as ra0, but as wlan0/wmaster0 (tried both in interfaces). When doing sudo ifup ra0/wlan0, it says something about an invalid option. So I tried the iwpriv command, and (in Edgy!) it doesn't even have an option "set". So I dived back into the ubuntuforums and found that everybody is telling how to compile the original driver and/or how to implement WPA by using WPA-supplicant, but I did not need that with Dapper!
I also found different syntax in recent example interfaces, that did not use iwpriv/iwconfig, but looked more like

wireless-mode managed
wireless-essid Xxxxxx
wireless-key1 abcdef
adress 192.168.1.2
etc.

Now, can anyone tell me: Is it just the syntax or do I really have to compile the driver? Or use WPA-supplicant? And where can I find out about release-specific syntax??

I'm eager to learn, but right now I'm a bit lost... I'd appreciate any idea/piece of advice.

Adrian

---

### Post by FrodoB on 2006-11-29
Publish the output of lsusb or lspci, whichever is applicable please.

---

### Post by FrodoB on 2006-11-29
Publish the output of lsusb or lspci, whichever is applicable please.  

What is wrong with going back to Dapper, it is on LTS and will be supported until sometime in 2009?

---

### Post by wedj3092 on 2006-11-29
lspci -v | grep Network responded with

02:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI

this is good, because it means the driver is indeed included with Edgy, right?

about going back to Dapper: thought about that, too. I may eventually have to do it, but right now my ambition tells me to try and get wireless running (especially when the driver is included in Edgy) and not to give up just yet...

---

### Post by wedj3092 on 2006-11-29
I just read in another thread about installation from Alternate CD and Atheros devices that one has to 
sudo apt-get install linux-restricted-modules- 'uname -r'
but that's not related to my problem, is it? -- alright, forget about that.

two more things that may be helpful with helping me:

- could it have anything to do with IPV6 not being deactivated? (I read a lot about how it can cause problems)

- I get a ping respond from my loopback on 127.0.0.1 , but not from my router on 192.168.1.1

---

### Post by FrodoB on 2006-11-29
I think that I have seen several articles on this forum regarding the rt61 devices. Have you done a forum search for rt61?

The lspci message does not mean that it is included. It is however included I believe, but it may be defective and need replacing.

Like this article:

[http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

---

### Post by wedj3092 on 2006-11-29
Yes, I have read through the RT61-related articles/threads, but they all include downloading the original driver, which I'd like to avoid because I have no idea how implementing drivers works in linux and I fear it may be a source of further frustration. And also it seems unelegant to me, when I just had to edit the interfaces file in Dapper to get wireless network/internet. Do you or anyone know about that syntax thing I wrote in my initial message? What is the correct usage of iwpriv/iwconfig and did it change from Dapper to Edgy? Or, even better, where could I find out about the syntax/usage of iwpriv and other linux commands?

---

### Post by FrodoB on 2006-11-29
I don't believe there is supposed to be any difference. Have you looked in /etc/iftab to see if your device is tied to wlan0? If so remove that line and  reboot.

Dapper is sounding good to me.  After all Edgy will be long gone and Feisty Fawn may fix your problem in six months.

---


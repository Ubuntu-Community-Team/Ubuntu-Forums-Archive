---
title: "Ndiswrapper error (Not a valid driver .inf file.)"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by summersource on 2010-02-25
Thought I installed Ndiswrapper the other day. In a file search it was it was in my downloads and even simi fixed my ATI Graphics after the download.
 So last night I was double checking to make sure Ndiswrapper was installed  b/c have not been able to use my wireless for a week now, by which I am becoming extremely annoyed. I saw that it was not installed when I tried to install and I get the following error (Not a valid driver .inf file.)

---

### Post by mikeyphi on 2010-02-25
so - you're talking about wifi not graphics?
Which wifi card/chipset do you have?

---

### Post by summersource on 2010-02-25
AMD M880G Chipset

---

### Post by mikeyphi on 2010-02-25
> **summersource said:**
> AMD M880G Chipset

To determine what wireless card/chipset you have, open up a terminal and type the following.

lspci -v | less

Find the item re wireless and please post the result!

---

### Post by bkratz on 2010-02-25
> **summersource said:**
> AMD M880G Chipset

That number seems to be involved with video.

Input the following in the terminal
Applications>>Accessories>>Terminal

lspci | grep Wireless

(that is LSPCI in lowercase and W in uppercase)

What do you get now?

---

### Post by summersource on 2010-02-25
I have wireless atm just no telling how long it will stay up my graphics issues have to do with compiz fusion and AWN that I was trying to get working.
 Thank you for helping me 

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
        Subsystem: Acer Incorporated [ALI] Device 0293
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: cfd00000-cfefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f0300000-f03fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp



kerrie@kerrie:~$ lspci | grep Wireless
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
kerrie@kerrie:~$

---

### Post by redbook4574 on 2010-02-25
> **summersource said:**
> I have wireless atm just no telling how long it will stay up my graphics issues have to do with compiz fusion and AWN that I was trying to get working.
 Thank you for helping me 

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
        Subsystem: Acer Incorporated [ALI] Device 0293
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: cfd00000-cfefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f0300000-f03fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp



kerrie@kerrie:~$ lspci | grep Wireless
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
kerrie@kerrie:~$

I'm sure somebody will correct me if I'm wrong but I'm fairly sure the ath5k drivers work fine with that wifi adaptor, just un-install ndiswrapper and install ath5k and all should work.

---

### Post by mikeyphi on 2010-02-25
Sorry to say - not well supported.
Look here:

[http://sourceforge.net/search/?type_of_search=soft&words=Atheros+AR928X](http://sourceforge.net/search/?type_of_search=soft&words=Atheros+AR928X)

and bottom of this page:

[http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros)

---

### Post by bkratz on 2010-02-25
See this thread

start with post 5.

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

---

### Post by summersource on 2010-02-25
ok I downloaded madwifi do changes take place automatically or do I need to do anything?  Do I need ath5k also? Uninstalled NDISwrapper  (I think) . The reason I ask is because I have been having trouble installing/uninstalling and with downloads.

---

### Post by mikeyphi on 2010-02-25
> **summersource said:**
> ok I downloaded madwifi do changes take place automatically or do I need to do anything?  Do I need ath5k also? Uninstalled NDISwrapper  (I think) . The reason I ask is because I have been having trouble installing/uninstalling and with downloads.

Unfortunately you need to do something!!
Here follows an example of the code you need to use in a terminal:

sudo apt-get install build-essential
wget [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)
tar zxvf madwifi-ng-r2756-20071018.tar.gz
cd madwifi-ng-r2756-20071018
make clean
make
sudo make install
reboot

Line 1 is necessary software
Line 2 should be the website that has the driver you want to download
(if you already have it that's OK just navigate to where it's stored and execute line 3 onwards!)

---

### Post by redbook4574 on 2010-02-25
Also try loading backports and wireless backports I have heard they help with your card.

---


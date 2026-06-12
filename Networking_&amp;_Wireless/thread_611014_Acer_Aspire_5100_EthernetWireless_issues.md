---
title: "Acer Aspire 5100 Ethernet/Wireless issues"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by theluddite on 2007-11-12
Can somebody please help?  I can't use my wireless or ethernet internet connections.  In System>Administration>Network, only wired connections appear.  My USB connection works, but my ethernet connection does not.  I know the wireless card is functioning -- it worked with Windows.  I've tried ndiswrapper with two different drivers and I've installed madwifi-tools and bcm43xx-fwcutter to no avail.  I think I've tried just about every solution with the word "wireless" in it in this forum and nothing seems to work.

I'm running Gutsy Gibbon 7.10, and I have an Acer 5100, AMD64, 512MB DDR2 with an Atheros 802.11b/g wireless card and Realtek Semiconductors Ethernet card.

When I type ndiswrapper -l, I get this:
> bcmwl5 : driver installed
net5211 : invalid driver!

lspci is as follows:
[INDENT]> 00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/INDENT]

ifconfig -a returns this:

[INDENT]> eth0      Link encap:Ethernet  HWaddr 00:16:D4:CE:D4:F3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47480 (46.3 KB)  TX bytes:6220 (6.0 KB)
          Interrupt:21 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:0F:9F:8F:A3:51  
          inet addr:99.232.192.223  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:9fff:fe8f:a351/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:526122 (513.7 KB)  TX bytes:52536 (51.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:760 (760.0 b)  TX bytes:760 (760.0 b)
[/INDENT]

Maybe this is significant:  When I boot up, I get this message from dmesg:

[INDENT]> [   13.177743] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   13.177784] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   13.177822] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
[   13.177860] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   13.177897] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   13.177964] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[/INDENT]

I'm a complete neophyte so if you do have a good idea of what's wrong, please... explain it like I'm 5 years old.

---

### Post by beeper on 2007-11-13
I have the same hardware setup you do....Acer 5100 Atheros AR5006EG and AMD64.
When I used the 'Windows Wireless Drivers (ndiswrapper) Applet' , I got the wireless working. Lots of the features of the Network Manager don't work this way...but I can connect to my network. I used the same driver I already had working for WinXP_x64. I would say if you tried a 32bit Windows driver...then it would not match your CPU architechture and would fail. So make sure that the driver works for WinXP on your laptop or at least you've downloaded the right driver.

Be sure to uninstall the existing windows drive and then install you new x64 driver....

BTW - I don't use drivers for Vista....but I'm running WinXP Pro, Ultimate Vista, and Gutsy Gibbon on this laptop and I have the wireless connection working on all three OS's.

Good Luck
:)

---

### Post by theluddite on 2007-11-15
Thanks for the reply.  At least I know there's hope.  

What's the applet?  Is that just ndiswrapper?  Because, like I said, it's not working for me.  Which driver did you use, net5211?  What is your output of "ndiswrapper -|"?  Do you have a suggestion as to how to uninstall the old driver?  Otherwise, I'm going to just try blacklisting it.

Yeah, I didn't bother with a dual-boot on my laptop.  I've got vista on my desktop and that's enough for me.

---

### Post by danilofpires on 2008-01-02
One more.  :) Looks like we all get at the same point. After a lot of research and a few installations later I realized that "believe it or not" Ubuntu and PCLinuxOS are the most easiest distros to install the Atheros AR5007EG or AR5006EG. What you have to do is just get the acer_acpi module, unable the ath_pci and install the Windows driver by the ndiswapper tool. For me the XP32 driver version worked quite fine.

[I]Acer 5100-3357 MK38 2.2GHz, 2Gb DDR2.
Ubuntu Gusty. I saw a lot of comments with guys that worked with the 64bits version and had a lot of headaches. That's why I've been using the 32bits version.[/I]

The ACER_ACPI module.
>>For Ubuntu Feisty Fawn (7.04) (i386 and amd64) :  [COLOR="Navy"]deb [http://www.mumblyworld.info/ubuntu](http://www.mumblyworld.info/ubuntu) feisty[/COLOR] main
>> For Ubuntu Gutsy Gibbon (7.10) (i386 and amd64) : [COLOR="Navy"]deb [http://www.mumblyworld.info/ubuntu](http://www.mumblyworld.info/ubuntu) gutsy main[/COLOR]
>> To get the repository's key : [COLOR="Navy"]wget [http://www.mumblyworld.info/ubuntu/depot.key](http://www.mumblyworld.info/ubuntu/depot.key) -O- | sudo apt-key add - [/COLOR]

With deb package you just have to run the file, just like the "Other OS we can't pronounce the name".  :)

To see if everythig is fine type:

>> *dmesg | grep acer_acpi*

And you must see a message like that:
[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

Install the newer NDISWRAPPER version, pay attention to yor kernel version; If you are a newer to Linux you can also install the Visual Tool for ndiswrapper NDISGTK - I have to say that I don't like it at all, doesn't work for me), that's why I just install by the command line: ***ndiswrapper -i [path to your driver file/net5211.inf] ***

After that you can do a $ ***sudo ndiswapper -l*** and you will see the driver installed.

Enter you ***/etc/modprobe.d/blacklist*** and type the following line:
***blacklist ath_pci***

Enter the ***/etc/modules ***and add the lines
[I][B]ndiswapper
acer_acpi [/B][/I]( It may be already installed if you've done the installation by the deb package).

Do a reboot >> ***sudo init 6*** 

Everything must work quiet perfect.

---


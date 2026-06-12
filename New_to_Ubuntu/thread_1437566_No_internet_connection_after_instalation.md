---
title: "No internet connection after instalation"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Petr Hasek on 2010-03-24
Hallo, 
I just installed Ubuntu 9.10 on new and empty computer ASUS eee box 1501. Unfortunately the web connection (wired) failed (message like "wire has been disconeccted - you are offline now"). I tried to instal Ubuntu to an old PC and plug the wire in and it works normally.
Could someone advice what shall I check, set, change? So far, I checked only the cable, if it is pluged in properly. 
Note, I am absolutely Linux beginner. 
Thanks in advance. 
Petr

---

### Post by dineshs on 2010-03-24
Did you try this
right click on the network icon on the tray and ensure that the ENABLE NETWORKING option is ticked

---

### Post by 1991sudarshan on 2010-03-24
are you using ether net connection or PPPoE? if the answer if PPPoE the you have to the network setting and configure the connetion!

---

### Post by Petr Hasek on 2010-03-24
@ 1991surdarshan: I use the ethernet connection. 
@ dineshs: thanks, I'll check it when I am at home. Nevertheless, I installed the system from one boot CD to both PCs. It would be strange if networking is enabled on one of them and dissable on the second one. But anything is possible, maybe it depends on network card. 
Regards
Petr

---

### Post by undecim on 2010-03-24
If dineshs's solution doesn't work, open a terminal (Applications -> Accessories -> Terminal) and paste this command into it (use Ctrl+Shift+V instead of Ctrl+V if you like to use keyboard shortcuts)
```
lspci | grep Network
```
then post the output here.

---

### Post by mkvnmtr on 2010-03-24
Might be a good idea to check and then double check your wired connection and the adapters of the wire. Sometimes they do not seat well.

---

### Post by Petr Hasek on 2010-03-24
> **undecim said:**
> If dineshs's solution doesn't work, open a terminal (Applications -> Accessories -> Terminal) and paste this command into it (use Ctrl+Shift+V instead of Ctrl+V if you like to use keyboard shortcuts)
```
lspci | grep Network
```
then post the output here.
 
The output is 
```
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```
Will it help?
 
"Enable networking" option is ticked.

---

### Post by Petr Hasek on 2010-03-25
Does anybody have a hint? I consider claiming the computer but I would like to be sure it is defective before I ship it back to the seller.

---

### Post by dineshs on 2010-03-25
What about the lamp indication on the ethernet card and the device on the other end of the cable(modem/router/other PC).What is the device on the other end?Also I think you can post the output of
```
lspci
```

---

### Post by undecim on 2010-03-25
> **Petr Hasek said:**
> Does anybody have a hint? I consider claiming the computer but I would like to be sure it is defective before I ship it back to the seller.

I don't think that it is defective hardware (though I certainly wouldn't rule that out as a possibility.) In my experience, when ethernet cards fail, they usually just stop being recognized.

Try to connect again and then after getting the "wire has been disconeccted - you are offline now" message, go back to the terminal and post the output from
```
ifconfig
```

---

### Post by undecim on 2010-03-25
> **Petr Hasek said:**
> The output is 
```
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```
Will it help?
 
"Enable networking" option is ticked.

Sorry my mistake. The command should have been
```
lcpci | grep Ethernet
```

---

### Post by Petr Hasek on 2010-03-25
Thanks to all! I hope I foud a problem. 
 
Replys: 
# there is no LED on the back side of PC, indicating net connection.
# the device on the other end of the cable is "AirLive Ovislink WL-1120AP". It seems to work properly. 
# answer of terminal command lspci:
```
 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
 
Finaly, I checked the agreement with my internet provider and foud that the connection is bound to MAC address of PC. So I have to ask for access to net for my new PC. That also explains why the connection works on the old one only. Hopefully it will solve the problem. If so, I will mark the thread as "solved".

---

### Post by undecim on 2010-03-25
> **Petr Hasek said:**
> Thanks to all! I hope I foud a problem. 
 
Replys: 
# there is no LED on the back side of PC, indicating net connection.
# the device on the other end of the cable is "AirLive Ovislink WL-1120AP". It seems to work properly. 
...
Finaly, I checked the agreement with my internet provider and foud that the connection is bound to MAC address of PC. So I have to ask for access to net for my new PC. That also explains why the connection works on the old one only. Hopefully it will solve the problem. If so, I will mark the thread as "solved".

Depending on how the AirLive device functions, the MAC address may be irrelevant. Specificly, if it acts as a router, your ISP will only see the MAC address of your router, not your PC. To test this, you can look at the IP that Ubuntu has on your old working computer (by using the network applet). If it starts with 10. or 192., then the MAC address of your computers is irrelevant. Anything else, and its something worth looking into.

The fact that you don't see any LED showing network activity indicates a bad physical connection or a bad physical or data connection. So it could be a faulty card after all.

In short, it's either the MAC address, a bad connection, or a bad card.

---

### Post by Bobusa01 on 2010-03-25
I have the same problem no Internet after I Installed Ubuntu 9.10 It can see the MShome network. Connects through a router. Other Computers on the network have Internet and the OS is windows Xp on them. What do I need to get Internet

---

### Post by undecim on 2010-03-25
> **Bobusa01 said:**
> I have the same problem no Internet after I Installed Ubuntu 9.10 It can see the MShome network. Connects through a router. Other Computers on the network have Internet and the OS is windows Xp on them. What do I need to get Internet

You should create a new thread to get this problem answered. Make one and post a link here and I'll help you out.

---

### Post by Wingthor on 2010-03-25
Do you use DHCP?

---

### Post by Petr Hasek on 2010-03-29
It was as I wrote last time - I asked the internet provider for activation of the new MAC address and everyting works well now. 
Thanks to focus me on the oposite end of the wire...

---


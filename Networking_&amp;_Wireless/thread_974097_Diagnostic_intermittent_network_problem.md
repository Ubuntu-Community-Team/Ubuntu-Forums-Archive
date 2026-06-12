---
title: "Diagnostic intermittent network problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by wpault on 2008-11-07
Hi,

I'm having an intermittent failure on my network card / under heavy samba load. It seems to lock up and stop all network access until the network card / interface is reset through ifdown eth0 && ifup eth0.

Then it all starts working again. I have no idea why! I don't know if it's OS or the actual ethernet port on the motherboard. Nothing seems to get logged except for some DHCP requests (the machine is also my DHCP server) - perhaps this means that UDP is working ok, but TCP has stopped - and therefore not a hardware problem??? I don't know.

So is there a way of turning on more diagnostics / debugging to try and work out what's happening? Where else should I start?

For info my setup is Ubuntu 8.04 server with latest updates - kernel is 2.6.24-21

lspci output
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

The relevant samba log shows:
[2008/11/07 12:15:02, 1] smbd/service.c:make_connection_snum(1033)   office1 (192.168.2.100) connect to service profiles initially as user lewisa (uid=1001, gid=100) (pid 10056)
[2008/11/07 12:16:26, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 4 bytes to client 192.168.2.100. Error = Connection reset by peer
[2008/11/07 12:16:26, 1] smbd/service.c:close_cnum(1230)
  office1 (192.168.2.100) closed connection to service profiles
[2008/11/07 12:16:44, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2008/11/07 12:16:44, 0] lib/util_sock.c:send_smb(761)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2008/11/07 12:17:11, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2008/11/07 12:17:11, 0] lib/util_sock.c:send_smb(761)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2008/11/07 12:41:57, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 64574 bytes to client 192.168.2.100. Error = No route to host

Thank you in anticipation of your response

---


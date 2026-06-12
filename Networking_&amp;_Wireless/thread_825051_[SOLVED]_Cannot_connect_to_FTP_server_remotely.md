---
title: "[SOLVED] Cannot connect to FTP server remotely"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by lordfkiller on 2008-06-10
I have set up an FTP server using vsftpd and it is working well locally. But I cannot connect to it over Internet.

The computer is connected to a D-Link ADSL modem. Modem firewall is off and port 21 is being forwarded to the server(using virtual servers). Also my ISP believes that port 21 is open and my computer may listen to it.
But it still sounds like as if the packets are being blocked somewhere. When monitoring packets with Wireshark on the server computer, no packets arrive from people who are trying to login to FTP server.

I have also used online port scanners and telnet(Windows XP). They all say port 21 is not open.

How can I tell where the packets are being blocked from?

OS: Ubuntu Hardy x86_64

Any help is appreciated.

---

### Post by fwre01 on 2008-06-10
does your router have any log files you can look at? Did your ISP tell you that they allow FTP sites (on port 21) to be hosted on home ADSL accounts? i have known ISPs to block common server ports.

---

### Post by lordfkiller on 2008-06-10
Yes. They said I can listen to port 21 and run an FTP server.

The log file does not give any useful information. Just connect and disconnect times etc.

---

### Post by superprash2003 on 2008-06-10
then there probably is something wrong with your port forwarding.. could you post a screenshot of your port forwarding page.. also maybe you could try disabling firewall temporarily..

---

### Post by lordfkiller on 2008-06-11
4 images are attached. Firewall's already disabled.

Isn't there a way to track packets and see where they are blocked from? Something like tracerout that works with TCP ports too(not just ICMP).

---

### Post by lordfkiller on 2008-06-11
After calling the ISP again, they said TCP 21 is blocked!! I think their staff were sleepy last time as I called at 2 AM :)

---


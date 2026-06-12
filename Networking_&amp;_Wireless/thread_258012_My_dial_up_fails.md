---
title: "My dial up fails"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by S.A.A on 2006-09-15
Hi everyone:
I have Lucent/Agere modem, and i have installed the driver as it mentioned in the DialupModemHowto.
But, when i tried to dial up, i had this in the terminal:

Sep 15 16:55:14 localhost chat[8427]: send (ATZ^M)
Sep 15 16:55:14 localhost chat[8427]: send (AT&FH0L2^M)
Sep 15 16:55:15 localhost chat[8427]: expect (OK)
Sep 15 16:55:15 localhost chat[8427]: ATZ^M^M
Sep 15 16:55:15 localhost chat[8427]: OK
Sep 15 16:55:15 localhost chat[8427]:  -- got it
Sep 15 16:55:15 localhost chat[8427]: send (ATDT.....^M)
Sep 15 16:55:15 localhost chat[8427]: timeout set to 75 seconds
Sep 15 16:55:15 localhost chat[8427]: expect (CONNECT)
Sep 15 16:55:15 localhost chat[8427]: ^M
Sep 15 16:55:15 localhost chat[8427]: AT&FH0L2^M^M
Sep 15 16:55:15 localhost chat[8427]: OK^M
Sep 15 16:55:16 localhost kernel: [4294900.518000]  [__report_bad_irq+34/128] __report_bad_irq+0x22/0x80
Sep 15 16:55:16 localhost kernel: [4294900.518000]  [note_interrupt+104/192] note_interrupt+0x68/0xc0
Sep 15 16:55:16 localhost kernel: [4294900.518000]  [__do_IRQ+188/224] __do_IRQ+0xbc/0xe0
Sep 15 16:55:16 localhost kernel: [4294900.518000]  [do_IRQ+26/48] do_IRQ+0x1a/0x30
Sep 15 16:55:16 localhost kernel: [4294900.518000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Sep 15 16:56:07 localhost chat[8427]: ATDT.....^M^M
Sep 15 16:56:07 localhost chat[8427]: CONNECT
Sep 15 16:56:07 localhost chat[8427]:  -- got it
Sep 15 16:56:07 localhost pppd[8363]: Serial connection established.
Sep 15 16:56:07 localhost pppd[8363]: Using interface ppp0
Sep 15 16:56:07 localhost pppd[8363]: Connect: ppp0 <--> /dev/modem
Sep 15 16:56:38 localhost pppd[8363]: LCP: timeout sending Config-Requests
Sep 15 16:56:38 localhost pppd[8363]: Connection terminated.
Sep 15 16:56:39 localhost pppd[8363]: Hangup (SIGHUP)
Sep 15 16:56:39 localhost pppd[8363]: Modem hangup
Sep 15 16:56:39 localhost pppd[8363]: Exit.

Please help me !!!!

---

### Post by Iowan on 2006-09-15
I have dial-up - but it's on a separate router/firewall (not Ubuntu), so I'm only speculating about the problem.  It *appears* that the connection is established, but the authorization/authentication (CHAP/PAP/ETC?) doesn't happen (or even try). My guess is that the modem may be working, but the ensuing processes are not.

---


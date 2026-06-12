---
title: "Modem init fail strings"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by ubuntunewb75 on 2005-07-14
Well I finally found out where my modem was residing and linked it to dev/modem.  I can dial out now but I get this error message in the log file of gnomeppp.  It gives the same error if I dial out using wvdial:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT246-0001
--> Waiting for carrier.
ATM1L1DT246-0001
CONNECT 33600/ARQ/V34/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
CVX Access Switch.
Access is restricted to authorized users only.
login: 
--> Looks like a login prompt.
--> Sending: ppp289
ppp289
password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Jul 14 12:41:52 2005
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 11325
--> Using interface ppp0
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> Disconnecting at Thu Jul 14 12:42:00 2005
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT246-0001
--> Waiting for carrier.
ATM1L1DT246-0001

 16     The link was terminated by the modem hanging up.


I know my password is correct as well as the login name as I am using the same config for my windows laptop to post this  :smile:   the 16 at the bottom is the description of the fail code.  Is it my modem that is hanging up or is it the ISP doing the hanging up?

---

### Post by ubuntunewb75 on 2005-07-14
I also checked the logs for PON and tried connecting through pon and got this message:

Jul 14 13:35:27 localhost chat[12072]: abort on (NO ANSWER)
Jul 14 13:35:27 localhost chat[12072]: abort on (DELAYED)
Jul 14 13:35:27 localhost chat[12072]: send (ATZ^M)
Jul 14 13:35:27 localhost chat[12072]: expect (OK)
Jul 14 13:35:27 localhost chat[12072]: ATZ^M^M
Jul 14 13:35:27 localhost chat[12072]: OK
Jul 14 13:35:27 localhost chat[12072]:  -- got it
Jul 14 13:35:27 localhost chat[12072]: send (ATDT2460001^M)
Jul 14 13:35:27 localhost chat[12072]: expect (CONNECT)
Jul 14 13:35:27 localhost chat[12072]: ^M
Jul 14 13:35:59 localhost chat[12072]: ATDT2460001^M^M
Jul 14 13:35:59 localhost chat[12072]: CONNECT
Jul 14 13:35:59 localhost chat[12072]:  -- got it
Jul 14 13:35:59 localhost chat[12072]: send (\d)
Jul 14 13:36:00 localhost pppd[12071]: Serial connection established.
Jul 14 13:36:00 localhost pppd[12071]: Using interface ppp0
Jul 14 13:36:00 localhost pppd[12071]: Connect: ppp0 <--> /dev/modem
Jul 14 13:36:04 localhost pppd[12071]: Hangup (SIGHUP)
Jul 14 13:36:04 localhost pppd[12071]: Modem hangup
Jul 14 13:36:04 localhost pppd[12071]: Connection terminated.
Jul 14 13:36:06 localhost pppd[12071]: Exit.

hope this will help

---

### Post by alastair on 2005-07-14
This stuff is the most arcane and obscure in Linux I think.

The connection is made but something wrong happens after. Probbaly some sort of login/comm problem. Perhaps you need to send something else? e.g.

I always had to send "ppp" to a "protocol" question i.e.

login
password
protocol

encoded as :

ogin:--login: <USER> \
word: "\q<PASS>" \
ocol: ppp

in my "chat" script. It's been a long time though. Perhaps you could use "minicom" or something to dial-out and see what happens?

---

### Post by thunder_bear on 2005-07-18
Hey, every fine? I hope so!

Well, sometimes I have this problem hier in Brazil...
I verify everithing who I knew, but I can't find any aparent problem.
But, when I start my PC and go directly to connect to the Internet, my connection be stable! When I start some music after the connection, I have problems and just rebooting the PC I can connect to the Internet... If this don't help u, sorry, but I trying help to!
See

---


---
title: "Modem Help Needed!!"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Implied Quotient on 2008-08-28
Hey guys,

I'm running a U.S. Robotics Model 3092 PCI 56K Modem, and although it works well in Windows XP, it fails in Ubuntu.

Whenever I run wvdial it comes up with this:

> --> Carrier detected.  Waiting for prompt.
UQKT2 tnt1.****.**.da.uu.net
Login: 
--> Looks like a login prompt.
--> Sending: <***************>
<*************>
Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Aug 28 11:54:17 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6910
--> Using interface ppp0
--> pppd: &#1575;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1575;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1575;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1575;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1575;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Thu Aug 28 11:54:47 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


What should I do?

Thanks!

---

### Post by Implied Quotient on 2008-08-28
Bump...

Do I need to post more info?

---

### Post by xadder on 2008-09-04
I had similar problems today (on my father-in-laws computer) so am curious to know if you solved this?

---

### Post by mfdc1969 on 2008-09-13
I have pretty much the same dialogue after my modem fails. 

I have an Acer 5610Z with a Conexant HSF modem running the [Dell drivers from this Ubuntu Community support page]("https://help.ubuntu.com/community/DialupModemHowto/Conexant"):

```
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Sep 13 07:13:44 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 21948
--> Using interface ppp0
--> Disconnecting at Sat Sep 13 07:13:58 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

Looking into the pppd man pages I can decipher that the Exit Code 16 simply means the modem has hung up. But I don't under stand the line:

```
Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
```

I gather it's an issue of file permissions but is anyone able to explain that line in simpler terms?

Thanks.

------------

*** Note: I am no longer using Hardy and have installed Intrepid so I welcome the new challenge of this modem!

---


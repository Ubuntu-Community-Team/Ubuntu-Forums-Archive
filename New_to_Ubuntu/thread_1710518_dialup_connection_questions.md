---
title: "dialup connection questions"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by wsl on 2011-03-20
This message was originally posted in: [http://ubuntuforums.org/showthread.php?t=1589966&page=3](http://ubuntuforums.org/showthread.php?t=1589966&page=3)   #30
And,now I learned how to start a new thread.

"
Hi,

I am new to Ubuntu. I don't know if it is good to post here for my dialup.

I installed Ubuntu 6.06.1 Desktop on my old HP Celron 533, 194MB memory. Working nicely and I am happy except dialup.

My Modem is USB USR detected on /dev/ttyACM0. Now I am trying KPPP. I tried two connections to two different companies but the same problem.
(These 2 connections work well in my MS Windows system in the same computer and moodem easily.)


I am trying modem settings as follows.

Flow control: Hardware
Line termination: CR
Connection speed: have tried 19200, 38400, 57600

I config "Dial" tag, Authentication: to PAP/CHAP, after well dialing up, I got PPP log:
...[pppd7844]: The remote system is required to authenticate itself but I couldn't find any suitable secret (password) for it to use to do so....


The better try is set "Dial" tag, Authentication: Terminal-based, and then input my login name and password manually, and then on Login Script Debug Window:

Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP...
Header compression is on.

~...}#@!}!u} &}*.... a lot of these kind of stuff. Around 20 lines. Then,
NO CARRIER

in PPP log:
...[pppd8739]: The remote system is required to authenticate itself but I couldn't find any suitable secret (password) for it to use to do so....



Still can not go online. It is obviously problem on setting but it's almost there. Pls help!
"

----------------

Original replies pls ref: [http://ubuntuforums.org/showthread.php?t=1589966&page=4](http://ubuntuforums.org/showthread.php?t=1589966&page=4)   #31 and #32.

And my reply in #33 there is:

"
 Re: dialup connection
I was suggested to have new thread but I don't know how to start.

Can't find wvdial in menus in x-window, but in terminal, yes.

After trying wvdial:
sudo pppconfig
sudo wvdialconf /etc/wvdial.conf
sudo edit text/conf:wvdial.conf
(manually key in login name, pw, tel#)
wvdial /etc/wvdial.conf

Finally... works on Bell's connection well but not on 295.ca's connection.
Well, not easy. Any quick way? Like setup an icom on desktop and click it?

Why KPPP does not work?
Thank you all.
"
--------------
Then, original replies pls ref: [http://ubuntuforums.org/showthread.php?t=1589966&page=4](http://ubuntuforums.org/showthread.php?t=1589966&page=4)   #34.

--------------
***********   ************   *********

Now, when Ubuntu is starting my computer, the dialup is automatically establishing. Thus, just right after login into Ubuntu, I can go online by clicking FireFox right away. It's so convenient and no waiting any more! Even I have not install nor run GNOME-PPP yet. Is Gnome-ppp still necessary?

I have tried the previously installed KPPP, it shows that "the modem is busy", of course.

Now, if I want to dial a phone call, how can I stop the connection? This connection must be by wvdial. Neither KPPP nor Gnome-PPP can cut in this connection to disconnect it.  

Thank you, lk!

---

### Post by jre6 on 2011-03-20
> **wsl said:**
> Is Gnome-ppp still necessary?!
No, Gnome-PPP is not necessary, and has not undergone any development since a long time, and in my case, never dialed and only failed, in spite of the fact that all configuration was done correctly.

> **wsl said:**
> Now, if I want to dial a phone call, how can I stop the connection? This connection must be by wvdial.

Type in the terminal :
```
ps ajxf | grep wvdial
```

Something should come up. Check the text at the extreme right. If there is some text like "/usr/bin/wvdial" to the right, see the corressponding second number from the right. This value is the PID.

Kill wvdial with the pid by typing:
```
kill *pid*
```

Example:
```
user@ubuntu:~$ ps ajxf | grep wvdial
    1  2700  1327  1327 ?           -1 Sl    1000   2:17 /usr/bin/wvdial
 2795  2813  2812  2795 pts/0     2812 S+    1000   0:00      \_ grep --color=auto wvdial
user@ubuntu:~$ kill 2700
```

---

### Post by wsl on 2011-03-20
Thank you, jre6,

I got this:

user@HP0:~$ ps ajxf | grep wvdial
 5922  5974  5973  5922 pts/0     5973 S+    1001   0:00      \_ grep wvdial
user@HP0:~$

What number shoudl be PID? 2nd number from the right or left? 5974 or 5973 or 5900?

---

### Post by wsl on 2011-03-20
Tried again as these follows:

n@HP0:~$ ps ajxf | grep wvdial
 6671  6754  6753  6671 pts/0     6753 R+    1001   0:00      \_ grep wvdial
n@HP0:~$ kill 6754
bash: kill: (6754) - No such process
n@HP0:~$ kill 6753
bash: kill: (6753) - No such process
n@HP0:~$ kill 6671
n@HP0:~$


But, still connecting well and I am usingthis connection to send this reply.

---

### Post by wsl on 2011-03-21
Now, I am installing another old PC.

Wvdial is OK:

w@Dell0:~$ wvdial /etc/wvdial.conf
--> WvDial: Internet dialer version 1.55
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT5143505262
--> Waiting for carrier.
ATDT5143505262
CONNECT 26400/ARQ/V34/LAPM/V42BIS
belmoncnas47 line 92
Unauthorized Access Prohibited
Acces non-autorise interdit
BELMONCNAS47
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
Username:
--> Looks like a login prompt.
--> Sending: xxxxx
xxxxx
Password:
--> Looks like a password prompt.
--> Sending: (password)
Selection:
Selection:
Selection:
Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP address is 0.0.0.0. MTU is 1500 bytes
Header compression is on.
--> Looks like a welcome message.
--> Starting pppd at Mon Mar 21 22:15:09 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6748
--> Using interface ppp0
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> local  IP address 64.228.179.22
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> remote IP address 64.228.179.241
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> primary   DNS address 207.164.234.129
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]
--> secondary DNS address 67.69.235.1
--> pppd: &#65533;&#65533;[05][08][08][01][06][08]



As conecting, so I can use this connection to send this message. Yet, listed warnings.


But, after restart, it does not auto connect to dialup. My KPPP also has the same problems:

OK

OK

CONNECT 26400/ARQ/V34/LAPM/V42BIS

belmoncnas47 line 2 

Unauthorized Access Prohibited
Acces non-autorise interdit
BELMONCNAS47 

User Access Verification

Username: xxxxx
Password: 
Selection: 
Selection: 
Selection: 
Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP address is 0.0.0.0. MTU is 1500 bytes
Header compression is on.

~}#@!}!q} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp"E~~}#@!}!r} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrpR~~}#@!}!s} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp}-9~~}#@!}!t} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp#}&~~}#@!}!u} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp|<~~}#@!}!v} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp},z~~}#@!}!w} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrpS@~~}#@!}!x} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrpP}%~~}#@!}!y} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrp}/?~~}#@!}!z} &}"}&} }*} } }%}&m_I}'}"}(}"}1}$}%t}3}.}!MONStackGrpy~
NO CARRIER




Error-KPPP

The pppd daemon died unexpectedly!

Exit status:1
See 'man pppd' for an explanation of the error codes or take a look at the kppp FAQ on [http://developer.kde.org/~kppp/index.html](http://developer.kde.org/~kppp/index.html)


Detail, PPP Log:

Mar 21 21:57:16 Dell0 pppd[6280]: The remote system is required to authenticate itself
Mar 21 21:57:16 Dell0 pppd[6280]: but I couldn't find any suitable secret (password) for it to use to do so.


How should I setup my KPPP?

Tks.

---

### Post by wsl on 2011-03-21
Finally, I found a way to install Gnome-PPP and it is running well (sending message through this connecton) for this 2nd PC and I will try Gnome-PPP in the 1st PC, later. Gnome-PPP seems to be much easier than KPPP in Ubuntu 6.

---

### Post by beew on 2011-03-22
Eh... pardon my ignorance. Is there a Ubuntu release that comes out in June? (6.06??) Is there a reason why you are still running Ubuntu 6?

---

### Post by wsl on 2011-03-25
Actually, it's ver. 6.06 I meant.

---


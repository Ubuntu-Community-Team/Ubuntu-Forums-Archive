---
title: "Unable to set the login prompt in wvdial.conf"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by muntasir_120 on 2009-01-01
I've just signed up for a new dial-up ISP who uses a non-standard prompt to ask for the Username. I set the Login Prompt to the ISPs prompt string ('Ranks-ITT') as suggested in wvdial.conf's manpages, but still when I dial, wvdial sends 'ppp' on seeing the ISPs prompt. I am pasting the relevant section of my wvdial.conf file below,

```
[Dialer ranx]
Username = whale
Password = something
Login Prompt = Ranks-ITT:
Phone = 0101333
```

Searching the web didn't turn up anything diffrent. Can someone please point out my mistake?

Thanks in advance.

---

### Post by ieee488 on 2009-01-01
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

It doesn't look like you set the Login string which you need in addition to Login Prompt. Your sequence is not quite right so wvdial just goes ahead and starts up pppd.

---

### Post by muntasir_120 on 2009-01-19
Thanks for your help. 

I didn't think that the order of the options in wvdial.conf mattered. Also, what is the difference between the 'Login' and the 'Username' strings? I had tried setting both (together and separately) even before I posted here.

I made changes to my wvdial.conf as you suggested, but  I still can't login. I'm posting my complete wvdial.conf file below.

```
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 0101340
Modem = /dev/ttyS0
Username = someone
Login = someone
Login Prompt = Ranks-ITT:
Password = something
Baud = 460800

[Dialer ranx]
Phone = 0101331
Login = someone
Login Prompt = Ranks-ITT:
Password = something
```

Thanks again.

---

### Post by muntasir_120 on 2009-01-23
Here's what I get when I try to login, if that helps.

```
muntasir@muntasir-desktop:~$ sudo wvdial ranx
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT0101331
--> Waiting for carrier.
ATDT0101331
CONNECT 9600
--> Carrier detected.  Waiting for prompt.
User Access Verification
Ranks-ITT:
Ranks-ITT:
--> Hmm... a prompt.  Sending "ppp".
ppp
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Ranks-ITT:
--> Hmm... a prompt.  Sending "ppp".
ppp
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Fri Jan 23 15:12:12 2009
muntasir@muntasir-desktop:~$ 

```

Can anyone tell me where my mistake is?

---

### Post by lkraemer on 2009-01-23
Perhaps you should try this to see if it will help.

[http://tldp.org/HOWTO/Modem-HOWTO-11.html#ss11.1](http://tldp.org/HOWTO/Modem-HOWTO-11.html#ss11.1)

REF 11.1 and the following sections.

Have a look at this:
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

under "Configuring a Dial-Up Connection using pppconfig"

Did you configure ppp??  PAP or CHAP?  etc....

It appears that you are getting connected for a bit but the problem
is with ppp and the authentication.

OH, before I forget. Go check your PM.  I replied several days ago about
this and you haven't read the PM (Private Mail).

lkraemer

---

### Post by muntasir_120 on 2009-01-23
Thank you.

Just a few minutes ago I got wvdial to send my username by setting the 'Default Reply' option in wvdial.conf. But I still get an '% Authentication Failed' response from my ISP after sending my username and password correctly.

I am also reading the tutorials you've suggested. Hopefully I will find a solution there.

BTW, I didn't get any PM from you. My PM inbox is empty save for the welcome message.

---

### Post by muntasir_120 on 2009-01-23
Thank you lkraemer. After reading those tutorials I managed to login without wvdial, using Ubuntu's Networking option.

---


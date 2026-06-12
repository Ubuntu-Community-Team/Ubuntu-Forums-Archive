---
title: "External modem problems."
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by chuckman78 on 2006-10-04
Hi, everyone.

  After trying and missing with Dapper 6.06.0 LTS I retried to get my USRobotics External modem to work with Dapper 6.06.1 LTS. Results: the same as before, I can get gnome-ppp (and wvdial) to recognize the modem, it begins the process of connecting (dialing tones and handshaking tones, beeps and quirks) but at some point the modem stops and I see a "NO CARRIER" alert at the connection log. 

   This behavior also happens under Debian Sarge 3.1r2 and even under SUSE 10.0. The modem works flawlessly under Windows XP PRO. 

   The funny thing is that I can get a winmodem (Intel 537EP chipset) to work under Drape 6.06.0 and 6.06.1 but not the "real" external USRobotics one which should be a lot easier and straight  forward to do. ( I´ve could not make the 537EP winmodem to work on SUSE but that is another story).

   I used to get the USRobotics modem working on Breazy 5.10 with great performance but not anymore on Dapper. I have tried modifying a big set of parameters but I have had no luck. 

   Anybody with this problem? Any workaround? Any fix? It is pretty annoying to have bought this modem for this unique task (using it under linux) and not getting results. Thanks in advance for your help.

Regards,

Carlos.

---

### Post by _duncan_ on 2006-10-05
Not sure if we have the same modem. I used to have an external US Robotics Faxmodem that I couldn't get to work with Breezy (or any linux distro for that matter).

Breezy would auto-detect the modem, even dial-out to my ISP and negotiate a baud rate, then nothing. I narrowed it down as an authentication problem, but couldn't find a solution for it. I can probably fill up this page with all sorts of possible workarounds I tried, but no success.

Out of desperation, I went out and bought a cheap smartlink winmodem and got on-line in less than an hour. This same modem works well also in Dapper, but not the external USR modem. To date, I can get very good connection using this hardware modem in Windows XP.

Personally, I'm willing to concede that this modem just won't work with linux and move on.

---

### Post by chuckman78 on 2006-10-05
Hi _duncan_.

> **_duncan_ said:**
> Breezy would auto-detect the modem, even dial-out to my ISP and negotiate a baud rate, then nothing. I narrowed it down as an authentication problem, but couldn't find a solution for it. I can probably fill up this page with all sorts of possible workarounds I tried, but no success.

Yes, I know, been there, done that.

> **_duncan_ said:**
> Out of desperation, I went out and bought a cheap smartlink winmodem and got on-line in less than an hour. This same modem works well also in Dapper, but not the external USR modem. To date, I can get very good connection using this hardware modem in Windows XP.

That is exactly my situation, I got a cheap Intel 537EP chipset based modem and works great in Debian sarge and Ubuntu (I haven`t been able to get it working on SUSE 10.0, but that is another story).

> **_duncan_ said:**
> Personally, I'm willing to concede that this modem just won't work with linux and move on.

I am in the same position. It is just that it is really frustrating to have such a "suposedly" good piece of hardware and can´t get it to work in a way that is suposed to work flawlessly.

Regards,

Carlos.

---

### Post by chuckman78 on 2006-10-27
Hi all.

In case anyone is still interested, I got the modem working. It just needed the right Init strings. Here is a copy of my wvdial.conf file:

```

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200,N,8,1
SetVolume = 2
Dial Command = ATDT
[B]Init1 = ATZ
Init2 = AT&F1E0Q0V1&C1&D2S0=0
Init3 = ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4
Init4 = ATS10=255S11=40&U30&N39
Init5 = ATDT;[/B]
FlowControl = CRTSCTS

Username = xxxxxxxxxx
Password = xxxxxxxxxx
Phone = 555-5555
Idle Seconds = 0
Abort on Busy = off
Abort on No Dialtone = off
New PPPD = yes
Auto DNS = on
Dial Attempts = 0
Check DNS = on
Carrier Check = no
Auto Reconnect = yes
```

The relevant part is bolded but you could try with all the other stuff too.

Regards,

Carlos.

---

### Post by vanishedsoul on 2006-11-12
> **chuckman78 said:**
> Hi all.

In case anyone is still interested, I got the modem working. It just needed the right Init strings. Here is a copy of my wvdial.conf file:

```

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200,N,8,1
SetVolume = 2
Dial Command = ATDT
[B]Init1 = ATZ
Init2 = AT&F1E0Q0V1&C1&D2S0=0
Init3 = ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4
Init4 = ATS10=255S11=40&U30&N39
Init5 = ATDT;[/B]
FlowControl = CRTSCTS

Username = xxxxxxxxxx
Password = xxxxxxxxxx
Phone = 555-5555
Idle Seconds = 0
Abort on Busy = off
Abort on No Dialtone = off
New PPPD = yes
Auto DNS = on
Dial Attempts = 0
Check DNS = on
Carrier Check = no
Auto Reconnect = yes
```

The relevant part is bolded but you could try with all the other stuff too.

Regards,

Carlos.

can you please explain whats are those "Init strings" for? I having the same modem. Do i have to change those those string or they will work fine for me too? I have a little bit different problem is that modem has been detected but after the handshaking tone ( when handskaing tone stops), it gets disconnected, it never gets connected. The username passwords are all fine and its  already working on the winxp pro...:confused:

---

### Post by vanishedsoul on 2006-11-12
well i have copied the above config file and it worked for me, however the int3 gave error and i removed it and then tried and it worked fine, thanks

---

### Post by chuckman78 on 2006-11-14
Hi.

 I am glad it worked for you! Regarding the Init stuff, I know that they are used for modem initialization and configuration but I don´t know the details (it is in a todo list to learn more about this -as if I had the time :( ).

Regards,

Carlos.

EDIT: Check this link: 

[http://members.tripod.com/michaelgellis/modem.html]("http://members.tripod.com/michaelgellis/modem.html")

It´s got information on Init commands.

---

### Post by _duncan_ on 2006-11-17
Hi Carlos,

Thank you for sharing the info. It works perfectly for me too! Instead of wvdial, I used gnome-PPP, clicked on the "Setup" and "Init String" buttons respectively, then typed in the init string values as posted.

Duncan

---

### Post by chuckman78 on 2006-11-17
> **_duncan_ said:**
> Hi Carlos,

Thank you for sharing the info. It works perfectly for me too! Instead of wvdial, I used gnome-PPP, clicked on the "Setup" and "Init String" buttons respectively, then typed in the init string values as posted.

Duncan

Duncan, I am glad it worked for you. I used to dial with **gnome-ppp** too but then I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=197300") about dialing scripts and I have been using **wvdial** with the scripts and I have gotten great resuls.

Regards, 

Carlos.

---

### Post by RJARRRPCGP on 2007-04-10
> **_duncan_ said:**
> Not sure if we have the same modem. I used to have an external US Robotics Faxmodem that I couldn't get to work with Breezy (or any linux distro for that matter).

Breezy would auto-detect the modem, even dial-out to my ISP and negotiate a baud rate, then nothing. I narrowed it down as an authentication problem, but couldn't find a solution for it. I can probably fill up this page with all sorts of possible workarounds I tried, but no success.

Out of desperation, I went out and bought a cheap smartlink winmodem and got on-line in less than an hour. This same modem works well also in Dapper, but not the external USR modem. To date, I can get very good connection using this hardware modem in Windows XP.

Personally, I'm willing to concede that this modem just won't work with linux and move on.

Hey folks, listen. I can't use the internet under Ubuntu, at least with my US Robotics USR5686E modem, but it's not "NO CARRIER". 

Instead, it's an error message about LCP timing out, but only sometimes. 

With or without an error message, it always gets hanged up! 

It better not be because of the ISP! It's more likely to be the ISP's fault, because after years of being indenpendently owned, got aquired by a company outside of the state in 2006 or late 2005. 

UPDATE:

Please see this post:

[http://ubuntuforums.org/showthread.php?t=405513](http://ubuntuforums.org/showthread.php?t=405513)

---

### Post by chuckman78 on 2007-04-12
Hi.

Few questions:

1) Did you try with the init strings I mentioned before?

2) Are you sure your modem is at ttyS0? Might be at ttyS1 or ttyS2 or other.

I have had no problems with my modem on Edgy or Dapper since I fixed the init strings. It works flawlessly.

Regards,

Carlos.

---

### Post by RJARRRPCGP on 2007-04-12
> **chuckman78 said:**
> Hi.

Few questions:

1) Did you try with the init strings I mentioned before?

2) Are you sure your modem is at ttyS0? Might be at ttyS1 or ttyS2 or other.

I have had no problems with my modem on Edgy or Dapper since I fixed the init strings. It works flawlessly.

Regards,

Carlos.

Yep, it's on ttys0, because I always use COM1 and it did dial. The only thing I didn't try was the init strings.

But with all of the hanging ups, I ended up suspecting the ISP's authentication system!

I only gotten that kind of bull before, because my password entry and/or username entry was corrupted.

With the exact same settings, the Zoom 3048C is fine.

[COLOR=Lime]Getting disconnected is always rare with the Zoom 3048C. [/COLOR]

The US Robotics 5686E has strange behavior, under Windows XP, it dials and I'm able to use the internet, but randomly get disconnected and usually takes at least two dials, if not three to stay connected.

---

### Post by jitsu on 2007-04-29
I'm new to Ubuntu--

I have a TRENDnet TFM-560X ext. serial port modem and I'm using it now on Ubuntu 6.06. I installed Ubuntu 6.10 and the modem was not detected and with my limited knowledge I went back to Ubunt 6.06.

This modem is definitely a Linux compatible modem. What do I have to do to get it recognized and working in the 6.10 distro?

thanks,
jitsu

---

### Post by chuckman78 on 2007-04-29
Hi, jitsu.

What do you use to connect? I use wvdial. In case you use it, edit the wvdial.conf file changing these lines:

```
[Dialer Defaults]
[B]Modem = /dev/ttyS0
Baud = 115200,N,8,1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
FlowControl = CRTSCTS
ISDN = 0
Modem Type = Analog Modem[/B]

Phone = *Your ISP phone number*
Username = *Your username*
Password = *Your password*

Idle Seconds = 0
Abort on Busy = off
Abort on No Dialtone = off
New PPPD = yes
Auto DNS = on
Dial Attempts = 0
Check DNS = on
Carrier Check = no
Auto Reconnect = yes
```

The most relevant parts are on bold characters. I hope this help.

Regards,

Carlos.

---

### Post by jitsu on 2007-04-29
Hi Carlos:
I don't know what I'm using to dial. 

I tried yesterday to find something on WVDialer and WvDialer Conf. and I haven't been able to find any information.

On Ubuntu 6.06 in the setup, I hit autodetect (the modem) and everything worked. 

On 6.10 I don't get a thing.

I would like to upgrade to 6.10 but want the modem to work.

thank you very much for your help,

Charles

---

### Post by chuckman78 on 2007-04-29
Hi again.

**wvdial** is a terminal based utility for dialing an ISP. You just need to find the wvdial.conf file and edited the way I wrote in my last post.

To do this open a terminal box and type:

```
sudo gedit /etc/wvdial.conf
```


A window with the wvdial.conf file will open, edit it. Then save it.

Then in the terminal box type:

```
sudo wvdial
```

And the computer will try to connect to your ISP. If it is succesfull just keep that terminal open while you surf, close it to end the connection.

Regards,

Carlos.

---

### Post by jitsu on 2007-04-30
Hi Carlos:

I'm going to try to upgrade to Ubuntu in about a week or so. I will do what you suggest. I have to straighten out my Windows machine that picked up some malware.

Thank you very much for your help,
Charles

---


---
title: "how to connect to internet using sony ericsson k750i on  linux (ubuntu7.04)"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by yosahaj on 2007-09-10
hi

i've just installed the ubuntu 7.04 on my pc...

i've **sony ericsson k750i **handset with** unlimited gprs acces**...
but i dont know how to** access the internet** on linux....
coz when i'm using windows...i've the** sony ericsson pc suit** which have*** mobile networking wizard***..
using that i used to connect to internet.. But here it seems to dificult coz[U] the sony ericsson pc suit is not
supported to linux so i cant install it on linux...[/U]
so anybody plz tell me how to connect to internet using  sony eri..k750i  on linux....
coz i'm new to linux...i dont have any idea...:confused:
help me out plz..

---

### Post by mul14 on 2007-11-05
I have same problem. Gutsy can't detect my SE K750i as modem.

And.. how to create dial-up connection with Linux?

I use Ubuntu 7.10 Gutsy Gibbon.

---

### Post by singh2485 on 2007-11-23
I connected to net using a w700i phone. (Maybe it works for other models too)

Here's how i did it.

```
sudo wvdialconf
```

It will scan for the modems connected.
and will update the /etc/wvdial.conf 

It will tell you which port your modem is connected to..

Then try using kppp for configuring and connecting... You can use the modem you found earlier...

Or try editing the /etc/wvdial.conf (use su)
Give a username, password and phone number string

Then run 
```
wvdial 
```(in some terminal)

Should connect.

---

### Post by rraj.be on 2008-01-03
> **singh2485 said:**
> I connected to net using a w700i phone. (Maybe it works for other models too)

Here's how i did it.

```
sudo wvdialconf
```

It will scan for the modems connected.
and will update the /etc/wvdial.conf 

It will tell you which port your modem is connected to..

Then try using kppp for configuring and connecting... You can use the modem you found earlier...

Or try editing the /etc/wvdial.conf (use su)
Give a username, password and phone number string

Then run 
```
wvdial 
```(in some terminal)

Should connect.


Hey thanks a lot for u but i did'nt get the stuff of being changing my user name and telephone no
could u help me..

another thing how to mail to ur personal mail adress.... form a forum

---

### Post by hunter_te on 2008-03-22
Here is how u do it..... works for both, fiesty and gutsy ;)

1.Connect the mobile via USB cable.

2. Open terminal and type "sudo su" to become root.

3. It will ask for the root password, type in there.

4. Then Issue this command
Code:

wvdialconf /etc/wvdial.conf

Phone wud b detected as Modem

5. Then to Edit this file, open it in a Text Editor

Code:

gedit  /etc/wvdial.conf

When we issued command in point 4, it showed the address of ur phone that in which USB port it has been connected. note it down from there.
"Modem = /dev/***"

6. When Text Editor opens the file, erase everything from there and Paste the following:
Code:

[Dialer Defaults]
Modem = /dev/ttyUSB0  # <------- Replace it with the reading you got 
Phone = *99#   #<-----Replace this with service provider number
Username = abc
Password = xyz
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Carrier Check = No

The mOdem has been configured successfully.

To dial the internet conenction type
Code:

wvdial

If eerything goes fine it wud say that connected successfully.
Press Ctrl+C to disconnect.


If it doesnt work, then call up ur cellphone provider and ask them the number to dial to get internet working from a PC. They may even require u to have unique id and password. 

GoodLuck

---


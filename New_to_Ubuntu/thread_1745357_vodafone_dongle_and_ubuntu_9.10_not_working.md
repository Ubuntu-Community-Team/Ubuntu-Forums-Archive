---
title: "vodafone dongle and ubuntu 9.10 not working"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Anna22 on 2011-04-30
Hi Guys,

I am completely new to this forum and quite desperate to install my new Vodafone Mobile Broadband Dongle thing working in Ubuntu 9.10 on my eee pc (in new-zealand) . I only have been working with ubuntu since a couple of months, so please help me! 

I've tried to follow the advices given online but I am now completly stuck.

- First,  tried to create a new connection by right  clicking on the network manager applet and selecting 'Edit  Connections', then choosing the 'Mobile Broadband' tab and clicking  'add'. The problem I had was that after I selected 'WAP' from  the list, it wouldn't connect and came up with a box demanding  the password. I searched the internet and tried pretty much everything suggested, none worked. 

Then,as suggested in some threads I changed the APN to " www.vodafone.co.nz" . 
Didn't work.

So, what could I do now ?
Any suggestion will be appreciated !

Cheers

---

### Post by alphacrucis2 on 2011-05-01
> **Anna22 said:**
> Hi Guys,

I am completely new to this forum and quite desperate to install my new Vodafone Mobile Broadband Dongle thing working in Ubuntu 9.10 on my eee pc (in new-zealand) . I only have been working with ubuntu since a couple of months, so please help me! 

I've tried to follow the advices given online but I am now completly stuck.

- First,  tried to create a new connection by right  clicking on the network manager applet and selecting 'Edit  Connections', then choosing the 'Mobile Broadband' tab and clicking  'add'. The problem I had was that after I selected 'WAP' from  the list, it wouldn't connect and came up with a box demanding  the password. I searched the internet and tried pretty much everything suggested, none worked. 

Then,as suggested in some threads I changed the APN to " www.vodafone.co.nz" . 
Didn't work.

So, what could I do now ?
Any suggestion will be appreciated !

Cheers

I have one running fine on 10.10. I didn't preconfigure anything IIRC. Just plugged it and I think it asked me what provider to use and vodafone NZ was listed. When I look at the config under NM it has just internet in the APN field.

---

### Post by lemmy999 on 2011-05-01
I'm using a PAYG Voda dongle in the UK. Settings are number *99#, username and password are left blank. apn should show "pp.internet". IIRC if you are using a contract SIM then the apn should just be "internet"

I can't see any mention of WAP so I'm a little confused where thats coming from.

---

### Post by alphacrucis2 on 2011-05-01
> **lemmy999 said:**
> I'm using a PAYG Voda dongle in the UK. Settings are number *99#, username and password are left blank. apn should show "pp.internet". IIRC if you are using a contract SIM then the apn should just be "internet"

I can't see any mention of WAP so I'm a little confused where thats coming from.

Mine is identical to yours except for apn being just "internet" rather than "pp.internet" and you are right my one is on a monthly contract rather than PAYG. Looks like the UK & NZ settings for these are identical at least for vodafone. Funnily enough the connection is far more stable under Ubuntu than Windows. That may be because the windows driver is a bit old. Ubuntu identifies it as a HUWEI device.

---

### Post by Anna22 on 2011-05-02
> **lemmy999 said:**
> I'm using a PAYG Voda dongle in the UK. Settings are number *99#, username and password are left blank. apn should show "pp.internet". IIRC if you are using a contract SIM then the apn should just be "internet"

I can't see any mention of WAP so I'm a little confused where thats coming from.

When it asks me to choose my billing plan, I can pick from:
 
 &#8220;WAP&#8221; (the apn shows: live.vodafone.com
 &#8220;Restricted&#8221; (apn: [www.vodafone.net.nz]("http://www.vodafone.net.nz/"))
 &#8220;Unrestricted(public) &#8220; (apn: internet)  
 &#8220;My plan is not listed&#8221; ( here the apn is left blank.)
 
Don't know what any of those means, I'm not on a monthly contract, just a pay as you go thing.
 
I tried pp.internet with preselecting WAP and restricted but doesn't seems to wok.
 

 Help  :-) ?!

---


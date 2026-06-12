---
title: "How to configure Evolution for MS Exchange Server 5.5?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by CapsLockmat1 on 2009-02-10
Hello,

        I have Ubuntu 8.1 and I want to configure Evolution for MS Exchange Server 5.5. I read on Evolution FAQ that there is something called Brutus..but it needs installation on both Server and Client site. I don't have access to the Server. So only thing I can play with is my client machine.I heard there is something called as IMAP using which I can do so. If any1 can help me with detailed steps..Or if there is any link...I would be really thankful.

 I installed evolution-exchange and when I tried to connect to the server, it gave error message,
"The server is running Exchange 5.5, evolution-exchange connector supports 2000 and 2003 Server"

Thanks..

- CapsLock

---

### Post by mr_skater99 on 2009-03-17
I'm in the same boat.

Finally convinced the powers that be at work to give the developers a linux desktop.  

We have exchange 5.5 with owa - but this is not supported by the evolution-exchange plugin.  

Is the work going on this plugin to get this working.  Is it a lost cause?  I hope not as OWA/citrix that we have at the momment - really are not great at all...

---

### Post by Kobalt on 2009-03-17
"Exchange 2007/MAPI Connector" is on the Gnome 2.26 RoadMap, but as fas as I have tested, with our Exchange 2003 server, it is still not working (authentication troubles).

---

### Post by beefcurry on 2009-04-15
No luck with evolution in jaunty.

---

### Post by mr_raider on 2009-04-25
I was able to connect to my exchange server for the first time with jaunty. I'm pretty sure it's a 2007 exchange server:

[https://exchange.mcgill.ca](https://exchange.mcgill.ca)

---

### Post by beefcurry on 2009-04-25
Did you do it from Evolution and did you manage to sync your calender/tasks/ and everything else?

---

### Post by mr_raider on 2009-04-25
Calendar tasks and contacts. Not memos.

---

### Post by mr_skater99 on 2009-04-26
I've just upgraded at work to 9.04 - and WOULD LOVE to get away from citirx.

Can you talk us through what you did to get this set up with evolution?

Cheers

---

### Post by mr_raider on 2009-04-26
I ran the upgrade from 8.10 to 9.04.

Start evolution. Created new account as exchange server type, and set my OWA address (https) as exchange server address, put in the username and password, click autheticate, and voila.

---

### Post by mr_skater99 on 2009-04-27
I tried that - and i still get the message saying exchange 5.5 isnt supported.

Has anyone else tried this?

---

### Post by mr_raider on 2009-04-27
Sorry. I believe Jaunty added support for exchange 2007. Not 5.5.

---

### Post by mr_skater99 on 2009-04-27
Aren't 2007 and 5.5 the same thing?

---

### Post by mr_raider on 2009-04-28
In that case, try installing the evolution-mapi plugin is synaptic and connecting with an exchange mapi account.

---

### Post by mr_skater99 on 2009-04-28
Thanks, I tried this.

Fill out all my details on the account tab and hit authenticate - put in my password, get a spike in disk and then evolution crashes.

Its consistent....

---

### Post by mr_skater99 on 2009-04-28
Looks like i found my issue - just wonder how long this will take to get to ubuntu:

[https://bugzilla.redhat.com/show_bug.cgi?id=493661](https://bugzilla.redhat.com/show_bug.cgi?id=493661)

---

### Post by dugh on 2010-04-07
I see the same issue in Ubuntu 10.04 beta.

Exchange 5.5 not supported by Evolution.

---

### Post by rjgonza on 2010-09-10
So is this still an issue with ubuntu?  I just tried connecting with a freash install of 10.04 and it says that evolution does not support exchange 5.5 :(

---

### Post by ctt1wbw on 2010-10-11
Sorry to bring up an old thread, but just updated to 10.10 last night and I am still getting the same errors.  Is it fixed, am I doing something wrong here?

I use Mail2Web as my only email and they run Sever 2007 and Evolution won't support this.

---

### Post by ibizatunes on 2010-10-11
exchange 5.5 is end of life, there is never going to be support for it, you need to upgrade your exchange server to a newer version

[http://en.wikipedia.org/wiki/Microsoft_Exchange_Server](http://en.wikipedia.org/wiki/Microsoft_Exchange_Server)

evolution should support exchange 2007
[http://en.wikipedia.org/wiki/Evolution_(software](http://en.wikipedia.org/wiki/Evolution_(software))

---

### Post by frncz on 2010-10-11
I also cannot get exchange to work (Ubuntu 10.10 64). After installing evolution-mapi, I get more options, but evolution crashes after entering my password when it tries to authenticate the connection with the server.

---

### Post by rjgonza on 2010-10-11
From what I understand, we are still outta luck.  I hope someone can prove me wrong soon.

---

### Post by paulphillips on 2010-10-19
I can confirm that evoltuion-mapi plugin works, but this requires direct access to the exchange server (not the OWA server).  For me - this means a VPN. 

Evolution-exchange does not work for me also in 10.10.

OWA access appears to only be possible from a browser.

---

### Post by pfilias on 2010-10-21
I am running Ubuntu 10.04 and am using the evolution-mapi extension. 

[LIST]
[*]When I first connected, I was able to open e-mail messages, but they would take a few seconds to open. 

[*]My calendar was synced, but my contacts weren't for some reason.
[/LIST]

Now I'm just bummed this isn't working for me. I'd love to :guitar: Ubuntu during the day, when I had the urge to escape Windows XP.

---


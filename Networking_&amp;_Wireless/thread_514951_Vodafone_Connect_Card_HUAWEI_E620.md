---
title: "Vodafone Connect Card HUAWEI E620"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by lynx75 on 2007-08-01
Hello All, 

  I've got some problem with my Vodafone Connect Card HUAWEI E620 with Ubuntu 7.04.

First of all I'm a brend new user in linux, but I'm following the procedures linked below :
	
[http://www.tuxjournal.net/?p=318](http://www.tuxjournal.net/?p=318)
[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

First step :
sudo apt-get install python-dbus python-twisted python-serial python-glade2 python-pysqlite2 wvdial nozomi-source python-notify python-gnome2-extras

With the command above linux installed the packages without any problem.

Second step:
sudo python setup.py install

When I've lauched the command above the follows error appears : can't open file 'setup.py': [Errno 2] No such file or directory.
Infact, setup.py is not exists in any part of the hard drive.
 
Step 3:
Ok, however I've downloaded the vodafone mobile drivers under the link below and installed it.

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

I've inserted my vodafone connect card and launched the program(drivers) under application, internet , but nothing happen :-((( .

I've checked the log but I cannot understand very well what's happen, but however something happen , but my 3g card is still not working.

If you need further information, I'm very please to give you in order to help me (us) to fix the problem. But please explain what I must do, because it's my first time with linux as well.

Thank you in advance, 
Marco

---

### Post by lynx75 on 2007-08-02
I'm "fighting" with this problem, Is there someone who help me, please ???

thanks

---

### Post by Kosimo on 2007-08-02
Hmm..
I'm using it..

That's the way I did:

Download the Vodafone Mobile Connect Card:

Install it.

Run it..

Oh,  I forgot to connect the usb modem!

Closing the program

Connecting the USB modem, 

Open the Vodafone Mobile Connect Card again

Hit Connect..

And surf ;)


(I'm on feisty completely updated)

I didn't install any driver..

---

### Post by lynx75 on 2007-08-02
Many thanks for you message.

Did you downloaded the program from the link below?

[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=11](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=11)

and the file name is :

- vodafone-mobile-connect-card-driver-for-linux_0.9.7.3_feisty_all.deb

I am try to do a new fresh Ubuntu installation with the lastest update and install only the program downloaded above.

Fingers cross :-)))

thnaks
lynx

---

### Post by Kosimo on 2007-08-02
> **lynx75 said:**
> Many thanks for you message.

Did you downloaded the program from the link below?

[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=11](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=11)

and the file name is :

- vodafone-mobile-connect-card-driver-for-linux_0.9.7.3_feisty_all.deb

I am try to do a new fresh Ubuntu installation with the lastest update and install only the program downloaded above.

Fingers cross :-)))

thnaks
lynx



Yes, that was the one ;)

I'm sure you'll do it :P

---

### Post by lynx75 on 2007-08-02
Nothing to do.

I've just re-installed my Ubuntu, updated everythings , downoaded the VOdafone Mobile connect software but does't works..........

If I launched the Vodafone Mobile connect software without my connect card the program was opened, but the connect card is inserted into the pcmcia slot nothing happenz....

My laptop is an HP nc6220....

Any ideas, pleasE? 

thanks
lynx

---

### Post by Kosimo on 2007-08-02
> **lynx75 said:**
> Nothing to do.

I've just re-installed my Ubuntu, updated everythings , downoaded the VOdafone Mobile connect software but does't works..........

If I launched the Vodafone Mobile connect software without my connect card the program was opened, but the connect card is inserted into the pcmcia slot nothing happenz....

My laptop is an HP nc6220....

Any ideas, pleasE? 

thanks
lynx

I really have no answer about is.. :( Sorry.. I was using the USB version by the way...

---

### Post by lynx75 on 2007-08-02
many thanks Kosimo... I hope that someone can help me as, well.


In any case I'm use the PCMCIA version...

please....help me

thanks

---

### Post by aldobenart on 2007-08-02
:(
I'm having a very similar problem un kubuntu feisty on acer travelmate 4230.

I'installed vodafone drivers and they recognize my PCMCIA card, but the only thing happening is the word connecting .... in the bottom left corner of the GUI.

However, I can't understand what Kosimo means with "connecting the USB modem". My E620 is a PCMCIA card.

I'm in Italy. Have I to configure anything before running Vodafone GUI?

Thanks in advance.
Orpilda

---

### Post by lynx75 on 2007-08-02
Vodafone provide 2 different connections:

- One with the PCMCIA card model E620,

- & another one with USB box model E220 .

 I live in Italy as well (milano) and you don't need to configure anything, I suppose. 

I can't understand when I launched the Vodafone Mobile connect software without my connect card the program was opened, but when I've connected the card into the pcmcia slot nothing happenz.

In my case the software do not recognize the vodafone card.

IS THERE SOMEONE WHO HELPS US, PLEASE???

Otherwise I must use, shhh windows xp...

thanks
lynx

---

### Post by Divan Santana on 2008-06-20
simply install the vodafone "official" software from:
[https://forge.betavine.net/frs/?group_id=12&release_id=11](https://forge.betavine.net/frs/?group_id=12&release_id=11)

I used the 2.0 beta3 and it worked on a few laptops I tried! :)

---


---
title: "HElp to connect Reliance CDMA Modem"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by jagaprakash on 2009-07-31
How to connect the Reliance CDMA Modem in Ubuntu 9.04?
any one help me plz.........

---

### Post by r.v.the.evil on 2009-07-31
i have got tata indicom plug 2 surf
and i am not able to connect on ubuntu 9.04(still)
but one thing is for sure u have to install wvdial first
and configure it.
and remaining i will wait with u for other replies

---

### Post by GeorgeVita on 2009-07-31
Hi **r.v.the.evil**,

you have an answer waiting:

> **GeorgeVita said:**
> Hi **r.v.the.evil**,
if you have an active internet connection on your Ubuntu PC this should work. Try also the System > Administration > Synaptic Package Manager and find it to packages, choose **wvdial** to install.

If you do not have an internet connection you must follow instructions from my previous post (download to another PC, copy to a usb mem and install all 5 .deb packages).

Read also: [http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)
Regards,
George

If your problem is the missing wvdial read: [http://ubuntuforums.org/showthread.php?t=846522](http://ubuntuforums.org/showthread.php?t=846522) or the link at my signature.

Regards,
George

---

### Post by r.v.the.evil on 2009-07-31
i have wvdial configuered onterminal linux
and internet startsworks on terminal and it is shown on the modam
but how can i use this internet on mozzila firefox. please tell me about linux terminal commands also

---

### Post by Liolikas on 2009-07-31
Just start firefox and use internet. You do not have to setup something more on Firefox.

---

### Post by r.v.the.evil on 2009-07-31
but its not working there

---

### Post by sonu 1807 on 2009-07-31
check... if firefox is set to run offline in File menu... can u run update? from System --> Administration --> Update manager

---

### Post by r.v.the.evil on 2009-07-31
ok bro now i m using vista for internet
and iw il reboot my computer
to chek that mode
but according to my opinions
the applet application on task bar shows no conections
might be any other problem
please give me a quick reply for this and subscribe this thread 
so can i take your further help may be tomorrow or another day
well thanks 
ravi kumar

---

### Post by Liolikas on 2009-07-31
Paste contents of /etc/wvdial.conf here.

---

### Post by sonu 1807 on 2009-07-31
Actually in wvdial...the network manager shows offline.... You can connect using network manager too...just click it and then click Auto Mobile CDMA connection...it would not first work...and give you a message that its offline.... then right click it and go to edit connections...in edit connection choose mobile broadband...then click edit ...puch in the number (by default it is #777) and your username and password...after setting it up you can simply click Auto CDMA connection to go online....

---

### Post by r.v.the.evil on 2009-07-31
[driver defaults]
usb modem
phone = #777
username = internet
password = internet
remaining are written as it is
i have configured this file
and
starts it by wvdial command
and modem lights starts blinking
it only blinks when internet is started
i also dont know much about terminal
a take a week to install and download wvdial
hence u can understand my knowledge about ubuntu

---

### Post by Liolikas on 2009-07-31
Install something without internet on Ubuntu is really problematic.
Double check that you password really is internet.

So then write command:

```

sudo wvdial

```
and paste output here.

---

### Post by sonu 1807 on 2009-07-31
in wvdialfile add one more line 

Stupid Mode = 1

If you right click network manager... it will open up a network connection window ...in mobile broadband tab click add... a connectionn assistant will be there...go forward..choose tata indicom plug 2 surf...it will work automatically....u may have to edit it for ur username and pswd...during installation if you had not chosen india as your location then you have to choose india in assistant

---

### Post by r.v.the.evil on 2009-07-31
thanks   well it was the work offline error in the browser which i have fixed it now i am connected on ubuntu and the problem is solved
thanks to
george vita , sonu and liolikas
again for this
the owner of this thread might regard it as solved for me

---


---
title: "Connecting to Fermilab's Network with Ubuntu"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by Dr Gonzo on 2007-06-27
I'm posting this because I figured out how to do it, and for a long time, I had wished that somebody would post about it.

For those of you who are wondering why you'd want to do this, I work on the CMS experiment at the Large Hadron Collider at CERN.  To work on our software, we sometimes have to connect to an analysis farm at Fermilab in Batavia, Illinois.  They use Kerberos and a kerberized version of ssh.  Until Feisty, I was unable to get this working under Ubuntu.  I was having to work from the Scientific Linux workstation I have at work, and I really prefer working in Ubuntu.

Of course, to do this you have to have Fermilab security credentials.

So, the first thing to do is install the right version of ssh.
```
apt-get install ssh-krb5
```
I'm fairly sure that it will install kerberos 5 along with it by default.  This used to replace the regular version of ssh with a special one that replaced the default ssh, but they've now rolled a lot of the fixes into the normal version.  So, this is now a transitional package that simply alters some config files to make it play well with Kerberos.  No major changes to your system, and normal ssh connections function fine.

Next, you'll need to edit /etc/krb5.conf to work with the FNAL.GOV cell.  [This is where I found the configuration file.](http://www.fnal.gov/docs/strongauth/krb5conf.html)  I just copied the template into /etc/krb5.conf after moving the default to /etc/krb5.conf.default.

Once all of that's done, you should just be able to get your kerberos ticket and connect to the computers you want.  I usually connect to the CMS UAF.  To connect to an SLC3 machine, you just do```
ssh cmsuaf.fnal.gov
```  For later software releases and an SLC4 machine, do```
ssh cmslpc.fnal.gov
```

Hope this is useful to somebody.  It would have been to me!

[Here's some info about CMS computing.](http://www.uscms.org/SoftwareComputing/index.html)

---

### Post by d0.fnal on 2008-02-03
Thank you,

I was looking for this info before trying (U/K)ubuntu. I will try your recipe and give you my feed back soon.
This is what I really love about Linux...you find the answer to your questions sometimes even before you ask your question.

D0

---

### Post by **martha** on 2008-05-18
Thank you!

I have just installed kerberos on my Ubuntu 8.04 and your recipe worked perfeclty, except that the krb5-user was not installed within the dependencies. So I did 

sudo apt-get install krb5-user

and that was it. That was really useful. Thank you again.

---

### Post by astronomy88 on 2008-07-15
Thanks Dr Gonzo, this message was a Godsend. I spent all of yesterday and most of today trying to log onto Fermilab with Ubuntu 8.04. I'm so happy you took the time to post your findings, as I was rapidly losing faith in myself and my OS.

---


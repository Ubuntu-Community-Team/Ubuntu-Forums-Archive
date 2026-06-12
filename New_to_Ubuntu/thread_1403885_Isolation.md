---
title: "Isolation"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by MaryO on 2010-02-10
Greetings,

I use my laptop for web surfing and email while I use a separate netbook for online banking.  Someone told me that this wasn't necessary.  He said that I could achieve the same level of security by running another operating system from a CD.  He said to use one operating system for web surfing and the other just for the online banking.  If I get malware that compromises my security in one operating system, the other still won't be affected.

Is this true?  Also, will I achieve the same level of security if I run ubuntu off of a flashdrive?  

I figured out how to run ubuntu on my netbook off of a flashdrive, but I can still 'see' the Acer harddrive in ubuntu's version of Explorer.  That makes me wonder how secure it is.

Thanks,
Mary

---

### Post by halitech on 2010-02-10
I've been using online banking from my everyday machine for years and never had a problem. If you are that insecure about online banking then my suggestion would be not to use online banking period.

---

### Post by nhasian on 2010-02-10
[The Washington Post]("http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html") advises people to use linux instead of windows to do online banking.  If you are already using Ubuntu, then you dont need to worry about booting off a liveCD.  You can install Ubuntu side by side with Windows so you can choose which one to boot when you turn your computer on.  instructions are here:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

you should read this as well:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by NightwishFan on 2010-02-10
Anyone can get into a local harddrive from a live system. Just keep your machine out of arms reach of anyone that might want to steal information. I am willing to bet your online banking uses end to end encryption, which should keep anyone from passively collecting it over the web. I think you are fine.

---

### Post by sandyd on 2010-02-10
> **NightwishFan said:**
> Anyone can get into a local harddrive from a live system. Just keep your machine out of arms reach of anyone that might want to steal information. I am willing to bet your online banking uses end to end encryption, which should keep anyone from passively collecting it over the web. I think you are fine.

+1
As long as no one has physical access to your computer, ubuntu should be more than adequate for your security/banking needs.

just make sure that you type your password/username on a non-pishing site....

---

### Post by NightwishFan on 2010-02-10
If you use Firefox, you can mouse over the logo directly to the left of the web address to view Encryption/Signing information. That should verify if your activities with the page are encrypted.

---

### Post by MaryO on 2010-02-10
Thanks so much for answering.

I know the banks encrypt the communication between my computer and theirs, so I'm not worried about that.  What I'm concerned about is keylogging malware. I surf the web and use email a lot.

I'm hardly rich; but I'm frugal, and if I lost what I had, it would really, really hurt.  Actually, it's my retirement accounts that I'm most worried about. 

It sounds to me as if you guys haven't heard of what I'm talking about.  I don't know much about computers, so maybe I'm worried about nothing.

---

### Post by NightwishFan on 2010-02-10
I doubt someone could keylog you if they can't get on the root account.

---

### Post by MaryO on 2010-02-10
> **nhasian said:**
> [The Washington Post]("http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html") advises people to use linux instead of windows to do online banking.  If you are already using Ubuntu, then you dont need to worry about booting off a liveCD.  You can install Ubuntu side by side with Windows so you can choose which one to boot when you turn your computer on.  instructions are here:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

you should read this as well:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Didn't know that.  Thanks!

---

### Post by halitech on 2010-02-10
in order to keylog you, they would either need 1) physical access to your hardware to install either a hardware keylogger (which you would see) or install software (which they would need your user account info for) or 2) port forwarding set up on your router (if you have 1) or the built in firewall set up with a hole in it (unlikely unless you played around with it) plus your user account info to log in.

---

### Post by halitech on 2010-02-10
> **NightwishFan said:**
> I doubt someone could keylog you if they can't get on the root account.

wouldn't need the root account, any account with sudo rights would do

---

### Post by NightwishFan on 2010-02-10
That is what I meant.

---

### Post by MaryO on 2010-02-11
> **NightwishFan said:**
> Anyone can get into a local harddrive from a live system. Just keep your machine out of arms reach of anyone that might want to steal information. I am willing to bet your online banking uses end to end encryption, which should keep anyone from passively collecting it over the web. I think you are fine.

I think this answers my question.  Thanks.

---


---
title: "Virus??"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by hopkinsjeni on 2010-07-19
Now I know linux doesn't have virus's as such but a fee have my friends have been saying that once they've downloaded attachments I've sent them to windows from linux they are having virus trouble. 
Is there a way I can check for files that may be causing this and delete them? I am a complete beginner in regards to bugs and bug checking so any help possible would be greatly appreciated.

---

### Post by jerenept on 2010-07-19
You cannot get a Windows virus in Ubuntu, however the files containing the virus are still harmful to Windows users. You should scan them with ClamAV or Avast!, both of which have Linux variants.

To install ClamAV, you can use the Software Centre and search for "Virus Scanner" or open a terminal and type
```
sudo aptitude install clamtk
```

then type your password.

---

### Post by Paqman on 2010-07-19
There are antivirus products for Linux that will check for Windows viruses. ClamAV is in the repos, but it's not terribly good. I'd recommend [Avast]("http://www.avast.com/linux-home-edition").

---

### Post by hopkinsjeni on 2010-07-19
Thanks guys that's super helpful, I shall get one of those installed right away

---

### Post by fallenshadow on 2010-07-19
I would recommend Bitdefender... its very easy to use and super fast for scanning.

[http://www.bitdefender.com/world/business/antivirus-for-unices.html](http://www.bitdefender.com/world/business/antivirus-for-unices.html)

You just need to request a free license on the right hand side of the page. (its free for personal use)

---

### Post by WRDN on 2010-07-19
I've used ClamAV in the past for this purpose, and it has been fine. One thing to note however, is that, you should probably get an **on-demand** virus scanner, so it won't be constantly eating up system resources.

---

### Post by 3rdalbum on 2010-07-19
Firstly, Windows users sometimes attribute ANYTHING out of the ordinary to viruses.

Secondly, these e-mails might not be coming from your computer at all; they might be coming from someone else's virus-infested computer, being sent to your friends under the guise of being from your e-mail address. Viruses do this, sometimes.

Thirdly, although it's possible to attach a Windows virus to an e-mail on Ubuntu and literally send it to your friends, it's impossible for that virus to actually attach ITSELF to the e-mail. Unless it was paired up with a Linux virus - and no such pairing is known to exist. In fact, no Linux viruses are known to exist in the wild at the moment.

---

### Post by jerenept on 2010-07-19
> **3rdalbum said:**
> Firstly, Windows users sometimes attribute ANYTHING out of the ordinary to viruses.

Secondly, these e-mails might not be coming from your computer at all; they might be coming from someone else's virus-infested computer, being sent to your friends under the guise of being from your e-mail address. Viruses do this, sometimes.

Thirdly, although it's possible to attach a Windows virus to an e-mail on Ubuntu and literally send it to your friends, it's impossible for that virus to actually attach ITSELF to the e-mail. Unless it was paired up with a Linux virus - and no such pairing is known to exist. In fact, no Linux viruses are known to exist in the wild at the moment.

1) sometimes
2) Not likely
3)True

However it is good practise to scan anything you have downloaded. the Windows users should scan all files downloaded, regardless of whether it came from a trusted person.

---

### Post by Paqman on 2010-07-19
> **WRDN said:**
> I've used ClamAV in the past for this purpose, and it has been fine.

Afraid I don't really share your optimism. 

[http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness]("http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness")

---

### Post by WRDN on 2010-07-19
> **Paqman said:**
> Afraid I don't really share your optimism. 

[http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness]("http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness")

Maybe I'm just lucky then.

Remember though, the best antivirus is the user. Don't go on dodgy sites. Don't download and install dodgy programs etc etc etc.

---

### Post by tarps87 on 2010-07-19
> **3rdalbum said:**
> Firstly, Windows users sometimes attribute ANYTHING out of the ordinary to viruses.

Secondly, these e-mails might not be coming from your computer at all; they might be coming from someone else's virus-infested computer, being sent to your friends under the guise of being from your e-mail address. Viruses do this, sometimes.

Thirdly, although it's possible to attach a Windows virus to an e-mail on Ubuntu and literally send it to your friends, it's impossible for that virus to actually attach ITSELF to the e-mail. Unless it was paired up with a Linux virus - and no such pairing is known to exist. In fact, no Linux viruses are known to exist in the wild at the moment.

> **jerenept said:**
> 1) sometimes
2) Not likely
3)True

However it is good practise to scan anything you have downloaded. the Windows users should scan all files downloaded, regardless of whether it came from a trusted person.

Just a quick comment about your response to the second point, this is definitely possible. Some mail servers enforce correct 'sent' addresses when sending an email however there a some that don't do this and it is quite easy once you have one to use the SMTP 'by hand' to trick it as the sent from address can be set by the sender.
The larger mail providers however employ a validity checker.

---

### Post by Paqman on 2010-07-19
> **WRDN said:**
> Maybe I'm just lucky then.

Remember though, the best antivirus is the user. Don't go on dodgy sites. Don't download and install dodgy programs etc etc etc.

Absolutely.

---


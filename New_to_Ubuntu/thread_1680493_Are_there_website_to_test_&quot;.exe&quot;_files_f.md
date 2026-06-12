---
title: "Are there website to test &quot;.exe&quot; files for Virus or keylogger?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by suomalainen on 2011-02-02
Ubunteros,

Does anyone know a web site where I can upload a .exe file to see if it contains a virus, trojan or even a key logger?


Thank you,

Suomalainen

---

### Post by Frogs Hair on 2011-02-02
I don't see any in my searches . If you know a Windows user with good up to date anti virus/malware you could send it to them for a scan or have them download the same package and scan it.

---

### Post by suomalainen on 2011-02-02
To be honest, I'm also kinds wondering what this .exe file is and if it may be personal info or something.

I thought there was a place online that could scan the file and let me know if it is legit...

---

### Post by SeijiSensei on 2011-02-02
Use [ClamAV]("http://www.clamav.net/"):

```

sudo apt-get install clamav
sudo freshclam
clamscan wonky_program.exe

```

---

### Post by coffeecat on 2011-02-02
Searching for 'online virus scan' in Google quickly found me this:

[http://www.kaspersky.com/scanforvirus](http://www.kaspersky.com/scanforvirus)

I've just tried it in Ubuntu and it happily let me upload a file from Ubuntu to scan.

And you'll all be pleased to know that a .deb file downloaded from the Ubuntu main repository is free of viruses. :)

---

### Post by suomalainen on 2011-02-02
Coffeecat,

This was just what I was looking for! Perfect...This is a link worth book marking!!!!!

Thanks for your support!

---

### Post by luca@ on 2011-02-02
guys, can you help me out 'cause I'm trying to get a way to keep a pssw for make private the reading of QR codes.... thank you:p

---

### Post by stmiller on 2011-02-02
[http://www.virustotal.com/](http://www.virustotal.com/)

---


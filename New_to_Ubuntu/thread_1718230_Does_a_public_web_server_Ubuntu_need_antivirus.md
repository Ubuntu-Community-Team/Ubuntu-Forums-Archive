---
title: "Does a public web server Ubuntu need antivirus?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-03-31
I am going to host a web server with apache, mysql, php setup, of course using ubuntu as the OS. I will directly use port 80. Do I need antivirus?

---

### Post by wolfen69 on 2011-03-31
If windows users are going to be accessing this, it might be a good idea, but I am not an expert in this.

---

### Post by Paqman on 2011-03-31
Nope, not if you're just serving web pages. Securing a server is a very different to securing a desktop, you should read up on server security.

---

### Post by falko on 2011-03-31
If you run an FTP server and want to make sure that nobody can upload malware (so that nobody can download it from your server), it is possible to integrate ClamAV into your FTP server (ProFTPd, PureFTPd).

---

### Post by crispy_420 on 2011-03-31
I always fall on the side of caution and would say yes. Not so much for yourself but also for your clients. It always good to cover yourself from being the source of an infection and maybe the source of liability. But this all depends on what you plan on using the box for.

And as mentioned earlier, read up on securing a linux server and apache in general.

---

### Post by dixcuxx on 2011-03-31
> **falko said:**
> If you run an FTP server and want to make sure that nobody can upload malware (so that nobody can download it from your server), it is possible to integrate ClamAV into your FTP server (ProFTPd, PureFTPd).

I wouldn't have FTP and I will just locally access the computer. The only purpose of the computer is opening port 80 and run as a web server and host couple websites.

---


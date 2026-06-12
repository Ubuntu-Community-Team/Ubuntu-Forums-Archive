---
title: "antivirus and firewall"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2010-11-14
Hello, I'm running Ubuntu 10.10 as a duel boot machine alongside Windows 7, I know peoiple say Ubuntu has very little malware when compared to the other major operating systems, still I would feel safer if I had an antivirus/antimalware program.

Anyone know of a good antivirus and where I can get it? Also, what is a good firewall for Ubuntu? 

Thanks

---

### Post by Rave Gloves on 2010-11-14
Go to Applications>ubuntu software centre.  Type in "Firewall Configuration" Download that package.

For Anti Virus i have no idea which one is good, i have never set one up, Im actually guilty of not setting up a firewall, which i know is bad :P

---

### Post by Paqman on 2010-11-14
> **skyzthelimit230 said:**
> 
Anyone know of a good antivirus and where I can get it? 


Avast has a Linux version. However, none of the available antivirus products will actually make Linux any more secure. They search for Windows viruses. All known Linux threats are patched through your normal updates, so there's nothing for them to secure.

> 
Also, what is a good firewall for Ubuntu? 


Ubuntu ships with no services listening on any ports, so enabling a firewall wouldn't make it any more secure. If you install any server packages then a firewall is a good idea. There's actually one called ufw built in, it's just not turned on by default. Install the package Gufw if you want a tool to manage it.

---

### Post by uRock on 2010-11-14
Hello and welcome to the forums.

Please read the [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread. It will explain a lot of your questions about how ubuntu's security works.

---

### Post by sisco311 on 2010-11-14
EDIT: never mind... :)

Welcome to the forums!

---

### Post by skyzthelimit230 on 2010-11-17
Thanks everyone

---


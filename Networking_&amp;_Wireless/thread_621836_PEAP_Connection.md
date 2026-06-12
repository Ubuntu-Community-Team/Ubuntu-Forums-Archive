---
title: "PEAP Connection"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by dudumomo on 2007-11-24
Hello
I want to know how can i connect my laptop on the connection of my university.
It's a PEAP connection with Login, pass and domain. I find in network manager, PEAP but without domain.

I have Gutsy with an Intel 3945 a/b/g.

And i have 2 differents connections, 1 in my university in PEAP and one other at home (WPA and config with IP,Sub mask,DNS...) If you know how can I switch easily between this connections

Thanks for your help !

---

### Post by dudumomo on 2007-11-25
Up Up:mrgreen:

---

### Post by wieman01 on 2007-11-26
Maybe WICD is an option for you:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by dudumomo on 2007-11-26
I tried wicd, it's good for change network connection ! But not for connect PEAP with domain. WICD has not an option for domain....or may be i never see it....

---

### Post by wieman01 on 2007-11-26
Then you can take a look at my WPA tutorial. It's a bit of a pain, because you need to set it up manually by command line. But check it out for testing purposes.

Alternatively, send an email to the WICD team and ask them to implement it. Why not?!

---

### Post by dudumomo on 2007-11-26
Okay i will try !

EDIT :
I send a message in the WICD's forum and i read your WIKI but i never see for PEAP with domain...("Log on to") May be i am blind :p

---

### Post by dudumomo on 2007-11-26
an idea ?

---

### Post by wieman01 on 2007-11-26
Hang on a minute... you enter the domain as part of your user name, don't you? E.g.:
> /my_domain/my_user
Could you try?

---

### Post by dudumomo on 2007-11-27
Good idea !
I remember for read my university's mail, i need to enter mydomain/myname
But i tried with network manager...but it doesn't work.....

---

### Post by wieman01 on 2007-11-27
> **dudumomo said:**
> Good idea !
I remember for read my university's mail, i need to enter mydomain/myname
But i tried with network manager...but it doesn't work.....
It should... if it doesn't, try WICD once again.

---

### Post by dudumomo on 2007-11-27
I tried with WICD but it's the same !
It doesn't work :
I tried "/mydomain/myname" or "mydomain/myname" but no...

Thx for your help !

---

### Post by dudumomo on 2007-11-30
Up up !:)

---

### Post by dudumomo on 2007-12-06
nobody know ?

---

### Post by jazty on 2008-01-31
My college uses a similar system: PEAP authentication requiring domain, username and password.

I think your problem is the slash "/". I can connect if I use "\" instead

I can logon using Network Manager and the following settings:

-- Connect to other wireless network --

Network Name: network_name
Wireless Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
Anonymous Identity: BLANK
CA Certificate: (NONE)
PEAP Version: Version 1
Inner Authentication: MSCHAPv2
User Name: domain\username (NOTE THE ONE SLASH)
Password: password

then click connect and ignore the certificate warning.

It took a couple tries for me to finally connect (possibly due to a weak signal), but it did end up working.

Hope this helps

---

### Post by wieman01 on 2008-01-31
> **jazty said:**
> My college uses a similar system: PEAP authentication requiring domain, username and password.

I think your problem is the slash "/". I can connect if I use "\" instead

I can logon using Network Manager and the following settings:

-- Connect to other wireless network --

Network Name: network_name
Wireless Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
Anonymous Identity: BLANK
CA Certificate: (NONE)
PEAP Version: Version 1
Inner Authentication: MSCHAPv2
User Name: domain\username (NOTE THE ONE SLASH)
Password: password

then click connect and ignore the certificate warning.

It took a couple tries for me to finally connect (possibly due to a weak signal), but it did end up working.

Hope this helps
It does, thank you.

---


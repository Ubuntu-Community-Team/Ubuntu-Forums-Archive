---
title: "ubuntu 10.04 to winXP network problem"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by M93 on 2010-08-24
i've been trying to access my XP desktop shared folders from my ubuntu 10.04 laptop for days and i still cant and i dont know where the problem is
* laptop is connected to the desktop through wireless network
* desktop can find ubuntu in the workgroup members and can access    shared folders
* ubuntu can see 'windows network' but it only displays the ubuntu share folder.

thanks in advance :)

---

### Post by jtarin on 2010-08-24
Have you consulted this documentation?[https://help.ubuntu.com/10.04/internet/C/networking-shares.html]("https://help.ubuntu.com/10.04/internet/C/networking-shares.html")

---

### Post by dtoronto on 2010-08-24
This could also be a windows permission issue, that you may need to add permissions to everyone on the windows machine.  Can you see the windows share on your linux box?

---

### Post by necromonger on 2010-08-24
Here you go.




         [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by M93 on 2010-08-24
> **jtarin said:**
> Have you consulted this documentation?[https://help.ubuntu.com/10.04/internet/C/networking-shares.html]("https://help.ubuntu.com/10.04/internet/C/networking-shares.html")

i did it..but its still

---

### Post by M93 on 2010-08-24
> **dtoronto said:**
> This could also be a windows permission issue, that you may need to add permissions to everyone on the windows machine.  Can you see the windows share on your linux box?

i dont know about permissions but i can see 'windows network' inside it 'WORKGROUP' inside it 'ubuntu'

---

### Post by M93 on 2010-08-24
> **necromonger said:**
> Here you go.




         [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

i am working on it now, seems like i've got problem 3
i hope it works :)

---

### Post by oldsoundguy on 2010-08-24
In simple terms, you have to go to the XP box, open it up, open the control panel and set up the network via the wizard.
Then you have to select what you want to share .. files/folders etc and go to each of them .. right click and select properties and then sharing.
In my case I had whole second and external drives and share the ENTIRE content.

While you are at it .. start>settings>printers and faxes and grant print sharing there.

---

### Post by M93 on 2010-08-24
> **oldsoundguy said:**
> In simple terms, you have to go to the XP box, open it up, open the control panel and set up the network via the wizard.
Then you have to select what you want to share .. files/folders etc and go to each of them .. right click and select properties and then sharing.
In my case I had whole second and external drives and share the ENTIRE content.

While you are at it .. start>settings>printers and faxes and grant print sharing there.

yes yes yes....IT WORKED!!
this forum is gr8 n fast i should have came here ever since i had that problem...THANK U ALL! :D

---


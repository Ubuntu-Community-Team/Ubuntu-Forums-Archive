---
title: "Lan"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Darkblizz on 2007-10-04
K so i have just a normal LAN setup at my house and I can access my windows files from linux but my problem is getting on my linux box.  I type in the ip address and it brings up a login box i try and log in and i dunno what it wants cuz i type my user name/pass and it doesnt work! Help!


Darkblizz - The UBuntu NoobY ;)

---

### Post by Cryptog on 2007-10-04
How are you trying to connect to your linux box?  I suggest using putty (available for windows) to connect via ssh. You will have to have openssh-server installed first (apt-get install openssh-server) for it to work.

---

### Post by rickyjones on 2007-10-04
> **Darkblizz said:**
> K so i have just a normal LAN setup at my house and I can access my windows files from linux but my problem is getting on my linux box.  I type in the ip address and it brings up a login box i try and log in and i dunno what it wants cuz i type my user name/pass and it doesnt work! Help!


Darkblizz - The UBuntu NoobY ;)

Are you trying to access the Linux computer in terms of filesharing? As in, you browse your network shares from Windows and when you connect to the Linux computer it prompts for a username/password?

If so then try using the same username/password that you use when you login to the Linux system. 

-Richard

---

### Post by Darkblizz on 2007-10-04
Yes i am trying to just connect using a browers and it does prompt me to login but when i use my username / password it doesnt let me in ! so bascially it's not letting me do that :(

---

### Post by rickyjones on 2007-10-04
I'm no SAMBA expert but I think you need to add your user account on the Linux computer to the SAMBA users database.

I want to say the command is as follows:
```
sudo smbpasswd user
```
Replace "user" with your Linux username. It'll prompt you to set the password at that point.

Give that a try :)

-Richard

---

### Post by Darkblizz on 2007-10-04
THANKS that worked just great !!!!

<3 Ubuntu forums :)

---

### Post by rickyjones on 2007-10-04
You're welcome. I'm glad it worked for you.

-Richard

---


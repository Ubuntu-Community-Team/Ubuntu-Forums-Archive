---
title: "VNC server?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Nerflander on 2011-03-24
I dont know how this works , but i need to be able to remote to my ubuntu server whenever i want... even if there is another person logged in or even when the user is logged of for example... with the standard stuff that doenst works...

anyone knows a solution?

---

### Post by bluefrog on 2011-03-24
ssh

---

### Post by Nerflander on 2011-03-24
Alright , did a bit of googling and you are saying that if i install openssh server etc configure it , i should be always able to remote to the server unless its off or other obvious things.

---

### Post by Grenage on 2011-03-24
If you're happy with just a terminal, ssh will indeed do you just fine.  If not, then VNC is an option; I'd personally opt for freenx over VNC.

---

### Post by Nerflander on 2011-03-24
Ye i know the vnc part , but to make this happen i must install the openssh server? or else where not getting anywhere:P

---

### Post by deconstrained on 2011-03-24
> **Nerflander said:**
> Ye i know the vnc part , but to make this happen i must install the openssh server? or else where not getting anywhere:P
VNC is in general a very insecure service to have running. It's way more secure if you tunnel it over SSH. SSH has a track record of being quite secure, provided it's configured correctly. You want the connection to be secure if you're going to be using it remotely.

---

### Post by Nerflander on 2011-03-24
Very true. I will instal the openssh then.

But thats terminal mode only isnt it? Is there a way to have it the same as RDP in windows?

---

### Post by Grenage on 2011-03-24
> **Nerflander said:**
> Ye i know the vnc part , but to make this happen i must install the openssh server? or else where not getting anywhere:P

No, openssh is not required for VNC; as mentioned, you can tunnel it.  The reason I recommend freenx is that it utilizes SSH and is very responsive.

---

### Post by Nerflander on 2011-03-24
Hmhk... getting bit confused...

So lets sum this up!

With the SSH i cant get in my server anytime? even when its at the login screen?

With VNC atm i cant. I am working from a vista machine at my work enviroment. And i use VNC viewer to get in the linux server. But i cant when its at the login screen and it seems not to be capable of handeling multiple remote connection? 

All i want is acces 24/7.. Im leaving the company so the other it man has absolutely no experience in this so im creating a manual so he can login at request but if the previous user didt log of normally you have to walk to the server and login correctly. And that is not the way remote sessions should work.

Maybe this sheds more light in the problem.

---

### Post by Grenage on 2011-03-24
> **Nerflander said:**
> Hmhk... getting bit confused...

So lets sum this up!

With the SSH i cant get in my server anytime? even when its at the login screen?

With VNC atm i cant. I am working from a vista machine at my work enviroment. And i use VNC viewer to get in the linux server. But i cant when its at the login screen and it seems not to be capable of handeling multiple remote connection? 

All i want is acces 24/7.. Im leaving the company so the other it man has absolutely no experience in this so im creating a manual so he can login at request but if the previous user didt log of normally you have to walk to the server and login correctly. And that is not the way remote sessions should work.

Maybe this sheds more light in the problem.

Try freenx, it's free and will do what you want; their website has install instructions and Windows clients available.  If you don't need a GUI, then just use ssh on its own - that will also work fine, regardless of logons.

---

### Post by Nerflander on 2011-03-24
Ok , il work with that advice first then :) 

If i enocunter more problems or anything il let you know. For now il see what i can do with this !

thanks :)

---

### Post by Nerflander on 2011-03-24
Thanks all FreenX did the job!

---

### Post by Grenage on 2011-03-24
> **Nerflander said:**
> Thanks all FreenX did the job!

Peachy!

---


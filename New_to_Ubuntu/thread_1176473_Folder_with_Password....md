---
title: "Folder with Password..."
date: 2009-06-02
forum: New to Ubuntu
---

### Post by penguin-of-doom on 2009-06-02
Hey,
Is there a program for Debian that I could protect my folder that nobody can get into? I know the administrator can go everywhere, but I am the administrator ^^ so how can I protect a folder with a password?

regards,
penguin-of-doom

---

### Post by Shpongle on 2009-06-02
try true crypt , if you wanna hide something that will definately do the trick!! ;)

---

### Post by Celauran on 2009-06-02
You could also just change the permissions on the directory to 0700.

---

### Post by unutbu on 2009-06-02
Ecryptfs is another option:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by aysiu on 2009-06-02
> **Celauran said:**
> You could also just change the permissions on the directory to 0700.
That doesn't really work, as anyone can boot a live CD or boot into recovery mode and see the file or change its permissions.

Encryption is the only way. I also highly recommend TrueCrypt.

---

### Post by bodhi.zazen on 2009-06-02
> **aysiu said:**
> encryption is the only way.

+1

---

### Post by Celauran on 2009-06-02
> **aysiu said:**
> That doesn't really work, as anyone can boot a live CD or boot into recovery mode and see the file or change its permissions.
Wow. I suddenly hate live CDs.

---

### Post by penguin-of-doom on 2009-06-02
Is it also possible that I could create the folder as root and then nobody else can see the content of it? That I could set rights only for me. Is that possible? I think that's easier than all the programs. I do not understand the English-Text of the Tutorial. I'm not so good at english ^^ But thank you for your answers!

regards,
penguin-of-doom

---

### Post by Celauran on 2009-06-02
> **penguin-of-doom said:**
> Is it also possible that I could create the folder as root and then nobody else can see the content of it? That I could set rights only for me. Is that possible? I think that's easier than all the programs. I do not understand the English-Text of the Tutorial. I'm not so good at english ^^ But thank you for your answers!

regards,
penguin-of-doom

No, they're right about the LiveCD. I had completely overlooked that. You can set the permissions to whatever you like and it won't matter -- LiveCDs can mount local filesystems and thus anyone booting your machine with a LiveCD will gain root access, defeating the restrictive permissions. Encryption really is the only option. That or removing your CD drive :P

---

### Post by penguin-of-doom on 2009-06-02
ok =) Then I will try to translate the tutorial ^^ thanks for your answers!

regards,
penguin-of-doom

---

### Post by macvr on 2009-06-16
@ aysiu
Hi,
seems my comment was deleted! from the thread>  Folder with Password...

since you had replied before me, i presume it was you... 

I'd like to know how my solution is different from the solution others have given, to change the user permissions? instead of using the terminal , i have created the launcher.

What the technical well versed staff dont seem to understand... is that encryption is not very essential to home users like me. I dont have any incriminating materials which i need to encrypt, so dont many users.

The basic need is to lock the folders by changing the permissions , so that when friends pop by to use the system , i dont have to be rude and say wait, i'll log you in as a guest user...

Well it is not perfect but enough. Just a temporary block.

And the user is informed about the method , so he surely knows what he wants...! Why do his choices have to be curbed?

---


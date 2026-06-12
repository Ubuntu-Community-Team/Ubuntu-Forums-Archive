---
title: "to hell with sudo"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by degarb on 2010-02-02
One week in to sucessful install and I have had enough with sudo etc.  Every time I turn around, I cant do this or that, because of permissions.  I cannot even unzip a file cause it is saying I don't have permission.   Is there some way of totally and permanently disabling this stupid sudo and gksudos?   

I don't care why they are there, I just want them off.   I will shoot anyone unauthorized not touching computer, I don't need anything more unless I add it.

---

### Post by Merk42 on 2010-02-02
There is, but sudo is there in Linux by design and I believe telling people how to get around it is against forums rules.

**However** you shouldn't need SUDO simply to unzip something.  Unless you're not unzipping to your home folder, in which case why aren't you?

---

### Post by niffcreature on 2010-02-02
sounds like there is something abnormal going on. i have never had to type in a password while unpacking an archive. unless the archive has a password. 
i dont think theres enough info to know whats going on tho.
you can make it log in automatically quite easily, im sure you probably already know that though.

maybe try typing "id" in a terminal windows and posting the results.

---

### Post by degarb on 2010-02-02
The extractor is so broken, and entire security scheme is so broken that I cannot even extract a file to home/user/ttffont.  Hell  am the user!  I am sure you all have some stupid command line involving sudo to extract this.   but using a commandline on a typical task, performed every few minutes by some linux user, is pure stupidity/laziness/ or just not primetime on the part of the developers.

---

### Post by Natty Dreed on 2010-02-02
you will get used to it

i hate it, but it's protect me ;)

it's only 4 letters ;)

---

### Post by SuperSonic4 on 2010-02-02
> **Merk42 said:**
> There is, but sudo is there in Linux by design

Nope, sudo is there in Ubuntu (and it's derivatives) but not with any other distro. Suse, Fedora, Mandriva, Arch and Slackware all enable the root account. I believe debian does too. I prefer having a root shell open but that's not allowed to be told here, probably to protect new users from themselves

Anyway, the OP is more bothered about having to be root to extract fonts

---

### Post by Natty Dreed on 2010-02-02
> **degarb said:**
> The extractor is so broken, and entire security scheme is so broken that I cannot even extract a file to home/user/ttffont.  Hell  am the user!  I am sure you all have some stupid command line involving sudo to extract this.   **but using a commandline on a typical task**, performed every few minutes by some linux user, is pure stupidity/laziness/ or just not primetime on the part of the developers.

just right click on it

---

### Post by lykwydchykyn on 2010-02-02
> **degarb said:**
> The extractor is so broken, and entire security scheme is so broken that I cannot even extract a file to home/user/ttffont.  Hell  am the user!  I am sure you all have some stupid command line involving sudo to extract this.   but using a commandline on a typical task, performed every few minutes by some linux user, is pure stupidity/laziness/ or just not primetime on the part of the developers.

Before assuming that the developers are drooling idiots, could you entertain the possibility that something is wrong on your system, that maybe being a completely new user you've done something incorrectly, or that you don't really need sudo to do whatever it is you're doing?

What exactly are you trying to do?

---

### Post by Merk42 on 2010-02-02
> **degarb said:**
> The extractor is so broken, and entire security scheme is so broken that I cannot even extract a file to home/user/ttffont.  Hell  am the user!  I am sure you all have some stupid command line involving sudo to extract this.   but using a commandline on a typical task, performed every few minutes by some linux user, is pure stupidity/laziness/ or just not primetime on the part of the developers.

Something isn't behaving properly, the Linux security model aside, you should be able to extract something to a folder you made in your own home directory

I suggest doing as niffcreature said and typing id in the terminal and pasting the results

---

### Post by ibuclaw on 2010-02-02
If you are having to use sudo all the time, there is something wrong with the way you are using your system.

I suppose anything up to 5 times a day would seem appropriate if you are still installing/removing/configuring system internals. But ideally a typical user will only get prompted for a password once or twice, if not every other day.

Regards
Iain

---

### Post by aysiu on 2010-02-02
> **tinivole said:**
> If you are having to use sudo all the time, there is something wrong with the way you are using your system. This.

And, as others have indicated, if your system is functioning properly **and** if you know how to use it properly, there's no reason you shouldn't be able to extract archives by just right-clicking and selecting extract here.

If you want to know how to do something (and if you calm down), post a new thread asking politely for help.

In the meantime, this rant thread is closed.

---


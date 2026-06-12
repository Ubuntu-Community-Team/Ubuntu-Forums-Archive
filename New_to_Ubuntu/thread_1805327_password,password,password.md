---
title: "password,password,password"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by don.usilton on 2011-07-15
I'm having a startup issue with ubuntu 11.04. It asks for my password 3 or 4 times before it recognizes it. Can anyone tell me what to do to solve this problem?....Thanks....Don

---

### Post by lisati on 2011-07-15
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by brunolabs on 2011-08-21
> **don.usilton said:**
> I'm having a startup issue with ubuntu 11.04. It asks for my password 3 or 4 times before it recognizes it. Can anyone tell me what to do to solve this problem?....Thanks....Don


Same problem here. Sometimes I need to try 10 to 20 times to login...

:(

---

### Post by fabricator4 on 2011-08-21
> **don.usilton said:**
> I'm having a startup issue with ubuntu 11.04. It asks for my password 3 or 4 times before it recognizes it. Can anyone tell me what to do to solve this problem?....Thanks....Don,

Well, we all have finger trouble from time to time.  You could set the system to automatically log you in when you turn the computer on.  If you do this it's of course important not to forget your password - you'll still need it to do updates and change system settings.

You could also change the password to something that's easier to type. ;-)

There's no known issues with passwords not being recognised by Ubuntu - it's almost always aforementioned finger trouble.

Try logging into a console (ctrl-alt-F1).  Do you still have trouble?

Chris

---

### Post by brunolabs on 2011-08-31
> **fabricator4 said:**
> 
Well, we all have finger trouble from time to time.  You could set the system to automatically log you in when you turn the computer on.  If you do this it's of course important not to forget your password - you'll still need it to do updates and change system settings.

You could also change the password to something that's easier to type. ;-)

There's no known issues with passwords not being recognised by Ubuntu - it's almost always aforementioned finger trouble.

Try logging into a console (ctrl-alt-F1).  Do you still have trouble?

Chris


I also have this problem when password is asked for updates or system settings. In fact, the problem is getting worse, need more tries to login sucessfully.

I can't login correctly through the console as well.

What is this finger trouble and how can I fix it?


Thanks for the help in advance.


PS- Tried a fresh install of 11.04 and the problem continues.

---

### Post by claracc on 2011-08-31
Perhaps your keyboard isn't working properly,  you could try with other keyboard.

---

### Post by dniMretsaM on 2011-08-31
> **brunolabs said:**
> What is this finger trouble and how can I fix it?

Finger trouble is when you hit the wrong keys while typing (or you don't hit a key at all). It basically means typos.

---

### Post by madjr on 2011-08-31
auto login FTW!

as for typos, open gedit (or any text editor) and type in your pass multiple times to see if it matches.

else you have a clear case of FINGER TROUBLE disease/syndrome!

---

### Post by brunolabs on 2011-08-31
Different keyboard same problem.

It's not a typo, trust me. After a few times getting invalid password messages, I press each key gently and slowly. lol

---

### Post by brunolabs on 2011-08-31
> **madjr said:**
> auto login FTW!

I have auto login now. But I still need it for updates and stuff.

As for the typo issue it isn't the case, as you can confirm with this posts.

---

### Post by dniMretsaM on 2011-08-31
Try making a new user account and seeing if the password works with it.

---

### Post by brunolabs on 2011-08-31
> **dniMretsaM said:**
> Try making a new user account and seeing if the password works with it.

Meanwhile I made another fresh install. Password: a (to prevent typos).
Now I cannot login at all. Wrong password message all the time. :( :confused:

---

### Post by madjr on 2011-08-31
hm, seems similar to this issue
[https://answers.launchpad.net/ubuntu/+question/37718](https://answers.launchpad.net/ubuntu/+question/37718)
[https://answers.launchpad.net/ubuntu/+question/37784](https://answers.launchpad.net/ubuntu/+question/37784)

or
[http://forums.v3.co.uk/showthread.php?p=962462](http://forums.v3.co.uk/showthread.php?p=962462)

or this
[http://ubuntuforums.org/showthread.php?t=1719677](http://ubuntuforums.org/showthread.php?t=1719677)

---

### Post by cariboo on 2011-08-31
@brunolabs, can you give us an example of the original password? Not exactly the same but similar.

---

### Post by dniMretsaM on 2011-08-31
Weird. Are you installing from the same LiveCD? If so, download and burn a new ISO. Burn it at the slowest speed to avoid corruption.

---

### Post by brunolabs on 2011-09-01
> hm, seems similar to this issue
[https://answers.launchpad.net/ubuntu/+question/37718](https://answers.launchpad.net/ubuntu/+question/37718)
[https://answers.launchpad.net/ubuntu/+question/37784](https://answers.launchpad.net/ubuntu/+question/37784)

or
[http://forums.v3.co.uk/showthread.php?p=962462](http://forums.v3.co.uk/showthread.php?p=962462)

or this
[http://ubuntuforums.org/showthread.php?t=1719677](http://ubuntuforums.org/showthread.php?t=1719677)

Their solutions don't work with me.


> **cariboo907 said:**
> @brunolabs, can you give us an example of the original password? Not exactly the same but similar.

asd


> **dniMretsaM said:**
> Weird. Are you installing from the same LiveCD? If so, download and burn a new ISO. Burn it at the slowest speed to avoid corruption.

No luck with that as well. :S

---

### Post by brunolabs on 2011-09-01
How can I submit a bug like this to lauchpad? Which application is responsible for this malfunction?

---

### Post by philinux on 2011-09-01
> **brunolabs said:**
> How can I submit a bug like this to lauchpad? Which application is responsible for this malfunction?

Seahorse is the app for passwords and encryption keys in System>Prefs. I'm guessing this is the app that is misbehaving. Open a terminal and use this. Have you got a launchpad ID?

```
ubuntu-bug seahorse
```

---

### Post by brunolabs on 2011-09-01
> **philinux said:**
> Seahorse is the app for passwords and encryption keys in System>Prefs. I'm guessing this is the app that is misbehaving. Open a terminal and use this. Have you got a launchpad ID?

```
ubuntu-bug seahorse
```


Done.

---

### Post by philinux on 2011-09-01
> **brunolabs said:**
> Done.

Great. Can you include a link to the bug report. Someone else can change the status to confirmed, and also click the affects me etc.

---

### Post by brunolabs on 2011-09-01
Launchpad bug report link:

[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/838936]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/838936")

---


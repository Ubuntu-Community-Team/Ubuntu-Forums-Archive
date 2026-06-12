---
title: "expired root account -- need to re-enable"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by th3 mant1s on 2009-04-03
Hi Community,


Okay I KNOW this is against popular suggestion not to have the root account enabled. Now that we have that established and you know that I know what i'm doing I have one simple question...

How do I make this message...


```
[sudo] password for hypernode: 
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)

```

Go Away?

So far I have enabled the root account by issuing the...

```
passwd root
```

command and then disabled it by issuing the

```
passwd -i root
```

command. 

Bottom Line... how do I make it the way it was before disabling it and before I got the message popping up.

Thanks guys,

-J

---

### Post by connorh123 on 2009-04-03
I think I know what you're talking about.
Try going into Administration>Users and Groups> unlock it>then change it.

---

### Post by stchman on 2009-04-03
There is ZERO need to have a root account.  I have been an Ubuntu user for over 2 years and never needed to log in as root.  With sudo you can do whatever administration needs you have to do.

---

### Post by th3 mant1s on 2009-04-03
Hi connorh123,

Unfortunately I don't have a GUI. 

do know how to do it via terminal?

Thanks

-J

---

### Post by th3 mant1s on 2009-04-03
> **stchman said:**
> There is ZERO need to have a root account.  I have been an Ubuntu user for over 2 years and never needed to log in as root.  With sudo you can do whatever administration needs you have to do.

stchman I understand. however this is in a controlled environment I NEED TO FIX THIS. If you have the answer would you please tell?

Thanks 

-J

---

### Post by kanikilu on 2009-04-03
Can you re-enable it in recovery mode?

It seems they take a pretty strict stance on "root talk" around here, so I'll leave it at that...

---

### Post by connorh123 on 2009-04-03
> **th3 mant1s said:**
> Hi connorh123,

Unfortunately I don't have a GUI. 

do know how to do it via terminal?

Thanks

-J

Like stchman said, root isn't all that important.
In fact, it can be very dangerous if you ever log on as it.
And an answer to your question, no, I don't know how to do it via terminal.

---

### Post by CyberMando on 2009-04-03
If I am reading thsi correctly, you are no longer able to use sudo or su or login as root because you have disabled the root account. Is it true that sudo not longer works?

---

### Post by connorh123 on 2009-04-03
Are you now saying you're having trouble with sudo?

---

### Post by albinootje on 2009-04-03
> **th3 mant1s said:**
>  ```
[sudo] password for hypernode: 
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)

```


What happens when you boot into "recovery mode" and then run :
```

usermod -L root
init 2

```
Does that fix sudo usage for you ?

---

### Post by stchman on 2009-04-03
> **th3 mant1s said:**
> stchman I understand. however this is in a controlled environment I NEED TO FIX THIS. If you have the answer would you please tell?

Thanks 

-J

As I have never had need or ever used root account I have no knowledge.  AFAIK, it is against forum rules to discuss enabling root accounts on Ubuntu.

I am sure you can Google this and come up with something.

---

### Post by CyberMando on 2009-04-03
I am new today and I just read the conduct policy and did not see that it is against the rules. Where would I find that rule? Does that mean that people with this problem and not get help from th eUbuntu communuty? What is the meaning of Ubuntu again?

---

### Post by primaxx on 2009-04-03
> **CyberMando said:**
> I am new today and I just read the conduct policy and did not see that it is against the rules. Where would I find that rule? Does that mean that people with this problem and not get help from th eUbuntu communuty? What is the meaning of Ubuntu again?

I din't know that either, but here is the rule!:
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by CyberMando on 2009-04-03
> **primaxx said:**
> I din't know that either, but here is the rule!:
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

Sure enough, it does say to not post how to allow root access. Right below that is

Following those should see you right in the forums, but do note that they are only a shortened version of the full Code of Conduct.

So I looked at the Code again and searched for root and was not able to find it. I wonder if that would include a case like this where, because no one would provide correct info about how to enable root, the user did it incorrectly and is now unable to use sudo. I had not expected this community to have the attitude that security lies in ignorance. That is entirely counter to best IT knowledge and counter to the free software spirit.

---

### Post by albinootje on 2009-04-03
> **CyberMando said:**
> I am new today and I just read the conduct policy and did not see that it is against the rules. 

I realize that booting into recovery mode might not work because of your expired root password.
Can you test it ?
Or is this a remote VPS you're working on ?

If it's a machine you can reach physically and it has a cdrom- or dvd-drive then it can be fixed by booting from a Linux live cdrom/dvd and then mount the Linux partition that has /etc on it, and then fix the problem by editing (removing the encrypted password for user root) in /etc/shadow.

---

### Post by th3 mant1s on 2009-04-03
Hi Again Everyone,

I am not having trouble with

sudo su or sudo 

all i really want is for the message to stop popping up. Also I know what how offended everyone is about the whole root thing however it's in a controlled environment and is in a purely isolated area with no contact via the internet or anything else. I never intend to put it on the net. In fact it may just go away for ever soon. Just was wondering about how to get rid of the "expired" message that comes up.

Thanks all,

-J

---

### Post by th3 mant1s on 2009-04-03
> **stchman said:**
> As I have never had need or ever used root account I have no knowledge.  AFAIK, it is against forum rules to discuss enabling root accounts on Ubuntu.

I am sure you can Google this and come up with something.

I don't want to sound pompous however if talking about a root account is against forum policy why don't we just all together pretend root accounts (or privlidges) exist all together? It seems we have entered a quagmire of a topic.

---

### Post by CyberMando on 2009-04-03
sudo -s
to get a root shell
passwd
to set the root password. Your message is gone and your computer is more secure.

---

### Post by stchman on 2009-04-03
> **th3 mant1s said:**
> I don't want to sound pompous however if talking about a root account is against forum policy why don't we just all together pretend root accounts (or privlidges) exist all together? It seems we have entered a quagmire of a topic.

I think what the forum admins are trying to do is create a culture that does not use root login.  They want to create a culture that uses sudo to get administrative tasks accomplished.

Problem is when one logs in as root you pretty much bypass all the security features Linux has.  People can then get malicious code on their system.  After that these root login folks will bash Ubuntu as a POS insecure OS when they violated the security of the OS.

This will be my last post on root login cr@p.  As you can see I am 100% against it.  I am sure there are others out there that care very little about security so google is their best bet on getting info.

---

### Post by CyberMando on 2009-04-03
Are you aware that anyone who can reboot your computer has only to use the rescue option to get root access to your computer?

---

### Post by Zill on 2009-04-03
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

[http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by bodhi.zazen on 2009-04-03
I am going to close this thread now.

First, we do support setting a root password when necessary (and,yes indeed there are times when it is in fact necessary).

If it is not necessary , please use sudo -i.

I will not belabor that point, but for informational purposes see :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

[YARP - Yet another root post]("http://ubuntuforums.org/showpost.php?p=5769207&postcount=77") :twisted:

There are many problems with setting a root password, and this thread is one such example, it can cause breakage.

Although we tell people this, many do not get it and feel we are being paternalistic.

I usually do not argue with trolls or people who, as the OP does, 

> you know that I know what i'm doing/end rant

At any rate, this is a known bug with sudo and exists on Debian/Ubuntu systems.

The solution is to boot to the recovery mode and set a root password

Then lock the root account with :

```
usermod --lock root
```Reboot or telinit 2

and all will be well in  the world.

All I ask in return is that you stop ranting about Ubuntu and sudo already.

---

### Post by bodhi.zazen on 2009-04-03
Update :

This is the PM I received from [th3 mant1s]("http://ubuntuforums.org/member.php?u=778343")

> **Thank You**             
                                                                
Bodhi

Thanks for regulating the "expired root account -- need to re-enable" thread. I was trying to express as clearly as possible what I know what entails when operating as root. This was an academic exercise that I just needed some information on however people will whenever talking about root tend to swing the topic out of proportion. Anyway thank you for the solution! I've been using Ubuntu for a few years for all my server and in mixed environments and its great. I've always wondered why that message wouldn't go away so I posted on it.

Thanks,

---Name obfuscated for privacy.

---


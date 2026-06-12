---
title: "kstartupconfig4 does not exist or failed. The error code is 3. Check your installatio"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by carolija on 2009-05-22
Can anyone help me please I am going crazy now, this is i don't know how many time after installing kubuntu happening : > kstartupconfig4 does not exist or failed. The error code is 3. Check your installation .

So it's go like this, after installation all is fine few days and after I'd like to change my desktop to look little bit "fency" and install some programs I have even save the list of programs!
This is list of programs I have installed before this hepend :

[http://carolija.eu/how-to/I-installed-this]("http://carolija.eu/how-to/I-installed-this")

...So wan i install them and after restart i got this msg kstartupconfig4 does not exist or failed. The error code is 3. Check your installation , but I can login via ssh from other IP just i can't run X only way to get in is via konzola .

This is my Xorg.0 log ( maybe this help too )

[http://carolija.eu/how-to/Xorg.0.log]("http://carolija.eu/how-to/Xorg.0.log")

And yes I use ATI at this old PC where I'd like to use kubuntu. somebody told me there is some problem whit those two ?

what i should do please advice to I don't reinstall it again

---

### Post by Sef on 2009-05-22
1) How much ram do you have?

2) What is your ATI card model?

---

### Post by carolija on 2009-05-22
> **Sef said:**
> 1) How much ram do you have?

2) What is your ATI card model?

i think there 1 giga Ram but I don't remember whats the ATI model, is there is some command to see that please ?


Thank you Sef for your time,


> carolija@carolija:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1002        396        606          0        100        223
-/+ buffers/cache:         72        930
Swap:         5686          0       5686
carolija@carolija:~$ 
-
carolija@carolija:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026476     406100     620376          0     102812     229312
-/+ buffers/cache:      73976     952500
Swap:      5823460          0    5823460
carolija@carolija:~$ 


Ah there is it, i found it ( hope it's good command ) :

> carolija@carolija:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
carolija@carolija:~$ 


---

### Post by carolija on 2009-05-23
Any help please ?

---

### Post by carolija on 2009-05-25
I have find solution, thanks !

---

### Post by rafaloo on 2009-05-28
I have the honor of the same message!
```
kstartupconfig4 does not exist or failed. The error code is 3. Check your install
```
You can write as you did it

---

### Post by Dread Knight on 2009-06-09
> **carolija said:**
> i have find solution, thanks !

help please!

---

### Post by glantucan on 2009-07-14
I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

---

### Post by bb69 on 2009-07-21
Yes ! it works for me too: my home directory was previously a different linux distro, and the property was not correctly setup
thanks

---

### Post by Kobalt on 2009-07-22
It worked for me as well, the problem occured after an update-reboot, using Karmic. Strange...

---

### Post by itnet7 on 2009-08-04
> **glantucan said:**
> I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

Thanks Glantucan, This fixed mine as well after an upgrade of a previously working kde version in Jaunty!

Chris

---

### Post by jim.hitch on 2009-08-08
> **glantucan said:**
> I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

Unfortunately this hasn't worked for me.

There quite a lot comes up in a search for this error. But it's all pretty vague.

This has happened to me after two days of setting up jaunty on a new machine in order to move to it for work. If I can't find anything I'll start again and reinstall from scratch. I always find myself doing that at least a couple of times on any new machine / new install combination!

Any other ideas would be most welcome.

Jim

---

### Post by karlabe on 2009-08-27
Using the previously suggested approach did not solve my problem. There is a difference in the error message that keeps popping up whenever I enter a KDE session (cause the problem does not exist when I enter a GNOME session), the number generated is 127 not 3. I tried to google for this with little success. 
kstartupconfig is found in /usr/bin and from command prompt it executes fine, i.e. no errors are generated. What does not execute is kdostartupconfig4, which according to some replies I found to similar problems, is related. When invoked this output is returned:
kdostartupconfig4: symbol lookup error: kdostartupconfig4: undefined symbol: _ZN6KDebug13hasNullOutputE9QtMsgTypei

Cannot make any sense out of this.
Any help is greatly appreciated

---

### Post by jim.hitch on 2009-08-27
Hi

Since posting my query I've given up on KDE4 for the time being and gone for 3.5.10 which I know to be rock solid. I use my laptop for work, so only have so much patience for systems that still appear to be unstable. 

I didn't find any answers to the issue, but on building a non-work partition with 9.04 I haven't had a repeat of the problem above. 

The only difference between builds with the problem and that without is that I didn't specify that the /home partition be encrypted in the build which worked.

Does your build have a separate /home partition, and is it encrypted?

---

### Post by Bobscrachy on 2010-08-15
> **glantucan said:**
> I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

How did you find out what group this folder was in order to use that command? And why did chown accept the newowner.newgroup as the same thing? Wouldn't it be something like name of account and type of account. Like name.adminstrator? 

This fix worked for me, but i'm trying to understand how it worked.

---

### Post by loknar28 on 2010-08-30
Has anyone tried running the command 
sudo chown -R **username**.**username** /home/**username**/.kde in a domain environment.

If so how would the command be formatted?

I tried 
sudo chown -R **DOMAIN\username**.**DOMAIN\username** /home/DOMAIN/**username**/.kde
and I get the following error
chown: invalid user 'domainusername.domainusername'

Running wbinfo -u gives accounts in the DOMAIN\username format and I greped to verified the user is there.

---

### Post by craft47 on 2011-06-10
> **bb69 said:**
> Yes ! it works for me too: my home directory was previously a different linux distro, and the property was not correctly setup
thanks

Hi I am having the same problem, but when I log in to the console and enter the command I get that /home/username/.kde does not exist.  I am thinking this may be because my /home is on another partition, am I on the right track?  I am going to try /dev/sda6/home/username/.kde.  Would that be right if my /home is on the sda6 partition?

---

### Post by COKEDUDE on 2011-07-07
> **glantucan said:**
> I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

Thx for this.

---

### Post by mariconor on 2011-10-06
> **jim.hitch said:**
> Unfortunately this hasn't worked for me.

There quite a lot comes up in a search for this error. But it's all pretty vague.

This has happened to me after two days of setting up jaunty on a new machine in order to move to it for work. If I can't find anything I'll start again and reinstall from scratch. I always find myself doing that at least a couple of times on any new machine / new install combination!

Any other ideas would be most welcome.

Jim

I had the same issue, and it was caused by selinux, and not the file  permissions per se. 

The solution was to run (as root user)

restorecon /home -R

---

### Post by 4ebees on 2011-11-01
Even an old post can come in handy.

Brand new install of Ubuntu, then the KDE desktop then...nothing!

:)

Thanks for writing a fix all those year ago :)

:guitar:

---

### Post by adquinn82 on 2012-09-14
> **glantucan said:**
> I may have found a workaround. For some reason ~/.kde belongs to root in my system. If that's your case, run
```

$ sudo chown -R **username**.**username** /home/**username**/.kde

```

Hope this helps
Cheers!

Thanks allot, this worked perfectly!

---


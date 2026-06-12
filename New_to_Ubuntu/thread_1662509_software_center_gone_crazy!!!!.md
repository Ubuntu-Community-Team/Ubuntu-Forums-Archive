---
title: "software center gone crazy!!!!"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-08
pls somebody help as my software center of ubuntu 10.10 has gone crazy... wenever itry to install any software 4m it by clicking on the install button against the software ots displaying an error    
REQUIRES INSTALLATION OF UNTRUSTED PROGRAM
         The action would require the installation of packages from              not authenticated sources.'


PLS PPL HELP ME I NEED TO INSTALL A LOT OF SOFTWARES 4M SOFTWARE CENTER..PLS:(:(:(:(

---

### Post by Norm24 on 2011-01-08
First thing no texting abbreviations if you want accurate help.

Second there's absolutely nothing wrong with Software Center,its simply informing you that you're installing software from outside the official repos.

If you trust the software and the source from which you'll be downloading it then go ahead download and install it.If you don't then don't use it.

---

### Post by vivek.pandey on 2011-01-08
> **Norm24 said:**
> First thing no texting abbreviations if you want accurate help.

Second there's absolutely nothing wrong with Software Center,its simply informing you that you're installing software from outside the official repos.

If you trust the software and the source from which you'll be downloading it then go ahead download and install it.If you don't then don't use it.

thanx a lot sir for ur help and advise but i dont think all softwares in my software center are from outside the official repos including mysql!!!
and secondly no such option is there as to go ahead its just the error message and no further movement just installation stops

---

### Post by QLee on 2011-01-08
[QUOTE=neo_aryan]thanx a lot sir for ur help and advise but i dont think all softwares in my software center are from outside the official repos including mysql!!![/QUOTE]

However, Norm24 didn't suggest "all software" in the software center, it is clear that at least some of the software that you are trying to install can not be authenticated. 

If you want more specific help then be more specific about what software you are trying to install and where you are trying to install it from. 

And I suggest you not "snap" at people who are trying to help by explaining things you don't yet know as an inexperienced user. If you treat people with respect, most of them will do likewise.

---

### Post by Linyx on 2011-01-08
Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```
then ....

```
apt-key add ~/.gnupg/pubring.gpg
```

See whats the output now.........

---

### Post by 3rdalbum on 2011-01-08
Sometimes this happens - the package manager thinks that all your repositories are not authenticated. If you reload the package list, it should solve the problem. You can reload the package list by going to System > Administration > Synaptic Package Manager and clicking the Reload button, or by typing this into the terminal:

```
sudo apt-get update
```

BTW I don't think the OP was snapping at the answerer, it's just his/her way of talking. And his description was correct, Ubuntu Software Center will not proceed with an unauthenticated package installation.

---

### Post by vivek.pandey on 2011-01-08
> **Linyx said:**
> Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```
then ....

```
apt-key add ~/.gnupg/pubring.gpg
```

See whats the output now.........

here are the outputs for the first code
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5[/CODE]

gpg: requesting key 437D05B5 from hkp server wwwkeys.eu.pgp.net
?: invalid HTTP proxy ([http://localhost:4001](http://localhost:4001) ): bad URI
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0



for second codeapt-key add ~/.gnupg/pubring.gpg
gpg: no valid OpenPGP data found.

---

### Post by vivek.pandey on 2011-01-08
> **QLee said:**
> However, Norm24 didn't suggest "all software" in the software center, it is clear that at least some of the software that you are trying to install can not be authenticated. 

If you want more specific help then be more specific about what software you are trying to install and where you are trying to install it from. 

And I suggest you not "snap" at people who are trying to help by explaining things you don't yet know as an inexperienced user. If you treat people with respect, most of them will do likewise.

i really apologise if my sentence was taken the other.. wat i meant was i tried to install some 5 to 6 softwares  which included catfish file search,converterall,mysql administrator ans few more i don remember.. all asked for my authentication and after i entered my password gave the error command. so by all i meant every software i tried to download was giving the error so i thought all softwares have same problem.

once again i m really really sorry for my conduct

---

### Post by QLee on 2011-01-08
[QUOTE=neo_aryan]...

once again i m really really sorry for my conduct[/QUOTE]

It's really not a big problem, I only made the suggestion in case you hadn't yet thought about it, we all work better together if we treat each other with respect and don't assume. And there is no reason that you have to listen to me anyway.

I hope the advice given you in this thread above has helped with the problem, those programs you mention sound like ones that would be in official repositories..

---

### Post by vivek.pandey on 2011-01-08
thanx to all for my help... i dont know whether the entire problem is solved or not neither which of the solution did the trick as ai tried all but for the time being i can download and install the softwares which i wanted... so thanx to all:P:P:P:P

---

### Post by QLee on 2011-01-08
[QUOTE=neo_aryan]...
?: invalid HTTP proxy ([http://localhost:4001](http://localhost:4001) ): bad URI
...[/QUOTE]

This looks like you have set a proxy, maybe you were trying to surf anonymously or something and the system is still trying to use the proxy for accessing the 'Net.


[Edit] I see that you are downloading OK now, good!

---

### Post by vivek.pandey on 2011-01-08
> **QLee said:**
> This looks like you have set a proxy, maybe you were trying to surf anonymously or something and the system is still trying to use the proxy for accessing the 'Net.

yes ..actually i have installed tork just to hide my ip.....i couldnt configure it properly it seems so even i dont know whether its working properly or not... my intention to install tork was just to study how such softwares work..how can they hide my ip address...but seems things didnt go the way i wanted ...so i left it solve in near future:):):):)

---

### Post by QLee on 2011-01-08
> **neo_aryan said:**
> yes ..actually i have installed tork just to hide my ip.....i couldnt configure it properly it seems so even i dont know whether its working properly or not... my intention to install tork was just to study how such softwares work..how can they hide my ip address...but seems things didnt go the way i wanted ...so i left it solve in near future:):):):)

You probably wanted tor, to be part of the tor network for anonymously browsing the 'Net. Yes, I think you should skip that for now, it will slow down your surfing anyway because of the hops to different servers to try and hide your IP. When you are ready, use a search engine for tor as a keyword.

---


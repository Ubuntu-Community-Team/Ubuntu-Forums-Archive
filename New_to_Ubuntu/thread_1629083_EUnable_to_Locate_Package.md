---
title: "E:Unable to Locate Package"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by vyas.subbu on 2010-11-23
Hi,

This message appears all the time when I try to apt-get install any package?
Any help? Am I missing something?

---

### Post by amjjawad on 2010-11-23
> **vyas.subbu said:**
> Hi,

This message appears all the time when I try to apt-get install any package?
Any help? Am I missing something?

System > Administration > Synaptic Package Manager

Click on "Reload" and check whether you get the same issue after that or not.

---

### Post by sikander3786 on 2010-11-23
> This message appears all the time when I try to apt-get install any package?

That shouldn't be the case for "any" package. It should be with some specific package only for which the repositories need to be turned on.

Please post the output of

```
sudo apt-get update
```

And also the name of the package you are actually trying to install.

---

### Post by Elfy on 2010-11-23
Please give us more information.

Please show us the output of this command run in a terminal - Apps- Accessories

```
cat /etc/apt/sources.list
```

---

### Post by vyas.subbu on 2010-11-24
> **sikander3786 said:**
> That shouldn't be the case for "any" package. It should be with some specific package only for which the repositories need to be turned on.

Please post the output of

```
sudo apt-get update
```

And also the name of the package you are actually trying to install.

Hi,
Thanks, the list is quite big, it is a server that has this problem. Can you please let me know what you are looking out for?

---

### Post by vyas.subbu on 2010-11-24
> **forestpiskie said:**
> Please give us more information.

Please show us the output of this command run in a terminal - Apps- Accessories

```
cat /etc/apt/sources.list
```
Hi,

Thanks for reply. The list is a long one. Can you let me know what is that we need to look for?

---

### Post by vyas.subbu on 2010-11-24
> **sikander3786 said:**
> That shouldn't be the case for "any" package. It should be with some specific package only for which the repositories need to be turned on.

Please post the output of

```
sudo apt-get update
```

And also the name of the package you are actually trying to install.

Hi,
Sorry for incorrect reply. 

It says unable to connect to gb.archive.ubuntu.com. And I see it failed. I am trying to install Nagios.

---

### Post by Elfy on 2010-11-24
When we ask for information we quite often know what it will look like.

Please post with the information you have been asked to provide.

---

### Post by vyas.subbu on 2010-11-24
> **forestpiskie said:**
> When we ask for information we quite often know what it will look like.

Please post with the information you have been asked to provide.
Hi,

Thanks for replying. 
Do you mean you want me to type 50-60 lines that scrolls down? Or are you looking for anything in specific? any section in the whole run?

---

### Post by philinux on 2010-11-24
> **vyas.subbu said:**
> Hi,

Thanks for replying. 
Do you mean you want me to type 50-60 lines that scrolls down? Or are you looking for anything in specific? any section in the whole run?

**Copy and paste** all the info here.

Highlight the text then use the code wrap # key to make it display better here.

```
example
```

---

### Post by Elfy on 2010-11-24
Yes - I would not expect anyone to type out that many lines - unless they were my child ;)

You should find that if you highlight all the text then a click with the middle mouse button will paste it for you - nice and easy once you know how. 

If you only do a quick reply you will not see the # that philinux talks about - you can instead type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end to get the same result.

[There are more BBCode options available.]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by vyas.subbu on 2010-11-25
> **forestpiskie said:**
> Yes - I would not expect anyone to type out that many lines - unless they were my child ;)

You should find that if you highlight all the text then a click with the middle mouse button will paste it for you - nice and easy once you know how. 

If you only do a quick reply you will not see the # that philinux talks about - you can instead type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end to get the same result.

[There are more BBCode options available.]("http://ubuntuforums.org/misc.php?do=bbcode")
:)

The problem is that, it is a separate system (Server) and I am typing all this from an other system. 

 Can I invoke browser on my server system? If yes, please let me know how?

I can than copy and paste it. Sorry to be a pain.

---

### Post by Elfy on 2010-11-25
Aah - always makes it useful to give people a clue as to what is going on :)

Maybe try creating a new sources list

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

See how that goes - then maybe you could use pastebinit to get the information - you'll need to install it

> sudo apt-get install pastebinit 
cat /etc/apt/sources.list | pastebinit
sudo apt-get update | pastebinit

then paste the 2 urls you'll get here.

In effect - we are looking for any errors from the commands.

---

### Post by ersinm on 2011-07-01
Hi everyone,

I'm having an issue similar to this. I'm trying to install MyDNS on Ubuntu 10.10. Each time I go to install I get the below error msg.

Any assistance would be much appreciated.

I hope the below info helps, if you need anything further please let me know.

:)

Thanks,
Ersin



```

root@oxygen:~# apt-get install mydns-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package mydns-mysql

```

```

root@oxygen:~# cat /etc/apt/sources.list
deb http://ftp.iinet.net.au/pub/ubuntu maverick main restricted universe
deb http://ftp.iinet.net.au/pub/ubuntu maverick-updates main restricted universe
deb http://ftp.iinet.net.au/pub/ubuntu maverick-security main restricted universe

```

---

### Post by CatKiller on 2011-07-01
I don't know anything about the package that you're trying to use, but a quick search of packages.ubuntu.com shows that it was only ever included in Dapper (6.06 LTS). Did the project get renamed to something else, perhaps?

EDIT: Did a quick search. The project page implies they haven't done anything since 2006. Which would explain why it hasn't been included in later Ubuntu releases.

EDIT 2: It looks like there's a project called mydns-ng that appears to be based on the earlier mydns. Doesn't seem to be included in the repositories but you could probably compile it.

---

### Post by ersinm on 2011-07-02
Thank you for your help, I will look into this. If I need any further assistance with this can I just reply back to this thread or a new thread? Sorry, never posted on forums before, only read them.


Thanks,
Ersin

---

### Post by CatKiller on 2011-07-03
> **ersinm said:**
> Thank you for your help, I will look into this. If I need any further assistance with this can I just reply back to this thread or a new thread? Sorry, never posted on forums before, only read them.

This topic, this thread. New topic, new thread :)

---

### Post by pengper on 2011-07-13
Hey guys, I have a similar problem. Trying to install Enlightenment.

I had a different error, but it was solved very fast with a search on the forums. Then I came up against this error. I tried it under both names "Enlightenment" and "e17". Here's the output to the things you guys suggested:

```

sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```
```


gossfunkel@gossfunkel-eMachines-D620:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

sorry it's so long :/
thanks

---

### Post by CatKiller on 2011-07-13
[QUOTE=pengper;11043057]
```

sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```Close the other package manager that you've got running.

(including Update Manager)

---

### Post by wraith1234 on 2011-08-23
i have the same problem... here is output:
#
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
#

---

### Post by the_zizi on 2011-08-24
Hi

I have simmilar problem. At the beginning I will put some light on my case. I'm trying to do LiveCD of my system. To do this I'm using program called Ubuntu Customization Kit(UCK). During this program i chose option to add programs manually using console or software center. I chose console and i write in *apt-get install name_of_package. *I'm trying to install Meep. But I get this message: E: Unable to locate package meep

This works when I'm doing it on my system, but on console connected to UCK gives me this error. Any ideas why. This also worked few weeks ago on UCK but now it doesn't. 

I've tried apt-get update but it didn't help. I think that it is worth metioning that I was able to install for eg. aptitude package. 

Any answer which put some light on this case is welcom.

Best regards
the_zizi

---

### Post by Miljet on 2011-08-24
I can see this thread is going to get really confusing. I have already lost count of how many individual problems we are supposed to be solving in this one thread.

---

### Post by the_zizi on 2011-09-08
Hi

Solution of this matter was quite simple. Man need to copy  /etc/apt/sources.list file from host system to newly created one, which  is localized at ~/tmp/remaster-root/etc/apt/surces.list. After that you need to update repository list (apt-get update). That should solve problem with apt-get install on UCK

Host system and new one were created from same .iso disc. I don't know why, but consistency of this two files is different.

Regards
the_zizi

---

### Post by deepi721 on 2011-12-04
i m also getting same error unabble to locate package.. plz help me out..

---

### Post by oldos2er on 2011-12-04
Please start a new thread, and give as many details of your problem as possible.

---

### Post by oldos2er on 2011-12-05
Closed, necromancy.

---


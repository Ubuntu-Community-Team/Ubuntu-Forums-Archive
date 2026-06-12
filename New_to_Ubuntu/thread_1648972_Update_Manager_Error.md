---
title: "Update Manager Error"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by chevyboy_0 on 2010-12-19
I keep getting a red dot with a wite line through it on my top tool bar. And when I click it I get an error message and this is what it says

'E:Malformed line 63 in source list /etc/apt/sources.list (dist parse)'

does any one have a fix for this? 

Thanks Andrew

---

### Post by Verbeck on 2010-12-19
could you post the output of the following from a terminal (applications>accessories)
```
cat /etc/apt/sources.list
```

---

### Post by stjohnmedrano on 2010-12-19
can we see your /etc/apt/sources.list ?

let see whats on your line 63, 

try this on your terminal.

```

cat -n /etc/apt/sources.list

```

---

### Post by ivanovnegro on 2010-12-19
Hey, could you be a little more precise with the red dots you mean.
What is not going exactly and maybe you could put here the output of your sources list?
What version of Ubuntu are you using etc.?

---

### Post by karthick87 on 2010-12-19
Post the output of,

```
cat -n /etc/apt/sources.list | grep 63
```

---

### Post by AngusH on 2010-12-19
> **ivanovnegro said:**
> Hey, could you be a little more precise with the red dots you mean.

I think he is referring to a stop sign. Like the ones you see on roads (at least in Britain).
Angus

---

### Post by chevyboy_0 on 2010-12-19
I am using 10.10

this is the output of cat /etc/apt/sources.list

> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner


deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner
deb-src [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartnerthis is from cat -n /etc/apt/sources.list | grep 63

>     63    deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner

---

### Post by ivanovnegro on 2010-12-19
> **chevyboy_0 said:**
> I am using 10.10

this is the output of cat /etc/apt/sources.list

this is from cat -n /etc/apt/sources.list | grep 63

You mixed your repositories with Lucid Lynx, an older release of Ubuntu but you are running currently Maverick.
I think this is the culprit.

---

### Post by karthick87 on 2010-12-19
Comment out the last two lines in your sources.list.So that it should look like,
> #deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner
#deb-src [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner                      ```
sudo apt-get update
```

---

### Post by chevyboy_0 on 2010-12-19
> **karthick87 said:**
> Comment out the last two lines in your sources.list.So that it should look like,
```
sudo apt-get update
```


Pardon the noob question but what exactly do you mean? Im still learning my way around Ubuntu. Im a Windows convert

---

### Post by stjohnmedrano on 2010-12-19
> **chevyboy_0 said:**
> I am using 10.10

this is the output of cat /etc/apt/sources.list

this is from cat -n /etc/apt/sources.list | grep 63

i think you should try put spaces between lucidpartner.

```

63    deb [http://archive/canonical.com/](http://archive/canonical.com/) lucid partner 			 		

```

---

### Post by karthick87 on 2010-12-19
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner


[COLOR=Red]#deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner
#deb-src [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner [/COLOR]    
```
See the last four lines carefully..You already have,
> deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
 deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
So comment out the last two lines,
> #deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner
#deb-src [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner 

---

### Post by Verbeck on 2010-12-19
run ```
gksudo gedit /etc/apt/sources.list
``` from a terminal or run dialogue(alt+F2) to edit the file and add a # to the beginning of the last two lines

edit: don't forget to save the file

---

### Post by chevyboy_0 on 2010-12-19
again i apologize for the question but by comment out do you mean remove or something else?

---

### Post by stjohnmedrano on 2010-12-19
> **chevyboy_0 said:**
> again i apologize for the question but by comment out do you mean remove or something else?

it means that when the computer read your /etc/apt/sources.list he will not read that part.

---

### Post by karthick87 on 2010-12-19
Those lines are not necessary you can delete the last two lines..Or you can add # sign infront of those lines..So that it should look like,
> 
#deb [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner
#deb-src [http://archive/canonical.com/](http://archive/canonical.com/) lucidpartner 			 		

---


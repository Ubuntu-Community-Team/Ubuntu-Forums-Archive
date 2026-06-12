---
title: "soucses.list Empty? cant save changes?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by tcbarr on 2011-04-26
So I looked around for a while on the webz and couldnt find an answer to  this problem in other threads.

I have a malformed lin (46) in source code /etc/apt/sources.lists.
I used the gedit command and the page that was opened was black
as per a recommendation I copied and pasted someone elses code but it wont let me save it, it says "could not find the file /etc/apt/sources/list.

please help, I'm such a noob

Oh, Im using ubuntu 10.04

---

### Post by coffeecat on 2011-04-26
Be very careful not to make typos.

> **tcbarr said:**
> /etc/apt/sources.lists.

and

> **tcbarr said:**
> /etc/apt/sources/list.

... are both wrong. It should be /etc/apt/sources.list . Use:

```
gksudo gedit /etc/apt/sources.list
```And be very careful with what you type or edit! :wink: That command gives you full administrative privileges and you can seriously damage your system if you are not careful.

Good luck and welcome to the forum. :)

---

### Post by tcbarr on 2011-04-26
Thanks coffeecat!
I was trying to install Chorme and got a "malformed line 46 in source" message before all this and I dont know how to fix that either.

here is what came up,

# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by satyanash on 2011-04-26
Hi,
as you can see in the last two lines of what you have pasted up there(namely line 46 and 47):

[COLOR="Red"]Incorrect Version[/COLOR]
```
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
```

[COLOR="Lime"]Correct Version[/COLOR]
```
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
```

make sure you add spaces between .com/[HERE]lucid

after that save!
next:

```
sudo apt-get update
```

Everything should be fine after this.

Satyajeet

---

### Post by coffeecat on 2011-04-26
Hi. Both lines 46 and 47 are malformed. In fact they're both superfluous. These are your lines 45, 46 and 47:

```
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
```Which are the last three lines in the file. See how there is no space between the com and lucid. That's not right. Anyway, lines 45, 46 and 47 are all unnecessary duplicates because you have a working archive.canonical partner line further up. Line 45 is also malformed even though the system isn't complaining about it. Simply delete those three lines.

Above this bit: 

```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
```Which you can leave, you will see this:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[COLOR=Red]deb http://archive.canonical.com/ubuntu lucid partner[/COLOR]
# deb-src http://archive.canonical.com/ubuntu lucid partner
```The line I've highlighted in red is the working partner line. Leave that as it is.

---

### Post by matthew.parlette on 2011-04-26
> **tcbarr said:**
> Thanks coffeecat!
I was trying to install Chorme and got a "malformed line 46 in source" message before all this and I dont know how to fix that either.


I'm not sure that 'source' mentioned in the error message means apt-get sources (apt-get sources is where the Ubuntu software center looks for programs you can install or update)

How are you installing Chrome? I did it this weekend by going here:
[http://www.google.com/chrome]("http://www.google.com/chrome")

And selecting the .deb package for Ubuntu/Debian. I can't remember the exact terminology on the page, so give me the steps you took and I'll see if I can give you a hand, be as descriptive as possible in your description.

---

### Post by tcbarr on 2011-04-26
Got it!

Thanks everyone :P

---


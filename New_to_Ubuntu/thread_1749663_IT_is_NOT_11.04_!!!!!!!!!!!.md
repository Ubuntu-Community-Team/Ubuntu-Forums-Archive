---
title: "IT is NOT 11.04 !!!!!!!!!!!"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by willyconkz on 2011-05-04
'about ubuntu' says it is 11.04 but I have no dash, no new files, nothing I can see. The upgrade (from update manager) downloaded nearly 700 meg then kept failing on last file of 1354 then aborting. I tried a dozen times and even tried different servers. Now it no longer shows as available to upgrade.

So how do I uograde without having to download a fresh install and all the pain of that?
Why does it say it is 11.04 when it is not?

---

### Post by jtarin on 2011-05-04
Your "Failed" update dialogue should tell you the file it is failing on......which one?
To see the intended desktop you might have to log out then select the desktop you want from the menu at the bottom of the login screen.

---

### Post by 23dornot23d on 2011-05-04
What does it display when you enter ......

uname -a

in a terminal .......

---

### Post by willyconkz on 2011-05-04
2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:13:54 UTC 2011 i686 GNU/Linux

when it fails it is while downloading file 1354 of 1354[I]

Could not download the upgrades
The upgrade has aborted. Please check your Internet connection or  installation media and try again. All files downloaded so far are kept.[/I]

On 'restart' I get the version as above plus two earlier versions offered plus recovery modes, nothing newer.

---

### Post by Rubi1200 on 2011-05-04
If you are currently on 10.10, there is/was a bug in the About Ubuntu menu which would say you are using 11.04 when you are not.

For the situation you are now in, post the output of this file please as we may find something that can help us:

```
cat /etc/apt/sources.list
```

---

### Post by willyconkz on 2011-05-04
unfortunately, after that restart, it will no longer open a terminal, says 'starting terminal' then disappears ... I shall try another restart.

---

### Post by jerome1232 on 2011-05-04
You can download an Alternate install cd, and use it to upgrade, I believe even the desktop cd's offer that option now as well.

That's actually how I upgrade distro to distro generally, seems alot less problematic than a network upgrade.

---

### Post by ted_rmt on 2011-05-04
There is a possibility that you logged in with a Ubuntu classic session. When you first click your username in the login window you will have session options that appear at the bottom of the screen. One other forum user ran into a problem because he disabled "use password on login" and never saw the session screen.

Before I speculate further. Try the help menu on the panel if  gnome is running; click the About option and see if that tells you you are running 11.04

---

### Post by fremantle on 2011-05-04
how many times do i have to say, always start fresh with a new ubuntu release :)

---

### Post by willyconkz on 2011-05-04
Thatnks but I don't want to go to a fresh install unless all else fails as I have downloaded a lot of stuff, programmes etc. I want to keep and not have to re-download as it is expensive here! I have data backed up of course but it is a real pain re-installing fresh and re-doing everything and tweaking settings etc.

cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted main #Added by software-properties

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by Never_Give_Up on 2011-05-04
That sounds like what happened to me in Unix but there was a script to fix it regardless of whether it is supported, so someone should have it but im not familiar with 11.04, but there is a fix you may need to purge your packages some may have errors, i am new here the pointof this message is that dont give up on it cuz theres a way to fix it

---

### Post by willyconkz on 2011-05-04
Help 2.30.1
Gnome 2.32

log on gives me only the choices I mentioned, password on log on is enabled

---

### Post by jerome1232 on 2011-05-04
I didn't say fresh install, I said upgrade.

The discs can upgrade an existing installation. Had I meant fresh install I'd have said fresh install but I said upgrade.

:popcorn:

---

### Post by willyconkz on 2011-05-04
> **jerome1232 said:**
> I didn't say fresh install, I said upgrade.

The discs can upgrade an existing installation. Had I meant fresh install I'd have said fresh install but I said upgrade.

:popcorn:
Yeah yeah, put your ego back in its box or bugger off, you are not helping me. Helpful is an attitude, not words. I am trying hard to be patient and work this out, pedantic arseholery really is worthless on your part with beginners who easily misunderstand. But then you know that, you just choose to be a fool.

I worked out what was meant by the session prompt at the bottom, there it also just offers ubuntu desktop or recovery or safe mode, no other options.

---

### Post by THE CARTER on 2011-05-04
You don't have to do a fresh install. In the live cd/usb there is an option to upgrade your existing ubuntu install. I got a similar error from the upgrade manager, and when I upgraded from the live cd it fixed everything. You can even upgrade an existing 11.04 install to a factory default 11.04 install to fix the problems.

Download the iso from the ubuntu homepage.

---

### Post by willyconkz on 2011-05-04
> **THE CARTER said:**
> You don't have to do a fresh install. In the live cd/usb there is an option to upgrade your existing ubuntu install. I got a similar error from the upgrade manager, and when I upgraded from the live cd it fixed everything. You can even upgrade an existing 11.04 install to a factory default 11.04 install to fix the problems.

Download the iso from the ubuntu homepage.

Thank you, if all else fails I shall do that, now I understand. I am trying to avoid expensive (for me) download fees as I have already downloaded the files but will do some more general reading to see how others are going with the upgrade and what it offers- if it seems worthwhile, will have to do that all again. I tried to download from the ubuntu site and again, it started to download then it just hung. My network connection is fine, all other downloads are optimum.

I still would like to know why it stuck a dozen times on the last file and why it no longer offers any upgrade in update manager, these are bugs of course. Should they be reported somewhere?

---

### Post by jerome1232 on 2011-05-04
> **willyconkz said:**
> Yeah yeah, put your ego back in its box or bugger off, you are not helping me. Helpful is an attitude, not words. I am trying hard to be patient and work this out, pedantic arseholery really is worthless on your part with beginners who easily misunderstand. But then you know that, you just choose to be a fool.

I worked out what was meant by the session prompt at the bottom, there it also just offers ubuntu desktop or recovery or safe mode, no other options.

Excuse me? 

I was trying to help. I was giving you an upgrade option that is more reliable than a network upgrade, you never mentioned it's expensive for you to download data.

Lighten up and relax, my post was in no way meant to offend. Your's however...

---

### Post by jtarin on 2011-05-05
> **fremantle said:**
> how many times do i have to say, always start fresh with a new ubuntu release :)
Do you need an exact count?:P

---

### Post by jtarin on 2011-05-05
I'm not at home on my Ubuntu machine now but I had this problem upgrading to 10.10 and I can't remember exactly the procedure but in your /var/cache/apt/archives/partial folder see if there is any files there.....if yes delete them and try the upgrade again. Don't purge your already downloaded files only the ones in /partial.

---


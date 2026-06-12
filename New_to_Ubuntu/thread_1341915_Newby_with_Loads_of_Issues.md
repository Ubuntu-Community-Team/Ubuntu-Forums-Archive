---
title: "Newby with Loads of Issues"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by toxicblogger on 2009-11-30
Hi everyone.


I hope this is the right place to be.


I have 3 major problems with ubuntu as i speak


1 - Update manager is giving me the following problem


'E:Type '*' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'



How do i rectify this?

2 - Some windows applications do not install very well on wine for instance media monkey or my accounting software. How do i overcome this problem?


3 - Zekr installed from Ubuntu Software centre does not work.


Look forward to yourprompt and friendly assistance
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8413192") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8413192")

---

### Post by ukripper on 2009-11-30
post output of sources.list:
```
gedit /etc/apt/sources.list
```

> 3 - Zekr installed from Ubuntu Software centre does not work.
Elaborate on this one. what problem you are having?

---

### Post by toxicblogger on 2009-11-30
Hi and thanks for the feedback

> **ukripper said:**
> post output of sources.list:
```
gedit /etc/apt/sources.list
```


I tried this on the terminal but to no avail. I was asked on the absolute beginners forum to remove line 56. How do i do that?

> Elaborate on this one. what problem you are having?


It doesnt run at all.

---

### Post by soapytheclown on 2009-11-30
okay seen as gedit isnt working do this in a terminal and copy and paste the output here:

```

cat /etc/apt/sources.list

```

---

### Post by 3rdalbum on 2009-11-30
> **toxicblogger said:**
> Hi everyone.

I hope this is the right place to be.

I have 3 major problems with ubuntu as i speak

1 - Update manager is giving me the following problem

'E:Type '*' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

All lines in that file must begin with "deb", "deb-src" or the "#" symbol (that symbol means 'this is just a comment, not computer-readable').

Open a text editor as root:

```
gksudo gedit /etc/apt/sources.list
```

or

```
sudo nano /etc/apt/sources.list
```

And remove all lines that don't begin with any of those three things. Save your changes, exit and run the command:

```
sudo apt-get update
```

In future, DON'T modify this file directly. Use the Software Sources program to add and remove repositories. It prevents you from adding things that will break the package manager.


> 2 - Some windows applications do not install very well on wine for instance media monkey or my accounting software. How do i overcome this problem?

Use native Linux software. Statistically, Wine works for less than 50% of Windows software, so you'll be much happier leaving Wine as a last resort, and using native Linux software wherever possible.

> 3 - Zekr installed from Ubuntu Software centre does not work.

What are the symptoms? What happens if you run it in the terminal?

---

### Post by toxicblogger on 2009-11-30
Hi soapy the clown


Sure thing


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
* May 2007 (3
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (8)
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
    * May 2007 (38)
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (8)
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
    * May 2007 (38)
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)

---

### Post by toxicblogger on 2009-11-30
> **3rdalbum said:**
> All lines in that file must begin with "deb", "deb-src" or the "#" symbol (that symbol means 'this is just a comment, not computer-readable').

Open a text editor as root:

```
gksudo gedit /etc/apt/sources.list
```or

```
sudo nano /etc/apt/sources.list
```And remove all lines that don't begin with any of those three things. Save your changes, exit and run the command:

```
sudo apt-get update
```In future, DON'T modify this file directly. Use the Software Sources program to add and remove repositories. It prevents you from adding things that will break the package manager.




Use native Linux software. Statistically, Wine works for less than 50% of Windows software, so you'll be much happier leaving Wine as a last resort, and using native Linux software wherever possible.



What are the symptoms? What happens if you run it in the terminal?


Dude, I just posted the source list. I was wondering if you know which lines to edit?


And by native linux you mean software written for linux? Cos if thats so then my accounting software doesnt have a linux version.

---

### Post by snowpine on 2009-11-30
> **toxicblogger said:**
> Dude, I just posted the source list. I was wondering if you know which lines to edit?


And by native linux you mean software written for linux? Cos if thats so then my accounting software doesnt have a linux version.

Delete everything after this line:

```
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

You may need to dual boot with windows (or install windows in a virtual machine) to use your windows accounting software.

---

### Post by soapytheclown on 2009-11-30
Hi, 
As snowpine has said, get rid of everything from the line he says onwards.

You seemed to have put some install instructions in the file somehow which is breaking it. - if you didnt manually edit it when trying to install the 'zekr' program there seems to be a pretty big blunder somewhere.

after quickly googling, see if this is of more use to you, Its an islamic mod of Ubuntu which you may prefer?

[http://www.sabily.org/website/index.php/en/sabily/what-is-sabily](http://www.sabily.org/website/index.php/en/sabily/what-is-sabily)

---

### Post by 3rdalbum on 2009-11-30
> **toxicblogger said:**
> Dude, I just posted the source list. I was wondering if you know which lines to edit?

Remove everything that's written in English. It looks like you've pasted an entire web page into that file. The package manager only understands lines beginning with the words "deb" or "deb-src".

Actually, maybe it would be easier if I just told you to remove everything in that file, and then go to System > Administration > Software Sources and enable the "main", "restricted", "multiverse", "universe", "backports", "security" and "updates" repositories by clicking the little checkboxes.


> And by native linux you mean software written for linux? Cos if thats so then my accounting software doesnt have a linux version.

That's what I meant. You can try checking if your accounting software is listed on the Wine HQ website's "AppDB", to see if anyone has posted instructions on how to get your software working better. Or, the other option is to install Windows inside a virtual machine (that runs in a window on your Ubuntu desktop) and install your program inside that virtual machine.

---

### Post by toxicblogger on 2009-11-30
> **snowpine said:**
> Delete everything after this line:

```
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```You may need to dual boot with windows (or install windows in a virtual machine) to use your windows accounting software.



ok that progress. Now this is what i get after executing the change. Can you confirm if this is ok


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by toxicblogger on 2009-11-30
> **3rdalbum said:**
> Remove everything that's written in English. It looks like you've pasted an entire web page into that file. The package manager only understands lines beginning with the words "deb" or "deb-src".

Actually, maybe it would be easier if I just told you to remove everything in that file, and then go to System > Administration > Software Sources and enable the "main", "restricted", "multiverse", "universe", "backports", "security" and "updates" repositories by clicking the little checkboxes.




That's what I meant. You can try checking if your accounting software is listed on the Wine HQ website's "AppDB", to see if anyone has posted instructions on how to get your software working better. Or, the other option is to install Windows inside a virtual machine (that runs in a window on your Ubuntu desktop) and install your program inside that virtual machine.



Hey thanks a million guys. The update issue is sorted completely. But, Zekr is still not running. I need help there. 

I have installed it from Ubuntu Software Centre but nothing happens when i click on the button.


What should i do?

---


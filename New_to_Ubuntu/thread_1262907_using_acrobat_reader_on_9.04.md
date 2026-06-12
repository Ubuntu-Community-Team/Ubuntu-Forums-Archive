---
title: "using acrobat reader on 9.04 ?"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by jrev on 2009-09-10
How can I download the acroread package in order to use acrobat reader ?

I added the medibuntu depot already but cannot find the package "acroread" in synaptic...

Help Please 

and thank you in advance :P

---

### Post by credobyte on 2009-09-10
[LIST=1]
[*]Open Add/Remove
[*]Search for acrobat
[*]Select it
[*]Enable partner repositories
[*]Install
[/LIST]
Mediabuntu doesn't offer 32bit Acrobat Reader ;)

---

### Post by jrev on 2009-09-10
thanks for your answer but no, no answer for the word acrobat...
How about the apt/sources.list file ?
Have you got a copy ? :P

---

### Post by credobyte on 2009-09-10
> **jrev said:**
> thanks for your answer but no, no answer for the word acrobat...
How about the apt/sources.list file ?
Have you got a copy ? :P

Not sure about software sources list, however, you can enable them from [COLOR=RoyalBlue]System / Administration / Software sources[/COLOR] ( select Third party tab and check both partner repos ).

---

### Post by Excedio on 2009-09-10
Also, try typing acroread instead of acrobat in Add/Remove

---

### Post by jrev on 2009-09-10
> **Excedio said:**
> Also, try typing acroread instead of acrobat in Add/Remove

Also not successful : unknown name ! :KS

How did you install the sources ?

---

### Post by Excedio on 2009-09-10
Does someone know a command that will "export" my software sources to a text file?
 
If I can get thet, I can should you all my software sources. I do not know which of my sources holds my Adobe Reader, which I don't use anyway.
 
Edit: Had a thought. Make sure that when yuo are looking at Add/Remove you have it set to "Show: All Available Applications"

---

### Post by credobyte on 2009-09-10
> **Excedio said:**
> Does someone know a command that will "export" my software sources to a text file?
 
If I can get thet, I can should you all my software sources. I do not know which of my sources holds my Adobe Reader, which I don't use anyway.
 
Edit: Had a thought. Make sure that when yuo are looking at Add/Remove you have it set to "Show: All Available Applications"

```
cat /etc/apt/sources.list > $HOME/Desktop/sources.txt
```

-----------------

```
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
```

Uncomment these 2 lines & update your apt database ;)

---

### Post by jrev on 2009-09-10
> **Excedio said:**
> Does someone know a command that will "export" my software sources to a text file?  


Yes :
> cat /etc/apt/sources.list

then you copy/paste the result in your next post ...

Thanks Excedio 

to credobyte :Edit: Had a thought. Make sure that when yuo are looking at Add/Remove you have it set to "Show: All Available Applications"

I did it !

:P

---

### Post by Excedio on 2009-09-10
> **jrev said:**
> Yes :
 
cat /etc/apt/sources.list
 
:P
 
```

excedio@excedio-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) intrepid main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) intrepid main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main
 

```
 
These are all of my third-party software sources. I havn't goa clue which one will contain Adobe Reader.
 
Edit: Changed it to show the whole file.

---

### Post by credobyte on 2009-09-10
> **Excedio said:**
> ```

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) intrepid main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) intrepid main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main

```These are all of my third-party software sources. I havn't goa clue which one will contain Adobe Reader.

None of them ( see my previous post ) :)

---

### Post by Excedio on 2009-09-10
> **credobyte said:**
> None of them ( see my previous post ) :)
 
I edited my post to show the whole file. Hopefully that will be helpful.

---

### Post by credobyte on 2009-09-10
> **Excedio said:**
> I edited my post to show the whole file. Howfully that will be helpful.

Yeah, it should help him ( just because of the fact that you're on Hardy and he can copy/paste entries from your software sources file, without modifying anything ) :)

---

### Post by Excedio on 2009-09-10
> **credobyte said:**
> *snip*just because of the fact that you're on Hardy*snip*
 
 
<------------- Intrepid

---

### Post by jrev on 2009-09-10
thanks, but you are on "Intrepid" and I am on "jaunty" 9.04 in France !

Here is my sources.list :

> jean@jean:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty main restricted
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty universe
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates universe
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://fr.packages.medibuntu.org/](http://fr.packages.medibuntu.org/) jaunty free non-free
jean@jean:~$ 


I don't know what source is missing, do you ?

---

### Post by Excedio on 2009-09-10
> **jrev said:**
> thanks, but you are on "Intrepid" and I am on "jaunty" 9.04 in France !
 
Need to update your profile info...says you're on Hardy...
 
I don't know if this would work, but.....would simply changing all the 'intrepid' to 'jaunty' work?

---

### Post by credobyte on 2009-09-10
> **Excedio said:**
> <------------- Intrepid

Woops :oops:

> **jrev said:**
> thanks, but you are on "Intrepid" and I am on "jaunty" 9.04 in France !

You haven't read all the replies in this thread. I already gave you the lines you need to add/enable to your sources file.

---

### Post by Excedio on 2009-09-10
> **credobyte said:**
> ```
cat /etc/apt/sources.list > $HOME/Desktop/sources.txt
```
 
-----------------
 
```
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
```
 
Uncomment these 2 lines & update your apt database ;)
 
Hint hint

---

### Post by jrev on 2009-09-10
> **credobyte said:**
> Woops :oops:



You haven't read all the replies in this thread. I already gave you the lines you need to add/enable to your sources file.

Thanks, I will check the new edition :lolflag:

---

### Post by ainsworth_t on 2009-09-10
If you're having problems getting it from the repositories, you can always download it directly from the Adobe web site, add execute permissions to the bin file, then execute it.

---

### Post by jrev on 2009-09-10
> **ainsworth_t said:**
> If you're having problems getting it from the repositories, you can always download it directly from the Adobe web site, add execute permissions to the bin file, then execute it.

I think i will follow your advice. Thanks

---

### Post by ainsworth_t on 2009-09-10
> I think i will follow your advice. Thanks
Sounds good. Let us know if you need more detailed instructions for that procedure.

---

### Post by jrev on 2009-09-10
I made a > chmod 755 AdbeRdr9.1.2-1_i486linux_fra.bin

but cannot execute this *.bin file on the Desk !
Got the answer : > unknown file type 

in french : type de fichier inconnu

---

### Post by aysiu on 2009-09-10
> **jrev said:**
> thanks for your answer but no, no answer for the word acrobat...
How about the apt/sources.list file ?
Have you got a copy ? :P
It's not called *Acrobat* anything. It's called *acroread*.

**Step 1**: Make sure you have the proper repositories enabled
Go to System > Administration > Software Sources
Under third-party, make sure the Partner repositories are enabled

**Step 2**: Install Acrobat Reader
Go to System > Administration > Synaptic Package Manager
Search for *acroread*
Right-click to mark it for installation. Click Apply.

---

### Post by wojox on 2009-09-10
You could always double click the pdf and have Evince open it.

---

### Post by aysiu on 2009-09-10
> **wojox said:**
> You could always double click the pdf and have Evince open it.
Or you could just download this file and double-click to install it:
[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.0-7jaunty2_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.0-7jaunty2_i386.deb)

---

### Post by jrev on 2009-09-10
> **aysiu said:**
> It's not called *Acrobat* anything. It's called *acroread*.

**Step 1**: Make sure you have the proper repositories enabled
Go to System > Administration > Software Sources
Under third-party, make sure the Partner repositories are enabled

**Step 2**: Install Acrobat Reader
Go to System > Administration > Synaptic Package Manager
Search for *acroread*
Right-click to mark it for installation. Click Apply.

found it at last in synaptic
thanks everybody :guitar:

---

### Post by Excedio on 2009-09-10
> **jrev said:**
> found it at last in synaptic
thanks everybody :guitar:
Glad you got everything working. If you are able to can you mark the thread solved for people who stumble across this in the future?

---

### Post by jrev on 2009-09-20
Acroread doesnt run on all computers.
I just bought a PC from Iventive France and when I want to open a PDF file this PC freezes solid and only the start button can restart it
:guitar:

---


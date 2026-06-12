---
title: "Trying to install LibreOffice 3.3"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Edward in CT on 2011-03-12
Dear Friends,

I've been trying to install Libre Office 3.3 on my Dell Vostro 1500 running Ubuntu 10.04.  I've been able to download the archive from a Linux format disk, copy it to it's own folder and extract the files from the folder.  What I can't do is intall the files.  I've been trying to use a package manager but errors always occur.  Does anyone have simple instructions for a relative new Linux user on how to install Libre Office?  Thanks

Ed

---

### Post by beew on 2011-03-12
You can install it from a ppa.

[https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa")

I have installed it by downloading a tar.bz file before the PPA was available but I had to first convert rpm packages to deb using alien and then run dpkg.

It is a lot easier to install via ppa and you get automatic updates.

---

### Post by roger_1960 on 2011-03-12
Hi

Have you looked at the instructions and downloads on [www.libreoffice.org](www.libreoffice.org)

---

### Post by drdos2006 on 2011-03-12
There is an easier way.

[http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml](http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml)

regards

---

### Post by beew on 2011-03-12
> **drdos2006 said:**
> There is an easier way.

[http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml](http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml)

regards

That is an odd instruction, why is he running all the commands out of the run box as root? (instead of using sudo in a terminal)

After removing previously installed Libreoffice versions, just add the ppa to the sources list and install.

Adding source with GUI:

First go to System > Administration > Synaptic Package Manager. Open  Synaptic and click Settings > Repositories on the top bar, then go to the tab Other Software and then add>  ppa:libreoffice/ppa, then  close the dialogue box, click "Reload" and then install Libreoffice from Synaptic and that's it.

---

### Post by Edward in CT on 2011-03-12
So I tried to go to Synaptic and I get a dialog box which says
'E: Malformed line 54 in source list /etc/apt/sources.list (dist),  E the list of sources could not be red.'

so I went to /etc/apt/sources.list.d and found libreoffice-ppa-lucid.list.  Clicked on it and got what looks like a text file.  The only text was deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) lucid main.

I'm basically a beginner and clueless.  How can I at least get package manager to work again so I can try all of the clever ideas alluded to above?

Thanks

Ed

---

### Post by beew on 2011-03-12
> **Edward in CT said:**
> So I tried to go to Synaptic and I get a dialog box which says
'E: Malformed line 54 in source list /etc/apt/sources.list (dist),  E the list of sources could not be red.'

so I went to /etc/apt/sources.list.d and found libreoffice-ppa-lucid.list.  Clicked on it and got what looks like a text file.  The only text was deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) lucid main.

I'm basically a beginner and clueless.  How can I at least get package manager to work again so I can try all of the clever ideas alluded to above?

Thanks

Ed

Hmm.. That is weird may be something get corrupted. just delete libreoffice-ppa-lucid.list and add it again and see what happens. I am using the ppa in Lucid and haven't got a problem.

Alternatively you can add the source and install using the terminal. In the terminal type

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```

---

### Post by Edward in CT on 2011-03-13
Tried to delete libreoffice-ppa-lucid.list in the terminal (with sudo priviledges) and it will not let me.  I can't use synaptic package manager now.  When I try, I get the "malformed line 54..." notice.  Can I remove and reinstall the package manager and stop this whole mess?

Thanks,
Ed

---

### Post by dnairb on 2011-03-13
The error you got was:

> **Edward in CT said:**
> 
'E: Malformed line 54 in source list /etc/apt/sources.list (dist),  E the list of sources could not be red.'

and yet you:

> **Edward in CT said:**
> went to /etc/apt/sources.list.d and found libreoffice-ppa-lucid.list.

To fix the reported error, in terminal type (or copy and paste):

```
gksudo gedit /etc/apt/sources.list
```

and look at line 54 (which is near the bottom, possibly the last line)

---

### Post by Edward in CT on 2011-03-13
Ok that got somewhere.  I got the source.list but it had no line numbers so I put cat /etc/apt/sources.list -n and got this...



orestes@orestes-laptop:~$ gksudo gedit /etc/apt/sources.list
orestes@orestes-laptop:~$ cat /etc/apt/sources.list -n
     1    # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
    15    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
    23    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
    24    
    25    ## Uncomment the following two lines to add software from the 'backports'
    26    ## repository.
    27    ## N.B. software from this repository may not have been tested as
    28    ## extensively as that contained in the main release, although it includes
    29    ## newer versions of some applications which may provide useful features.
    30    ## Also, please note that software in backports WILL NOT receive any review
    31    ## or updates from the Ubuntu security team.
    32    # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    33    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    34    
    35    ## Uncomment the following two lines to add software from Canonical's
    36    ## 'partner' repository.
    37    ## This software is not part of Ubuntu, but is offered by Canonical and the
    38    ## respective vendors as a service to Ubuntu users.
    39    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    40    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    41    
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
    44    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
    45    deb [http://download.tuxfamily.org/gericom/libreoffice/](http://download.tuxfamily.org/gericom/libreoffice/)

There is no line 54 to fix or delete.  Can I delete the whole file and replace it?  Why is it complaining about line 54 when there isn't any code on one?  Sorry to ask stupid questions but I have very little experience with command line (or any other) programming.  I just want to install LibreOffice or at least get Synaptic back.

Thanks,
Ed

---

### Post by dnairb on 2011-03-13
OK. So let's see what is in the /etc/apt/ folder.
In terminal:

```
ls /etc/apt/
```

EDIT: forget the above.

Are you sure that the error reported line "54" and not "45"?

In terminal:

```
gksudo gedit /etc/apt/sources.list
```

and delete the last line:

```
deb http://download.tuxfamily.org/gericom/libreoffice/
```

then save the file

---

### Post by Edward in CT on 2011-03-15
That worked perfectly.  Thanks so much for your help.
I only wish I actually understood what I just did instead of simply following your directions.  I wish there was a book: "Beginning Linux for Dummies."  I'd buy it right away.

Thanks again.  I'm very grateful for your assistance.

Ed

---

### Post by ahso4271 on 2011-03-15
What's the difference from libre to openoffice? or why libreoffice was created out of openoffice?

---

### Post by dnairb on 2011-03-15
> **Edward in CT said:**
> That worked perfectly.  Thanks so much for your help.
I only wish I actually understood what I just did instead of simply following your directions.  I wish there was a book: "Beginning Linux for Dummies."  I'd buy it right away.

Thanks again.  I'm very grateful for your assistance.

Ed

You're welcome.

---

### Post by lotharmat on 2011-03-17
> **ahso4271 said:**
> What's the difference from libre to openoffice? or why libreoffice was created out of openoffice?


Oracle bought Sun (or was it vice versa) Oracle now own the name Open Office

Libre Office is the non-oracle version of Open Office 

(I think that is how it went...)

---

### Post by Flutemaker on 2011-03-17
There's a big issue (at least it's big for people who are affected by it) about the icons that ship now with OpenOffice and their lack of colour coding, which helps to distinguish between the different types and enable you to find them a bit quicker in long file lists.

This was raised as issue a good few times and a lot of people just want the old icons back.
Oracle or the OpenOffice developers or the people behind it don't seem to take this issue serious enough to do something about it and that's why a lot of people swap over to LibreOffice which seems to be run by a lot of the developers who used to work on OpenOffice. Why they jumped ship, I don't know and it's not my business...

Personally, I don't like the monochrome icons and decided to go for LibreOffice after a good ten years of OpenOffice. It's running side by side at the moment, but if OpenOffice is continuing to ignore this issue, I might swap entirely...
I do also miss the colours that aren't used any more in the latest iTunes editions, the en vogue thing in the digital world seems to be grey and monochrome and blue... Makes you wonder why we came up with 32bit colours in the first place...

My five cents...
;)



> **lotharmat said:**
> Oracle bought Sun (or was it vice versa) Oracle now own the name Open Office

Libre Office is the non-oracle version of Open Office 

(I think that is how it went...)

---

### Post by JMichaelAnderson on 2011-03-18
I've done something wrong.  I get the following message:
compassbearer@compassbearer-AOD255E:~$ sudo apt-get clean
[sudo] password for compassbearer: 
compassbearer@compassbearer-AOD255E:~$ sudo apt-get clean
compassbearer@compassbearer-AOD255E:~$ sudo apt-get update
E: Malformed line 59 in source list /etc/apt/sources.list (type)
E: The list of sources could not be read.
compassbearer@compassbearer-AOD255E:~$ cat /etc/apt/sources.list
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
sudo tee -a /etc/apt/sources.listm/ubuntu maverick-security multiverse
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O-

---

### Post by JMichaelAnderson on 2011-03-18
> **drdos2006 said:**
> There is an easier way.

[http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml](http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml)

regards
I get the following message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by howefield on 2011-03-18
Sounds like you have more than one package manager open, (update manager / synaptic / software centre ect ect).

Close them all down and then try again.

---


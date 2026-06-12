---
title: "Adobe reader for 64 bit ubuntu 9.04"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by bappy004 on 2009-05-26
Hi all,
I wanna install Adobe reader in Ubuntu 9.04 64 bit edition. i saw in some sites that adobe has no 64 bit edition for linux. is it true? if not true, please someone help me  by describing the procedure of installing 64 bit adobe reader in UBUNTU 9.04.
thanks in advance

---

### Post by presence1960 on 2009-05-26
there is no 64bit version. you have 2 choices: 1. go to [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) and choose your version and download either the .deb or .bin Adobe Reader or 2. in terminal run ```
sudo apt-get install acroread
```

---

### Post by Mornedhel on 2009-05-26
Out of curiosity, why do you specifically need Adobe Reader ? There are several alternatives which you might want to check and a PDF reader installed by default (Evince).

---

### Post by jespdj on 2009-05-26
> **presence1960 said:**
> ... or 2. in terminal run ```
sudo apt-get install acroread
```
But acroread is not in the standard Ubuntu repository, so this will not just work. You can get acroread for 64-bit Ubuntu from the [Medibuntu](http://medibuntu.org/) repository. Follow [the instructions](https://help.ubuntu.com/community/Medibuntu) to add the Medibuntu repository to your sources.list and then enter the apt-get command to install Acrobat Reader.

---

### Post by presence1960 on 2009-05-26
> **jespdj said:**
> But acroread is not in the standard Ubuntu repository, so this will not just work. You can get acroread for 64-bit Ubuntu from the [Medibuntu](http://medibuntu.org/) repository. Follow [the instructions](https://help.ubuntu.com/community/Medibuntu) to add the Medibuntu repository to your sources.list and then enter the apt-get command to install Acrobat Reader.

thanks forgot that as one of the first things I do after install is enable medibuntu. Two sets of eyes are always better than one set!

---

### Post by XCan on 2009-05-26
> **Mornedhel said:**
> Out of curiosity, why do you specifically need Adobe Reader ? There are several alternatives which you might want to check and a PDF reader installed by default (Evince).

I'm actually looking for alternatives for Evince as well, so please share if you have any worthwhile. I find the rendering of Evince sometimes strange, and simply have been using Adobe Reader since it better represents my printed versions. Also a small picky is that by default Evince prints the colored boxes to 'bookmarks' in a PDF, probably easy to turn off but I haven't messed around with it.

---

### Post by philinux on 2009-05-26
> **bappy004 said:**
> Hi all,
I wanna install Adobe reader in Ubuntu 9.04 64 bit edition. i saw in some sites that adobe has no 64 bit edition for linux. is it true? if not true, please someone help me  by describing the procedure of installing 64 bit adobe reader in UBUNTU 9.04.
thanks in advance

Click the medibuntu link in my signature. Follow all the instructions. Acroread will then be in synaptic. However I would not install mozilla-acroread. It has a bug which causes cpu to go high and a bad memory leak.

---

### Post by bkline on 2009-07-09
> **Mornedhel said:**
> Out of curiosity, why do you specifically need Adobe Reader ? There are several alternatives which you might want to check and a PDF reader installed by default (Evince).

Perhaps because the alternatives aren't able to print many of the PDFs out there (for example, the forms from the US IRS)?

---

### Post by Mornedhel on 2009-07-09
> **bkline said:**
> Perhaps because the alternatives aren't able to print many of the PDFs out there (for example, the forms from the US IRS)?

No need to be like that, it was an honest question, to make sure the OP was aware that Evince was already installed, and wasn't just trying to install Adobe Reader to open normal PDFs when Evince could have done fine.

Now I'm sorry, but I have never come across a PDF Evince wasn't able to render. I will admit that since I have not tried to read every existing PDF, there are bound to be several out there (for instance every PDF with forms, which is still not a lot of PDFs), but my anecdotal evidence contradicts your anecdotal evidence.

Also, I do not consider "the forms from the US IRS" to be "many of the PDFs out there".

This is semi-unrelated and only my opinion (well, mine and a lot of people's as well), but PDF is a *terrible* choice for interactive documents (forms, javascript, etc.). It's a *publishing* medium. Tell your government to use secure online HTML forms instead.

---

### Post by aspergerian on 2009-12-21
For my uses, I need often to quote from medical article pdfs. Adobe Reader is the only one I've found that can copy from a column w/o including lines from a different column. My Ubuntu 9.10 64 bit needs a pdf reader that can copy from within a column. Is there a 64-bit Ubuntu-worthy alternative to Adobe Reader that can copy from within a column?

---

### Post by Mornedhel on 2009-12-21
If my memory serves correctly, kpdf has a rectangular selection mode, so that should work.

---

### Post by aspergerian on 2009-12-21
> **Mornedhel said:**
> ...kpdf...

Mornedhel, 

Thnx for the suggestion. I'll try kpdf and report back.

---

### Post by plucky on 2009-12-22
> **aspergerian said:**
> For my uses, I need often to quote from medical article pdfs. Adobe Reader is the only one I've found that can copy from a column w/o including lines from a different column. My Ubuntu 9.10 64 bit needs a pdf reader that can copy from within a column. Is there a 64-bit Ubuntu-worthy alternative to Adobe Reader that can copy from within a column?

Add the "partner" repository and install acroread in Ubuntu 9.10 64-bit.


Good Luck

---

### Post by aspergerian on 2009-12-22
> **plucky said:**
> Add the "partner" repository and install acroread in Ubuntu 9.10 64-bit.

I'm still sufficiently noob-esque that I don't know how to add the partner repository.

---

### Post by aspergerian on 2009-12-22
Solution that worked on my Acer 1410 solo core, via:
[http://ubuntuforums.org/showthread.php?p=8542306#post8542306](http://ubuntuforums.org/showthread.php?p=8542306#post8542306)

```
sudo apt-get install ia32-libs
```

```
cd Downloads
```

For now, the specification is:
```
sudo dpkg --force-architecture -i AdbeRdr9.2-1_i386linux_enu.deb
```

---

### Post by plucky on 2009-12-22
> **aspergerian said:**
> I'm still sufficiently noob-esque that I don't know how to add the partner repository.

**System > Administration > Software Sources**
 Enter your password and then select "Other Software " tab.

Tick the box that says "http://archive.canonical.com/ubuntu karmic partner"

Close and select reload.(this will update your repository information)

Open Synaptic Package Manager and search for "acroread" and select to install,then apply.

Or from a terminal ```
sudo apt-get install acroread
``` to install acroread

Good Luck

---

### Post by aspergerian on 2009-12-22
> **plucky said:**
> **System > Administration > Software Sources**
Enter your password and then select "Other Software " tab.
Tick the box that says "http://archive.canonical.com/ubuntu karmic partner"
Close and select reload.(this will update your repository information)
Open Synaptic Package Manager and search for "acroread" and select to install,then apply.
Or from a terminal ```
sudo apt-get install acroread
``` to install acroread


Although I've used those procedures while running 32 bit Ubuntu, those steps do not bring forth acroread via Synaptic Package Manager or via apt-get on my Acer 1410 running 9.10 64 bit. Those approaches were the first things I tried. That's why I had to keep searching for a way to install Adobe Reader on my Acer 1410 with 64 bit 9.10.

---

### Post by philinux on 2009-12-22
It's definitely in partner on 9.10, as I've installed it this way via synaptic only a couple on months ago.

---

### Post by llawwehttam on 2009-12-22
You could try Foxit. Its not my preference as I just stick with evince but it works.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by plucky on 2009-12-22
> **aspergerian said:**
> Although I've used those procedures while running 32 bit Ubuntu, those steps do not bring forth acroread via Synaptic Package Manager or via apt-get on my Acer 1410 running 9.10 64 bit. Those approaches were the first things I tried. That's why I had to keep searching for a way to install Adobe Reader on my Acer 1410 with 64 bit 9.10.


I am running 64 bit ubuntu and it works for me ```
Linux Petersville 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
```
**Have you got the partner repositories enabled?**

I have just enabled it and it is definitely there.```
sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2 libgnome-speech7
The following NEW packages will be installed
  acroread
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 63.5MB of archives.
After this operation, 153MB of additional disk space will be used.
Get: 1 http://archive.canonical.com karmic/partner acroread 9.2-1karmic1 [63.5MB]
Fetched 63.5MB in 2min 10s (486kB/s)                                           
Preconfiguring packages ...
Selecting previously deselected package acroread.
(Reading database ... 168930 files and directories currently installed.)
Unpacking acroread (from .../acroread_9.2-1karmic1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up acroread (9.2-1karmic1) ...

```

Please post the output from a terminal of ```
cat /etc/apt/sources.list
```


Good Luck

---

### Post by aspergerian on 2009-12-22
> **plucky said:**
> Please post the output from a terminal of ```
cat /etc/apt/sources.list
```

tcb@tcb:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
tcb@tcb:~$

---

### Post by plucky on 2009-12-22
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner


So your partner repository is enabled.

From a terminal ```
sudo apt-get update
``` will update your sources information and ```
sudo apt-get install acroread
``` will install Adobe Reader.

I see [here](http://ubuntuforums.org/showpost.php?p=8542306&postcount=8) that you have installed Adobe Reader on your 64 bit system.

Please mark thread as **solved** from the **Thread Tools** above

Good Luck

---

### Post by aspergerian on 2009-12-22
Plucky, 

Previously, Adobe Reader had installed into my Acer 1410 via steps delineated in post #15 in this thread. A few minutes ago, I did the two steps you set forth in post #22 which caused Adobe Reader to download again and to replace the Adobe Reader which sequence in post #15 had downloaded. Seems that there are at least two ways to install AR on a machine running 64 bit 9.10. 

Thnx for taking time to reply in depth.

---

### Post by zuber786 on 2009-12-22
why do you wanna use adobde reader
there are better readers out there for ubuntu

---

### Post by aspergerian on 2009-12-22
I clicked on Thread Tools, looked at the page for quite a while, saw nothing indicating how to mark the thread as [SOLVED], so I'll try putting that into the subject heading myself.

---

### Post by plucky on 2009-12-23
> **aspergerian said:**
> I clicked on Thread Tools, looked at the page for quite a while, saw nothing indicating how to mark the thread as [SOLVED], so I'll try putting that into the subject heading myself.

Sorry I forgot,only the original poster can mark the thread that is shown in the Index as solved.

Thanks for the update

Good Luck

---


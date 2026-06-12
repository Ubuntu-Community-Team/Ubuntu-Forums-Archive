---
title: "Micro. Money clone:  gnucash vs homebank ?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-23
[http://www.gnucash.org/](http://www.gnucash.org/)
or
[http://homebank.free.fr/index.php?id=4](http://homebank.free.fr/index.php?id=4)

Which one is the closer to such good Microsoft, and has as much features such as planner, graphs, reports, overview over year?

---

### Post by bodhi.zazen on 2010-09-23
IMO kmymoney is closest.

---

### Post by honeybear on 2010-09-23
> **bodhi.zazen said:**
> IMO kmymoney is closest.
```

The following NEW packages will be installed:
  akonadi-server kaboom kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdoctools kmymoney kmymoney-common libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1
  libaqbanking29-plugins-qt4 libattica0 libboost-program-options1.42.0 libclucene0ldbl libgpgme++2 libiodbc2 libkabc4 libkcal4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdnssd4 libkfile4 libkholidays4 libkhtml5 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4
  libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libnepomuk4 libnepomukquery4a libplasma3 libpolkit-qt-1-0
  libq4banking1 libqt4-opengl libqt4-svg libraptor1 librasqal2 librdf0 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0 mysql-server-core-5.1 oxygen-icon-theme plasma-scriptengine-javascript shared-desktop-ontologies soprano-daemon
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
The following packages will be upgraded:
  libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsqlite3-0 qt4-qtconfig
14 upgraded, 78 newly installed, 0 to remove and 201 not upgraded.
Need to get 58.7MB/109MB of archives.
After this operation, 205MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.at.debian.org squeeze/main libsqlite3-0 3.7.2-1 [382kB]
Get:2 http://ftp.at.debian.org squeeze/main qt4-qtconfig 4:4.6.3-1+b1 [143kB]
Get:3 http://ftp.at.debian.org squeeze/main libqt4-qt3support 4:4.6.3-1+b1 [1,421kB]
1% [3 libqt4-qt3support 511kB/1,421kB 35%]^C
```

- well : kmymoney requires too much packages, too sql
limited in grahphcis => so : forget about kmymoney although it seems to be  the best of best for linxu. It is although poor compared to quicken or ms microsoft money

- [http://www.mint.com/?cid=quicken](http://www.mint.com/?cid=quicken) 
needs linux?

- quicken: wine => forget => bug and slow
- ms money wine => forget => bug and slow

- gnucash: destined to usual human? far from ms money
and dedicated to customers or factory

- homebank
   bad import, and very limited
   you cannot even repeat a payment unless you fight with the program like stupid. No simulatiosn over years for budget/money
 
- others:
moneydance
it is a java thing; looks the best of the best, but too complicated and not nicely coded. It is in java, and look better than linux protertiy porograms

Forget finances under linux, bit like always, and good game gaming too :)


Solution: buy a Mac !

---

### Post by PaulW2U on 2010-09-23
> **honeybear said:**
> Forget finances under linux, bit like always,
I came to the pretty much the same conclusion that you did, there is nothing available that compares to either Quicken or MS Money. And that is just one of many reasons that I will always have to use Windows. But while I'm using Linux I just use a spreadsheet that I'm developing and update MS Money when I can.

Not ideal but it works......for me.

---

### Post by bodhi.zazen on 2010-09-23
> **honeybear said:**
> Solution: buy a Mac !

As you wish. I would not buy a mac just because Ubuntu asks I install those additional packages.

I agree with your observations, I was suggesting kmymoney is the closest. If it does not meet your needs, stay with MS. Windows or MAC.

---

### Post by honeybear on 2010-09-23
> **bodhi.zazen said:**
> As you wish. I would not buy a mac just because Ubuntu asks I install those additional packages.

I agree with your observations, I was suggesting kmymoney is the closest. If it does not meet your needs, stay with MS. Windows or MAC.
thanks
quicken rocks really and is also for mac
ms money, rocks too, and no one can say that those are most simple and can do most things than any other program.
if you need good products, please run for them (with mac or windows)


I found this one; it has the most basic functions:

- repeat bill/income monthly
- make graphs over years 

I mean why not to make it easy

[http://www.badger-finance.org/index.php?option=com_remository&Itemid=40&func=select&id=12](http://www.badger-finance.org/index.php?option=com_remository&Itemid=40&func=select&id=12)

---

### Post by eneville on 2011-05-14
I don't see any problem with either homebank or gnucash. They do different jobs, homebank appears to be easier for me, gnucash is a little harder, but if you know what you're doing, or what you want to achieve then both should be quite adequate.

---

### Post by jawolf3 on 2011-05-23
Can anyone help me with printing checks from gnucash? I was able to load my QIF file and gnucash seems to have gotten that right. Following the help instructions for printing has not worked - the printer spits out blank pages. I try to print the search results and use "print" in the number cell of each record in the register to get the checks in a search window for printing -- file, print checks. Not working. What don't I understand?

---

### Post by HermanAB on 2011-05-23
Only Americans still use checks.  The rest of the world abandoned cheques many years ago and moved on to electronic transfers.  So you are out of luck...

You could try SQL-Ledger, but it is aimed at business users.

Otherwise, install Virtualbox/VMware/KVM and use a WinXP virtual machine for Quicken/Quickbooks.

---

### Post by jelabarre on 2013-01-21
> **honeybear said:**
> [CODE]
...Solution: buy a Mac !
 
From what I've seen about Quicken for the Mac, you'd *still* get better functionality on a Linux system :confused:.  I think Intuit never recovered from deciding to abandon the Apple platform months before the iMac came out and revived the Macintosh platform, and Apple in general.  So their sunsequent products have (apparently) been cr*p.
 
No matter for me, I still run Quicken98 for Windows, never needed to upgrade, and since the Linux equivalents don't print checks very well (if at all in many cases), haven't found a usable FLOSS replacement.

---

### Post by oldos2er on 2013-01-22
Old thread closed.

---


---
title: "adobe reader install problems"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by VVAW on 2011-06-21
I need to install a older version 
I donwload 8.1.7 deb file try to install with ubuntu software center
I get this error message
Wrong architecture 'i386'

There is only 1 file to download

---

### Post by wolfen69 on 2011-06-21
You must be using 64bit ubuntu. The file is for 32bit systems. You could try:
```
sudo dpkg -i --force-architecture filename.deb
```

---

### Post by beew on 2011-06-21
Why would you want that resource hogging monster?  Downloading ~ 100+ mb to open pdf is ridiculous. Ubuntu comes with a pdf reader.

---

### Post by VVAW on 2011-06-21
I need  FileOpen Plug-in  to view files 
is there something I can use for this

---

### Post by dFlyer on 2011-06-21
I believe if you install the 32bit lib you will be able to run adobe reader on your 64bit system. Someone correct me if I'm wrong, but I run bibble5 on my wifes 64bit system which is a 32bit program.

---

### Post by VVAW on 2011-06-21
> **wolfen69 said:**
> You must be using 64bit ubuntu. The file is for 32bit systems. You could try:
```
sudo dpkg -i --force-architecture filename.deb
```

this didn't work

---

### Post by Perfect Storm on 2011-06-21
Adobe reader is available through Ubuntu Software Center (also for 64-bit systems via 32-bit libs). The package is called acroread.


Or by terminal:
```
sudo apt-get install acroread
```

---

### Post by VVAW on 2011-06-21
This is the newer version 9 I need older for FileOpen Plug-in to work

---

### Post by Perfect Storm on 2011-06-21
> **VVAW said:**
> This is the newer version 9 I need older for FileOpen Plug-in to work

ok. Then what wolfen69 said should work.

Download adobe here: [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

Choose v8.1.7

```
sudo apt-get install ia32-libs
cd /where/the/file/is
sudo dpkg -i --force-architecture filename.deb
```

I have tested this, should work.

---

### Post by VVAW on 2011-06-21
Note very new to this

Error


lt:~/Downloads$ sudo dpkg -i --force-architecture AdobeReader_enu-8.1.7-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package adobereader-enu:i386.
(Reading database ... 162762 files and directories currently installed.)
Unpacking adobereader-enu:i386 (from AdobeReader_enu-8.1.7-1.i386.deb) ...
dpkg: dependency problems prevent configuration of adobereader-enu:i386:
 adobereader-enu:i386 depends on libgtk2.0-0 (>= 2.4).
dpkg: error processing adobereader-enu:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobereader-enu:i386

---

### Post by Perfect Storm on 2011-06-21
Which version of Ubuntu do you use?

---

### Post by dFlyer on 2011-06-21
Install the 32bit lib. You could try sudo apt-get -f install which might pull in the 32bit lib, but not sure since your running in the 64bit environment.

---

### Post by VVAW on 2011-06-21
> **dFlyer said:**
> Install the 32bit lib. You could try sudo apt-get -f install which might pull in the 32bit lib, but not sure since your running in the 64bit environment.

Same problem

I am running 11.04

---

### Post by jtarin on 2011-06-21
If you want to open PDF files inside Firefox you need to install mozplugger.mozplugger allows you to seamlessly integrate external applications to view files downloaded from the web that Mozilla can not normally handle. The application is embedded within a Mozilla window as to act like and feel like a true plugin.

This allows you to view PDFs, Postscript files, animations and movies, amongst other file types all from within Mozilla (with supporting applications).

Install mozplugger in ubuntu

   ```
 sudo apt-get install mozplugger
```

And there is also.......[this]("https://addons.mozilla.org/en-US/firefox/addon/pdf-download/")

---

### Post by beew on 2011-06-21
> **jtarin said:**
> If you want to open PDF files inside Firefox you need to install mozplugger.mozplugger allows you to seamlessly integrate external applications to view files downloaded from the web that Mozilla can not normally handle. The application is embedded within a Mozilla window as to act like and feel like a true plugin.

This allows you to view PDFs, Postscript files, animations and movies, amongst other file types all from within Mozilla (with supporting applications).

Install mozplugger in ubuntu

   ```
 sudo apt-get install mozplugger
```And there is also.......[this]("https://addons.mozilla.org/en-US/firefox/addon/pdf-download/")

No it wouldn't work the FifeOpen plugin is a DRM thing that works only on Adobe.

---

### Post by jtarin on 2011-06-21
> **beew said:**
> No it wouldn't work the FifeOpen plugin is a DRM thing that works only on Adobe.FifeOpen plugin ???? Not familiar with that plugin????

---

### Post by jtarin on 2011-06-21
I just setup Firebird to use "Evince".Very quick opening.
Go to Firefox 
Menu>Edit>Preferences>Applications>PDF Document>select /usr/bin/evince

[You can test it here.]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBkQFjAA&url=http%3A%2F%2Fwww.tagg.org%2Fpdftest.pdf&rct=j&q=small.pdf&ei=EkkATsWtFcvJsgbx1aiXDQ&usg=AFQjCNHH_UE_EpcvEsRpVN0LtCHKq-iqHA&cad=rja")

---

### Post by beew on 2011-06-21
> **jtarin said:**
> FifeOpen plugin ???? Not familiar with that plugin????

I didn't know about that either. After reading OP's reply (#4) I googled and found a site (Numerical Recipe, I actually I have the book ) which required FO to access their electronic version online.  It is a DRM thing that no pdf reader other than ADOBE supports.  But they have since got rid of the requirement because too many Linux users are having problems. :)

[http://www.nr.com/forum/showthread.php?t=1798](http://www.nr.com/forum/showthread.php?t=1798)

---

### Post by mahmoodkamal on 2011-06-21
> **beew said:**
> I didn't know about that either. After reading OP's reply (#4) I googled and found a site (Numerical Recipe, I actually I have the book ) which required FO to access their electronic version online.  It is a DRM thing that no pdf reader other than ADOBE supports.  But they have since got rid of the requirement because too many Linux users are having problems. :)

[http://www.nr.com/forum/showthread.php?t=1798](http://www.nr.com/forum/showthread.php?t=1798)


Have you tried Foxit Reader ???

---

### Post by beew on 2011-06-21
> **mahmoodkamal said:**
> Have you tried Foxit Reader ???

I don't need to access the site so I don't need the plugin.:) But no, according to the sites' FAQ nothing else would work but Adobe, that applies to all OSes.

But they have gotten rid of the requirement anyway, that of course doesn't solve OP"s problem unless he is trying to access Numerical Recipes.

Anyway Foxit for Linux is crap, it couldn't even open its own manual and it has been dead for over almost two years,--no longer supported. Why would anyone want the crappy toss away from a company which only cares about Windows? Evince is much better and Okular has way more features.

---

### Post by jtarin on 2011-06-21
> **beew said:**
> I don't need to access the site so I don't need the plugin.:) But no, according to the sites' FAQ nothing else would work but Adobe, that applies to all OSes.

But they have gotten rid of the requirement anyway, that of course doesn't solve OP"s problem unless he is trying to access Numerical Recipes.

Anyway Foxit for Linux is crap, it couldn't even open its own manual and it has been dead for over almost two years,--no longer supported. Why would anyone want the crappy toss away from a company which only cares about Windows? Evince is much better and Okular has way more features.First time I heard about that plug-in and really have no use with organizations and their DRM when it comes to things like that. And your right....Foxit sucks. :)

---

### Post by VVAW on 2011-06-21
anybody on this I need to install a older version of adobe reader on 64 bit ubuntu 11.04

---

### Post by sadaruwan12 on 2011-06-21
You could use WINE and install a older windows version.

---

### Post by mahmoodkamal on 2011-06-22
> **beew said:**
> I don't need to access the site so I don't need the plugin.:) But no, according to the sites' FAQ nothing else would work but Adobe, that applies to all OSes.

But they have gotten rid of the requirement anyway, that of course doesn't solve OP"s problem unless he is trying to access Numerical Recipes.

Anyway Foxit for Linux is crap, it couldn't even open its own manual and it has been dead for over almost two years,--no longer supported. Why would anyone want the crappy toss away from a company which only cares about Windows? Evince is much better and Okular has way more features.

I am surprised as when i go to foxit website it shows version which is 2 year old but check the below link

[http://www.raiden.net/node/106](http://www.raiden.net/node/106)

where is the updated version???

---

### Post by centguy on 2012-12-20
I have spent hours after hours trying to install acroread

using AdbeRdr9.1.3-1_i386linux_enu.deb  AdbeRdr9.5.1-1_i386linux_enu.deb  AdobeReader_enu-8.1.7-1.i386.deb

on my 

Linux mint14-dell 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

(sorry I take the liberty of using mint and ubuntu interchangbly! educate me if
needed !)


but I keeping hitting a problem related to


adobereader-enu depends on libgtk2.0-0 (>= 2.4)

or similar problem.

I searched many sites but the only conclusion I have right now since 
ubuntu camp has not welcome acroread package.

Okay, if evince can support multitab like acroread then I will stop 
installing acroread on ubuntu/LinuxMint. But it seems I 
have somewhat disappointed by my luck so far.. 
what I want is a multitab functionality like I used to have with acroread
on other Linux OSes ..

The deb package GUI installation keeps saying:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cairo/libcairo2_1.12.2-1ubuntu2.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cairo/libcairo2_1.12.2-1ubuntu2.1_amd64.deb) 404  Not Found [IP: 91.189.92.201 80]

I search [http://archive.ubuntu.com/ubuntu/pool/main/c/cairo](http://archive.ubuntu.com/ubuntu/pool/main/c/cairo) and found that
the problem seems to be that 2.1 version is removed by the 2.2 version.

I downloaded a 2.1 deb from somewhere and did a dpkg -i, and I think 
I have broken the system ??

Anyway, I am `shopping' from other OS and trying to find out if LinuxMint can
satisfy my usual habbit but I am rather tired now after trying so many options !

If it is relevant please look into this issue seriously!

---

### Post by oldos2er on 2012-12-20
Old thread closed, please start a new thread. If you're using Mint, please give their forums a try: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---


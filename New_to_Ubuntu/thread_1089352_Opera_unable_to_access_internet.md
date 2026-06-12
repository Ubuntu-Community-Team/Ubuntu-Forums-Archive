---
title: "Opera unable to access internet"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by g1d2r3 on 2009-03-07
Hi,

Yesterday I installed opera on my machine.The .deb package was downloaded from opera website.Synaptic shows that opera is installed.But i am unable to access any website using opera.
The reason for me using opera is that i unable to login to my drupal installation using firefox.It shows a blank page when i login.

The other reason is I am unable to install internet explorer because  i think the installer cannot find a package online
this line i had paste in /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe

installation gives me following error:


IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install everything at: /home/gauresh/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXE   mfc42.cab
   0%   IEDOM.CAB   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/gauresh/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/gauresh/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/gauresh/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S2.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S3.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S4.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S5.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/IE_S6.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/gauresh/.ies4linux/downloads/ie6/EN-US/VGX.CAB: WARNING; possible 6896 extra bytes at end of file.
 An error occured when trying to cabextract some files.


Please help me with this. It would be great if you could provide me with some other alternative to access drupal site.
Thanks

---

### Post by Xiong Chiamiov on 2009-03-07
Don't install things using .debs from sites; use [the package manager](http://www.psychocats.net/ubuntu/installingsoftware) instead.

IEs4Lin is a bit finicky; sometimes it will work if you just try it again later.

Firefox shouldn't be having problems with sites; do you have the same problem using Firefox on other computers?  Have you installed any add-ons?  If you have, do you still have problems after disabling them and restarting Firefox?

Put long segments of code inside [noparse]```

```[/noparse] tags; it makes it easier to read.

---

### Post by g1d2r3 on 2009-03-10
Sorry for replying so late.
Yes I had a problem accessing my drupal site through firefox on windows Os too.I have tried Epiphany but I am getting the same problem.
The package of opera in repositories has some problems.Can you tell me any other browser that i should try.

---

### Post by mbzn on 2009-03-10
You may try Konqueror.

---

### Post by dstin1 on 2009-03-10
I installed opera a few days ago from [here ]("http://www.opera.com/browser/download/") it installed flawlessly and works fine.

---

### Post by clive littlewood on 2009-03-10
Hi

I have just accessed the Drupal site with both Opera and Firefox, so methinks you have a deeper problem than just browsers.

Can you access other sites ok ?

Do you have any filters in Firefox ?

Clive

---

### Post by 16sinker on 2009-03-14
Since this thread still seems to be open I hope I'm not violating Forum protocol by addressing a seperate Opera issue. That issue is that I got Opera with synaptic package manager rather than a .deb package and it doenn't appear in my sources.list. Opera runs fine and I really have no problem with it. I was just wondering if the absence in Sofware Sources is a problem.

---


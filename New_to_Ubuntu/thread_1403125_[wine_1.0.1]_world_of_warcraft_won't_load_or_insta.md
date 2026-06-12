---
title: "[wine 1.0.1] world of warcraft won't load or install"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Abkajud on 2010-02-09
Hey, gang!
This is my very first Ubuntu Forums thread, so be gentle ... and speak in simple terms! ^_^

Here's my relevant info, for starters:
CPU - 1.40 Ghz Intel Core2 Duo
RAM - 2014 MB, 501 free
Graphics card -  Intel Corporation Mobile GM965/GL960
Wine version # - 1.0.1
Ubuntu version - 8.10 Intrepid 

So. Here's my problem: I DL'ed Wine, I DL'ed the installer client for WoW, and then I managed to successfully install the client onto my computer. *Then*, when I told the computer to go ahead and install the actual program, it crashed, and Wine referred me to the Wine website to search for any proof that this bug had already been reported. 

It hasn't, so here I am! Sound and visuals all check out just fine while it's doing its thing, and Wine seems to be working properly, but when I try to install the WoW client, it either crashes at some point, or just never works at all, i.e. I tell it to run the installer.exe and it does nothing at all.

Help!
- Zac

---

### Post by RodrigoRodrigues on 2010-02-09
Have you ever run this game under any wine version?

it's your first thread but are you new to linux?

try running in terminal (wine install.exe) and see what error you get. sometimes a dll is needed.

also try to intall the latest wine version, for me some programs only run in version 1.1.3x

it´s not avaible for ubuntu so download the debian one ( [http://www.lamaresh.net/binary.php](http://www.lamaresh.net/binary.php) ), will install and shoud work fine...

> **Abkajud said:**
> Hey, gang!
This is my very first Ubuntu Forums thread, so be gentle ... and speak in simple terms! ^_^

Here's my relevant info, for starters:
CPU - 1.40 Ghz Intel Core2 Duo
RAM - 2014 MB, 501 free
Graphics card -  Intel Corporation Mobile GM965/GL960
Wine version # - 1.0.1
Ubuntu version - 8.10 Intrepid 

So. Here's my problem: I DL'ed Wine, I DL'ed the installer client for WoW, and then I managed to successfully install the client onto my computer. *Then*, when I told the computer to go ahead and install the actual program, it crashed, and Wine referred me to the Wine website to search for any proof that this bug had already been reported. 

It hasn't, so here I am! Sound and visuals all check out just fine while it's doing its thing, and Wine seems to be working properly, but when I try to install the WoW client, it either crashes at some point, or just never works at all, i.e. I tell it to run the installer.exe and it does nothing at all.

Help!
- Zac

---

### Post by yazmonium on 2010-02-10
you may need to run winetricks to install directx9 and an xml parser.  Instructions can be found at [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by Abkajud on 2010-02-10
Thanks for the speedy reply, everyone!
To answer your question, Rodrigo, I am new to Linux. 
Secondly, when I tried the terminal command you suggested, I was told "module not found". I have Wine; I've checked for it. And the WOW installation files are definitely on my computer. When I run "wine installer.exe" or "wine installwow.exe" in my terminal, nothing happens. 
I downloaded the version of Wine you recommended, as well, but that doesn't seem to have changed anything except that now Wine no longer appears under my Apps dropdown menu; it's lurking somewhere, but I don't see it where it's "supposed to" be.

One last thing: aside from 1.0.1 and 1.1.38, I've not tried to run this program (WoW, that is) through Wine before.

Yaz, thanks for the winetricks tip - I downloaded the recommended directX version; sadly that doesn't seem to have affected things either, but maybe I'm not at a point in the process yet where video stuff matters ^_^

---

### Post by sxmaxchine on 2010-02-10
i didnt seem to have any problems at all getting wow to run and im pretty sure i was using wine 1.0.1, although i had WOW installed on a portable hard drive and played it from that, also i used ubuntu 9.04

---

### Post by Abkajud on 2010-02-10
OK, new info!
I got the terminal command figured out with WoW, and it opened the installer *through* terminal - - very fancy! 
I then got this helpful error message, which may be of use: 

> fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
abkajud@abby-lappy:~$ fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
So something isn't talking to something else. I downloaded Firestarter firewall manager, and I've been following the instructions [here]("https://help.ubuntu.com/community/WorldofWarcraft#Alternative%202%20%28Download%20the%20Entire%20Game%29:"). Any suggestions?

Thanks!

---


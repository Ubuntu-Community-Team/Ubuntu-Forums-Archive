---
title: "Picasa photo's"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by jenelle on 2011-01-21
just a question or 2

i got a new a new computer brain to replace the one that decided to stop working i had only got a new screen 2 weeks before melt down, i have only just got the old linux ubuntu to update cause at first it would not [from an old disk ] so i think i am either 10.4 or 10.10 ?? where do i look to find out which i am ??


i want to down load picasa
this i did get it on my computer just before it crashed [my brother down loaded it for me but lives other side of town ] 



    * rpm, for Red Hat/Fedora/Suse/Mandriva i386 or x86_64:
      [http://dl.google.com/linux/rpm/testing/i386/picasa-3.0-current.i386.rpm](http://dl.google.com/linux/rpm/testing/i386/picasa-3.0-current.i386.rpm)

    * deb, for Debian/Ubuntu i386:
      [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

    * deb, for Debian/Ubuntu amd64:
      [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb)

All downloads are approximately 30 MB: Picasa software (13 MB), Wine (11 MB) and Gecko engine (6 MB). 

i don't think i use the first one but i am not sure which to click on with the next 2 ?
anyone give me an idea 
??
i am not 100% sure on doing this i don't know when my brother will be back down this way .

---

### Post by mike555 on 2011-01-21
If you have the 32bit regular Ubuntu use the middle one ,the .deb for 32bit.

---

### Post by jenelle on 2011-01-21
how do i find out if i have the 32 bit ubuntu ?? i think it is a good chance it is but if i want to make sure sorry

---

### Post by Verbeck on 2011-01-21
> **jenelle said:**
> how do i find out if i have the 32 bit ubuntu ?? i think it is a good chance it is but if i want to make sure sorry
type *uname -m* into a terminal (applications>accessories)
if it says i686, then it's 32 bit

---

### Post by jenelle on 2011-01-21
cool thanks was the 32 bit just learnt a new thing :D

> **mike555 said:**
> If you have the 32bit regular Ubuntu use the middle one ,the .deb for 32bit.

thank you for your help too i am now down loading it :D

downloaded it but something slightly went wrong if i put it on a disk would it matter if it was - or +

---

### Post by oldfred on 2011-01-21
I just install wine, winetricks, fonts and then download the latest windows picasa. I am currently using 3.8.


My old notes:
                       [SIZE=2]http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019[/SIZE]
    [LEFT][SIZE=2]http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html[/SIZE][/LEFT]
    [LEFT][SIZE=2]But I never installed Picasa 3.0[/SIZE][/LEFT]
    [LEFT][SIZE=2]http://ubuntuforums.org/showthread.php?t=1385837[/SIZE][/LEFT]
        [LEFT][SIZE=2]  114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/LEFT]
    [LEFT][SIZE=2]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/LEFT]
    [LEFT][SIZE=2]  116  sudo chmod 777 winetricks[/SIZE][/LEFT]
    [LEFT][SIZE=2]  117  sudo apt-get install cabextract wine wine-gecko[/SIZE][/LEFT]
    [LEFT][SIZE=2]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/SIZE][/LEFT]
    [LEFT][SIZE=2]Then download picasa for windows (changed to 3.8)
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/SIZE][/LEFT]
    [LEFT][SIZE=2]rename to picasa and move to wine programs first
[/SIZE][/LEFT]

---

### Post by dFlyer on 2011-01-21
to determine what version of Ubuntu your running type the following at the command prompt:

more /etc/lsb-release

---

### Post by jenelle on 2011-01-21
i now know it is the 32 bit one :-) 
i think it needs tweeking though only just got it all updated on my new computer as old one had melt down sadly 
i will try again when my brother is down i did down load it just would not fit where it was going i think it said
i got all my photo's on picasa just so much easier to up load if it is on the computer

---


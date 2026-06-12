---
title: "Canon ip4600 printer"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by chinner459 on 2011-08-29
I am trying to use a Canon iP4600 printer with Ubuntu 11.4 and although the system recognises the printer it will not print from the default paper cassette although it will print if fed from the rear tray by hand.  I have downloaded drivers for Debian Linux from Canon but have no real idea how to handle them.  Help would be appreciated

---

### Post by jerrrys on 2011-08-29
please post the download link

---

### Post by chinner459 on 2011-08-31
> **jerrrys said:**
> please post the download link

The download link I used is as follows


[http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)

from which I downloaded the file  iP4600_debian_tar  but I'm not sure what to do with it as I am a new newbie

---

### Post by jerrrys on 2011-08-31
i downloaded the ip4600 driver, which seems to be the same package as the 1900 and doesn't look like its seen an update since 2008.

anyhow, it would not install.  saying broken/unmet dependencies

you may find a answer here

  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ip4600+printer+canon&sa=Search&cof=FORID:9#866](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ip4600+printer+canon&sa=Search&cof=FORID:9#866)

good luck

---

### Post by chinner459 on 2011-09-15
> **jerrrys said:**
> i downloaded the ip4600 driver, which seems to be the same package as the 1900 and doesn't look like its seen an update since 2008.

anyhow, it would not install.  saying broken/unmet dependencies

you may find a answer here

  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ip4600+printer+canon&sa=Search&cof=FORID:9#866](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ip4600+printer+canon&sa=Search&cof=FORID:9#866)

good luck

Thanks.  The unmet dependency appears to be libcupsys2 which is not installed.  I have searched the web and found a libcupsys2 which I have installed but it does not seem to work.

---

### Post by Azdour on 2011-09-16
Hi,

I believe libcupsys2 has been superceded by lipcups2. There is an old thread here about installing the Canon ip9100:

[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

I'm not sure how useful it will be for you.

I also note you have another thread open on the Canon ip4600. Have you tried to install the Canon using post number 5?

---


---
title: "wubi installer fails to install xubuntu"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Xenphor on 2010-05-16
Hello

I've tried both the regular ubuntu and xubuntu wubi installers and have encountered the same problem. I let the wubi installer download the required iso and let it reboot and proceeded to install. 

At 79% the installer hangs for quite awhile and I get an error message that says "Apt Config Problem: Attempt to install packages from the CD Failed." Then it appears to search (through the internet?) for servers to download the packages. After this I get a message that the installer has suffered an unrecoverable error and must reboot. If I try to install again the same thing happens.

Do I need some sort of CD for it to install additional programs? I was under the impression that the wubi installer downloaded everything it needed and then installed by itself. Also, I used a wireless connection so I don't see how it could get files from the internet when it has not allowed me to choose my wireless signal and security settings. 

I have a Toshiba Satellite M-45 Laptop

Thanks for the help.

---

### Post by meborc on 2010-05-18
I just recently installed Xubuntu using Wubi and for me it worked well

are you using the latest Wubi? You can download the iso yourself and place it in the same folder as Wubi.exe, it should then use the downloaded iso as the image. You can verify if the downloaded image is fine using md5sum

---


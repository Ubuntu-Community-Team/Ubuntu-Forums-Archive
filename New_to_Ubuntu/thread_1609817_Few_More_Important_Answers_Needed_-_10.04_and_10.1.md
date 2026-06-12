---
title: "Few More Important Answers Needed - 10.04 and 10.10"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by D3SI on 2010-10-30
i have completely removed the Ubuntu from my System (Again) due to some issues  but i wanna make Ubuntu my Default OS and get rid of Windows for good so  can learn about Ubuntu is well...

1. first of all which ver sion is better to have if i wanna keep the system updated and easy to upgrade when new version comes out?

2. is it a good idea to move completely to Ubuntu from Windows?

3. lets say if am installing a software on Ubuntu using Terminal and i messed it up half way (for example PS3 Media Server for Ubuntu)...  how do i remove that software? (one of the reasons i removed Ubuntu)

---

### Post by shrimpy89 on 2010-10-30
Everybody's got a different opinion, but here's mine:

1. It's equally easy to upgrade each of them.  10.04 is the long term stable release, meaning it's supported for 3 years on the desktop with security updates and such.  Being a long term release, it's supposed to be more solid and stable.  10.10 was just recently released;  it contains newer versions of the software, so if you want the latest and greatest get 10.10.

2.  I recommend keeping Windows around, personally.  I'm a university student and ya never know when I'll get a class that requires using a Windows program.  Granted, I haven't used mine for months, but better safe than sorry, right?

3.  You'll have to be a little more specific on this one.  Were you downloading by apt-get/aptitude, .deb, or compiling from source?

---

### Post by WeAreLinux on 2010-10-30
1. I would suggest 10.04 since it's an LTS version. After using 10.04 for a while, you can then easily upgrade to 10.10 via the Update Manager. Between 10.04 & 10.10, there's really no major upgrade, so you could decide to stick with 10.04. It's your preference.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

2. Depends on the user. If you depend heavily on programs that only run in Windows (MS Office, Photoshop, etc.), then it might not be a good idea. On Linux, there's an alternative to almost everything with open-source software, but some users require MS programs. You also should know, you can run Window programs within Linux using Wine or Virtual Machines but sometimes are not a complete solution.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)

3. You should be able to remove the software via apt command but I'm not 100% sure if the program didn't install properly.

[https://help.ubuntu.com/community/AptGet/Howto#Removal%20commands](https://help.ubuntu.com/community/AptGet/Howto#Removal%20commands)

---

### Post by janpol on 2010-10-30
> **D3SI said:**
> i have completely removed the Ubuntu from my System (Again) due to some issues  but i wanna make Ubuntu my Default OS and get rid of Windows for good so  can learn about Ubuntu is well...

1. first of all which ver sion is better to have if i wanna keep the system updated and easy to upgrade when new version comes out?

2. is it a good idea to move completely to Ubuntu from Windows?

3. lets say if am installing a software on Ubuntu using Terminal and i messed it up half way (for example PS3 Media Server for Ubuntu)...  how do i remove that software? (one of the reasons i removed Ubuntu)
1. For this matter, neither version is better than the other. I just suggest you to try the latest (10.10). Use 10.04 if you prefer a LTS (Long Term Support) version. If you don't like upgrading every 6 months, just go with 10.04. Also, some people say that some version detects their drivers better than the other. 

2. It depends on your needs (I use only Ubuntu, but keep a Windows partition around in case I want to play Windows games), make a dual-boot, try to use only Ubuntu, and decide for yourself.

3. That depends, if you use apt, you can use the command:

```
apt-get remove package
```

Also, you can search for the package in the Software Center, and Uninstall it from there using a nice GUI

If you install a package by hand (./configure, make, make install), just run from the same folder you installed the package:

```
make uninstall
``` 

If you deleted that folder, you'll have to go to every folder and delete files by hand.

And, if you have any problem among the way, just come back here and we'll be glad to help you, this is the best part of using linux, the community :)

Good Luck!

---

### Post by papibe on 2010-10-30
> **D3SI said:**
> 1. first of all which ver sion is better to have if i wanna keep the system updated and easy to upgrade when new version comes out?
I's recommend you to use 10.04 LTS (long term support). In my opinion 10.10 is too fresh.

> **D3SI said:**
> 2. is it a good idea to move completely to Ubuntu from Windows?

That's a tough one. It all depends the work you do, the apps you used, etc. In general, it would be safer to have windows as an option. After you spend more time using Ubuntu, and feel more confident, you could take that decision with more groundings.

> **D3SI said:**
> 3. lets say if am installing a software on Ubuntu using Terminal and i messed it up half way (for example PS3 Media Server for Ubuntu)...  how do i remove that software? (one of the reasons i removed Ubuntu)
I don't understand the example you gave, but most of the software for Ubuntu is easily removable. That is the case for software you install using the software center, and the apt-get command. Also, most independent packages that you download have an "make uninstall" option.

Did it help?

---

### Post by tanjeen on 2010-10-30
I don't understand the example you gave, but most of the software for Ubuntu it's easily removable. That is the case for software you install using the software center, the apt-get command, and most independent download packages have an "ma uninstall" option.

---

### Post by D3SI on 2010-10-30
ok, thanks for the answers for far..

1. on download page it doesn't  explain difference between 10.04 and 10.10, if i install 10.04 will it ask me to update to 10.10? (cause otherwise i might just install 10.10 if its gonna have same updates)

2. about that removing PS3 Media Server (was using this guide: [http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4253](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4253))  went half was and it didnt work and i didnt know how to remove what i've installed so far..

3. About Dual Boot...  i've tried over 10 times but haven't managed to use Windows Boot loader to show up Ubuntu..  i dont like Grub Loader as its not that neat.   if there any proper guide which shows what to do from beginning (how to install  to get ubuntu in Windows Loader )

4. lets say i choose 10.04   should i get 32Bit or 64Bit?   i have 6GB RAM

---

### Post by papibe on 2010-10-31
> **D3SI said:**
> 1. on download page it doesn't  explain difference between 10.04 and 10.10, if i install 10.04 will it ask me to update to 10.10? (cause otherwise i might just install 10.10 if its gonna have same updates)
No, you'll be kept inside that "family". You'll get update but they will be named something like 10.04.1.

> **D3SI said:**
> 4. lets say i choose 10.04   should i get 32Bit or 64Bit?   i have 6GB RAM
Although it's getting close every day, I still think 32bits have more apps available. Note that Ubuntu DOES NOT have the limitation of 4Gb of RAM as 32bits version of windows.

Regards.

---

### Post by GabrielYYZ on 2010-10-31
> **papibe said:**
> Note that Ubuntu DOES NOT have the limitation of 4Gb of RAM as 32bits version of windows.

Regards.

that only works if there's a connection available during installation, if the installation happens without a connection present it defaults to the generic kernel, not the PAE. 

(just thought i'd clarify that, someone might read that, do an offline install and find that the detected memory is still 3.x gb. and go "WHHHYYYY!!!???")

---

### Post by D3SI on 2010-10-31
when you say connection available.. you mean Internet Connection?

if yes then why is that?

please answer #3 question

Thank You

---

### Post by janpol on 2010-10-31
> **D3SI said:**
> 
3. About Dual Boot...  i've tried over 10 times but haven't managed to use Windows Boot loader to show up Ubuntu..  i dont like Grub Loader as its not that neat.   if there any proper guide which shows what to do from beginning (how to install  to get ubuntu in Windows Loader )

I don't know how Windows boot loader is neater than grub (they do the same thing, both do it well, and both are ugly). If you want something more eyecandy, try BURG.

[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/]("http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/")

Also, there isn't much information available about windows boot loader, compared with the tons of documentation about grub. And they are just boot loaders (and also there are other boot loaders available), don't waste your time.

Regards

---

### Post by GabrielYYZ on 2010-10-31
> **D3SI said:**
> when you say connection available.. you mean Internet Connection?

if yes then why is that?

please answer #3 question

Thank You

indeed, by connection available i mean internet connection. and the reason for that is that, when an internet connection is available, ubuntu auto updates itself during the install and, if it detects 4gb or more, the PAE kernel gets installed.

---

### Post by D3SI on 2010-10-31
installed Burg and got exactly what I wanted from Start.

 Thank You ;)

now only thing left is Ubuntu Logo on Start up it has lower Res for some reason.

---

### Post by Jechem on 2010-10-31
maybe this can help you: [http://ubuntuforums.org/showthread.php?t=1472951](http://ubuntuforums.org/showthread.php?t=1472951)

---


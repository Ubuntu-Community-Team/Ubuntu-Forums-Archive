---
title: "How do I install i-scan?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Thirskman on 2011-07-24
I downloaded iscan from Avasys so I can use my epson 3490 photo, and it downloads into the download folder, but then when I follow instructions for installation nothing happens. What am I doing wrong? Where should I save the files? And which package should I use? I am using Natty Narwhal.

---

### Post by amjjawad on 2011-07-24
> **Thirskman said:**
> I downloaded iscan from Avasys so I can use my epson 3490 photo, and it downloads into the download folder, but then when I follow instructions for installation nothing happens. What am I doing wrong? Where should I save the files? And which package should I use? I am using Natty Narwhal.

Hello and Welcome :)

Are you sure the file(s) that you downloaded is/are compatible with Linux?

---

### Post by Thirskman on 2011-07-24
Well - according to the website it is! I downloaded iscan-2.10.0-1.c2.i386.rpm. Is that the right one? I am running Ubuntu 11.04. I also downloaded iscan_2.10.0-1.tar.gz. At the moment both are sitting in my downloads folder.

---

### Post by amjjawad on 2011-07-24
> **Thirskman said:**
> Well - according to the website it is! I downloaded iscan-2.10.0-1.c2.i386.rpm. Is that the right one? I am running Ubuntu 11.04. I also downloaded iscan_2.10.0-1.tar.gz. At the moment both are sitting in my downloads folder.

.rpm is (if I'm not wrong) for Fedora and other Redhat OS.

not sure about .tar.gz ... perhaps you need an application to open it.

What I'm sure about is .deb is what you can use by default in Ubuntu.

---

### Post by egalvan on 2011-07-24
> **amjjawad said:**
> .rpm is (if I'm not wrong) for Fedora and other Redhat OS.


yep, RPM is RedHat
[COLOR="Red"]R[/COLOR]edHat [COLOR="Red"]P[/COLOR]ackage [COLOR="Red"]M[/COLOR]anager

> 
not sure about .tar.gz ... **perhaps you need an application to open it**.

No, its a Linux-native tar'd/zipped file...
merely double-clicking will open it up.

> What I'm sure about is .deb is what you can use by default in Ubuntu.

"alien" will convert from .rpm to .deb, but  you're right, its better to get the .deb from the manufacturer...

---

### Post by amjjawad on 2011-07-24
> **egalvan said:**
> 
No, its a Linux-native tar'd/zipped file...
merely double-clicking will open it up.


Good to know that, thanks :)

---

### Post by egalvan on 2011-07-24
> **amjjawad said:**
> Good to know that, thanks :)

spread the knowledge, FOSS/OSS will one day rule!

---

### Post by Thirskman on 2011-07-25
Thanks that's very helpful - except a .deb version is not available. Any good sources where I can get one?

---

### Post by beew on 2011-07-25
> **Thirskman said:**
> Thanks that's very helpful - except a .deb version is not available. Any good sources where I can get one?

Are you sure? You should check the web site again.

But if indeed a .deb is not available you may be able to convert the .rpm into a .deb using alien.

first install alien 
```
sudo apt-get install alien 
```Then cd into the folder where your .rpm file is , say it is in Desktop (if it is in your Home then you don't need to do anything)

```
cd Desktop
```Then run alien
```

sudo alien -k name_of_rpm_package.rpm
```If everything works you will get a .deb package in the same folder, then just install it the usual way,--by right clicking or in the terminal

```
sudo dpkg -i name_of_deb_package.deb
```Now you may get error messages either during conversion or when you try to install the deb, usually this is because some dependencies are missing. If that happens check the error messages and install the missing dependencies, hopefully you can find them in the repo, then redo the conversion with alien if required.

---

### Post by Thirskman on 2011-07-27
Hi thankyou. There is definitely not a .deb available in relation to the Epson 3490.

I have used alien to convert the .rpm file, and installed it; however, first it does not show up in my list of installed applications in the software centre, and second, the computer still cannot recognise the scanner. Grr. This is enough to make me go back to Windows!

---

### Post by amjjawad on 2011-07-27
> **Thirskman said:**
> Hi thankyou. There is definitely not a .deb available in relation to the Epson 3490.

I have used alien to convert the .rpm file, and installed it; however, first it does not show up in my list of installed applications in the software centre, and second, the computer still cannot recognise the scanner. Grr. This is enough to make me go back to Windows!

Don't lose hope ;)

While your machine is on, unplug your scanner, reboot your machine, login to Ubuntu and plug the scanner back.

If nothing will happen, maybe you need to re-install the package?

---


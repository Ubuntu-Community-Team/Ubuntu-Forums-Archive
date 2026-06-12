---
title: "How do I run Kindle on Maverick"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by bwallum on 2011-02-18
Hi

How do I set up Kindle on Maverick?

---

### Post by blazemore on 2011-02-18
Could you just provide a little bit more information?
Are you trying to run the "Kindle for PC" program on Ubuntu?

---

### Post by blazemore on 2011-02-18
**HOW TO: **Install the "Kindle for PC" program on Ubuntu

**Step 1:**
Open the Ubuntu Software Centre (in the Applications) menu

**Step 2:**
Using the search box in the top-right corner, search for "wine"

[B]Step 3:
[/B]Install Wine by clicking the install button. The program's name is "Windows compatibility layer" or similar.

[B]Step 4:
[/B]Download [this file]("http://d1xhj100piaj9u.cloudfront.net/25338/KindleForPC-installer.exe"), which is a slightly older version known to work on Ubuntu.

**Step 5:**
Because the .exe file was downloaded from the Internet, and is potentially untrusted, Ubuntu won't let you just run it. You need to right-click on the file and select Properties. Then go to the Permissions tab, and tick the box marked "allow executing this file"

[B]Step 6:
[/B]Right-click on the file and select open with -> Wine

[B]Step 7:
[/B]Follow the installation procedure, but **do not** select the option to automatically run it at the end, as the program will crash.

[B]Step 8:
[/B]Go to Applications -> Wine -> Wine Configuration.
Open the Applications tab, and click Add Application.
Using the file browser that appears, navigate to Program Files\Amazon\Kindle for PC
Select the file "KindleForPC.exe", and change the Windows version to "Windows 98" using the drop-down.
Click OK to save your changes.

[B]Step 9:
[/B]The Kindle app is in Applications -> Wine.
You can also drag this launcher to your desktop or panel.

[B]Step 10:
[/B]Profit
[]("http://d1xhj100piaj9u.cloudfront.net/25338/KindleForPC-installer.exe")

---

### Post by ShakeyJake on 2011-02-18
Calibre should recognise it straight away. Just install calibre from the software centre.

---

### Post by Grenage on 2011-02-18
Yes, Calibre is an excellent program.  If you *need* to plug the Kindle into a PC, I'd use it.

---

### Post by bwallum on 2011-02-19
Thanks all, I've gone down the Calibre route for now. It doesn't seem to be available from the software centre. However it is in synaptic. So, for any followers navigate to:-

System>Administration>Synaptic Package Manager then search for calibre and apply

---

### Post by Hatsune Miku on 2011-02-19
> **bwallum said:**
> Thanks all, I've gone down the Calibre route for now. It doesn't seem to be available from the software centre. However it is in synaptic. So, for any followers navigate to:-

System>Administration>Synaptic Package Manager then search for calibre and apply

If it the device, just plug it in. All it does is mount it as a fat32 volume >.>

---

### Post by Old_Man_Unix on 2011-02-19
> **Hatsune Miku said:**
> If it the device, just plug it in. All it does is mount it as a fat32 volume >.>

+1

If you merely want to directly transfer files from your Ubuntu system to your Kindle Reader, simply plug the Reader  into a USB port.  I've transferred many files in this way with no problem.  The files must be transferred into the Documents folder on your Reader.  Of course, the files must be in a format that the Reader recognizes.

You can also convert unprotected PDF files - and some other format files - to Kindle Reader  files if you want to.  This will often make them easier to use on your Reader - especially long files or e-books.  Amazon provides this as free service for Kindle owners.   Simply email them the file(s) as instructed and you will have the converted file(s) returned to your email address and to your Kindle Reader via Wi-Fi. 

Linux utilities and programs to do this are also available but I've never had the need to use them since the free Amazon service is available to me. 

If you want to read the DRM-restricted AZW files in Ubuntu - the ones that Kindle uses natively - your best bet is to wait for Amazon to release a Kindle Application for Linux.  The other "solutions" are not so good, according to the conventional wisdom.

---

### Post by Old *ix Geek on 2011-02-19
It's ABSURD that Amazon--a company built on Linux--puts out a product, the Kindle--also built on Linux, but ignores its Linux users. I hope all of you who want a native Kindle application for Linux take the time to contact Amazon and let them know. Honestly, NOTHING will change if we don't speak up because silence is interpreted as meaning there is no market/interest.

---

### Post by gavinjb on 2011-02-24
Hi,

Not sure if anyone can help just got wine1.3 install and Kindle for PC, but when I try and register Kindle for PC all I get is

```

Registration timed out. Please try again

```

Can anyone help.

Thanks,



Gavin,

---

### Post by Nutbun on 2011-02-24
You register through your wifi from the kindle itself don't you?  I did anyway.  After that I just manage my kindle through Calibre.

---

### Post by gavinjb on 2011-02-25
> **Nutbun said:**
> You register through your wifi from the kindle itself don't you?  I did anyway.  After that I just manage my kindle through Calibre.

This is on KindleforPC running in Wine and not the Kindle Device

---

### Post by clive littlewood on 2011-02-25
Just as an after thought the excellent Calibre program can convert most ebook formats to the Kindle format.

---


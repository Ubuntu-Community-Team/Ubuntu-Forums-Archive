---
title: "Cleaning PCs with Rootkits"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by TIGGER959 on 2009-09-22
a) Is there any literature I can read regarding cleaning windows based PCs with rootkits on them?

b) Can you use ubuntu to boot to an XP based PC and modify the registry?

All help is appreciated.

---

### Post by halitech on 2009-09-22
look here: [http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

### Post by JuergenF on 2009-09-22
> a) Is there any literature I can read regarding cleaning windows based PCs with rootkits on them?I don't think there can be a HOWTO. This would need a lot of knowledge and time and be rootkit-dependent anyway.
Your best option is IMHO to use linux to save the user-data and re-install.
> b) Can you use ubuntu to boot to an XP based PC and modify the registry?AFAIK you can use wine to edit an exported registry. But to export and later import this registry you have to boot your infected Windows. So even that is probably not very useful...

---

### Post by TIGGER959 on 2009-09-22
I hate to show my ignorance but I am not good with the acronyms. i.e., IMHO.  In addition, what is wine other than dry, red or white?

---

### Post by TIGGER959 on 2009-09-22
Thanks!  I've got a program that will let me change passwords.  Didn't know of one that would let me edit the registry.

---

### Post by halitech on 2009-09-22
WINE - WINE Is Not an Emulator

[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

its a *nix program that allows you to run *some* windows programs and games

did you try the offline tool I posted a link to? it has a built in windows registry tool.

---

### Post by TIGGER959 on 2009-09-22
Just finished supper.  Will be downloading and trying it tonight.  I pulled the drive from the infected computer, scanned it w/Malwarebytes, and will now boot to the PC and try the program.

---

### Post by t0p on 2009-09-22
> **TIGGER959 said:**
> Thanks!  I've got a program that will let me change passwords.  Didn't know of one that would let me edit the registry.

If your computer has been rooted, changing the password is not a solution.  You need to remove the rootkit.  But, as has already been suggested, you'd probably be best off backing up your data and reinstalling Windows.  A rooted computer is *not* secure.

---

### Post by JuergenF on 2009-09-22
> I am not good with the acronyms.I don't know if they are used frequently in web-forums - maybe they are a just a remnant of the time I did most of my blabla in USENET-forums...
AFAIK = As Far As I Know
IMHO = In My Humble Opinion
Most you can probably just ignore, but if you want to find out about one you can probably find it at [thefreedictionary]("http://acronyms.thefreedictionary.com/")

---

### Post by jflaker on 2009-09-22
The only sure fire way to make sure you really cleaned the system is to wipe it clean and re-install


Backup all the data then use the system restore disk and you should be good to go.  

after 21+ years dealing with systems of all types, it is more economical to wipe/install than to try to troubleshoot and hope you got the actual culprit....

---

### Post by TIGGER959 on 2009-09-22
Thanks, I added to my Toolbar.

---


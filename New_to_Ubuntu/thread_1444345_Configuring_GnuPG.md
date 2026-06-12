---
title: "Configuring GnuPG"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Bob Henson on 2010-04-01
I'm using Linux Mint 8 Helena, and am a complete newbie to Linux. I want to add a configuration file to GnuPG to modify the way that Enigmail (in Thunderbird) displays information in the Key Mangager - particularly the "clean" command. In Windows it's easy- I edit a text file with the commands in, call it gpg.conf and stick it in the same directory as my keyrings. How do I go about it in Ubuntu? AFAICS, the GPG executable is in /users/bin - do I put a text file in that directory? 

Regards,

Bob

---

### Post by Diabolis on 2010-04-27
Its just as easy in Ubuntu. The difference is that configuration files are placed in a different folder from the installation files (executables). All your configuration folders are in your home folder, but you can't see them because they are hidden. Press **<ctrl> + h** to show hidden hidden folders. The folder you are looking for is **.gnupg/**

---

### Post by Bob Henson on 2010-04-29
Thanks. I now realise the significance of the dot in front of the directory name. I have edited my gpg.conf to my old settings. Little hiccoughs like this one aside, anything relating to cryptography is actually much easier in Linux than in the Windows versions of the same programs - but I'm still learning.
Regards,
Bob

---


---
title: "how do I upgrade to the new Firefox?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Arex Bawrin on 2009-07-14
(I'm on Jaunty) Sorry, I tried searching for this but got confused with the answers given. What is the best way to upgrade to the new firefox 3.5, and I have to warn you I am a total newb when it comes to getting around Ubuntu.

---

### Post by Revolutionary101 on 2009-07-14
Just type this into Terminal:

```
sudo apt-get install firefox-3.5
```

---

### Post by NilsE on 2009-07-14
> **Arex Bawrin said:**
> (I'm on Jaunty) Sorry, I tried searching for this but got confused with the answers given. What is the best way to upgrade to the new firefox 3.5, and I have to warn you I am a total newb when it comes to getting around Ubuntu.

Just install firefox-3.5 from Synaptic.  It is the official release just not totally branded yet.  It will say Shiretoko but that is OK.

Posted simultaneously so it is obvious you will get different answers.

---

### Post by Arex Bawrin on 2009-07-14
> **Revolutionary101 said:**
> Just type this into Terminal:

```
sudo apt-get install firefox-3.5
```

I did that but when I launch firefox it still says im on 3.0.11

---

### Post by Revolutionary101 on 2009-07-14
I guess you could just go to the Mozilla website then download the tar.bz2 file and extract it to a folder you want it in. Then just edit your application launchers to open the firefox file.

---

### Post by Arex Bawrin on 2009-07-14
> **Revolutionary101 said:**
> I guess you could just go to the Mozilla website then download the tar.bz2 file and extract it to a folder you want it in. Then just edit your application launchers to open the firefox file.

I finally got it thank you very much! I extracted the tar.bz2 file but I forgot to change the location of firefox in the app launcher. Thanks again.

---

### Post by Revolutionary101 on 2009-07-14
No problem I am glad you got it fixed.

---

### Post by Sef on 2009-07-14
Actually the best way is to use the [Ubuntu PPA for Firefox]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").   That way the updates keep coming through the Ubuntu updater.

---

### Post by lovinglinux on 2009-07-14
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by steveneddy on 2009-07-14
> **Sef said:**
> Actually the best way is to use the [Ubuntu PPA for Firefox]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").   That way the updates keep coming through the Ubuntu updater.

This is the way that i recommend also.

It's what all the cool kids are doing.

---


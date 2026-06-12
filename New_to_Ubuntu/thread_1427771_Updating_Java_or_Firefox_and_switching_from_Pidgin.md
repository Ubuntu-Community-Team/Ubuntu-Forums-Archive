---
title: "Updating Java or Firefox and switching from Pidgin to Digsby"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by KasRoth on 2010-03-11
Hello. I have a few questions about ubuntu when it comes to updates and the like. 

1) Currently "check for updates" is disabled on my firefox ( help-->check for updates ). I know that this is because I have something locked on the OS, and I can't figure out how to fix it. 

2) or some reason my university requires me to update Java to get onto their wireless network. I Downloaded the correct version, and gave it an archive, but I keep getting the following error:
 
chmod a+x jre-6u18-ubuntu-i586.bin
chmod: cannot access `jre-6u18-ubuntu-i586.bin': No such file or directory

3) Is it possible to remove Pidgin? It stopped working for me on my other laptop and I switched to Digsby and love it.  

I'm sure that there's a very simple command line I am missing, any help would be appreciated!

---

### Post by I8NY on 2010-03-12
For firefox the updates come through the ubuntu updater so the option to check for updates was disable.  For Java did u get it through the software center? You might have better luck with that.  You can remove pidgin in the package manager, but i didn't find it.  But I would just delete the shortcuts because it is hard to remove.  I like Digsby but i can't get it working in ubunut 64bit.  Hope this helps ;)

---

### Post by marshmallow1304 on 2010-03-12
1) As mentioned, Firefox is not installed manually, but through the package manager.  If you need the latest version, you can add this [PPA]("https://launchpad.net/~mozillateam/+archive/firefox-stable").

2) Where is the file?  Are you in the right directory?

3) ```
sudo apt-get remove pidgin
```

---

### Post by KasRoth on 2010-03-12
> **marshmallow1304 said:**
> 

2) Where is the file?  Are you in the right directory?




I know I'm not and that has to be the issue. right now I have the java .bin on my desktop. I'm not exactly sure what I'm missing. I haven't used Linux or anything like this before, so I'm probably missing a really common code that no one thinks to mention. 

Also, I'm trying to update this to use my blackberry as a modem and running into similar issues, leads me to think it's one common command that I'm ignorant on.

Everyone else, thanks a ton for all the help, you guys are fast and I appreciate it.

---

### Post by marshmallow1304 on 2010-03-12
You should move to your desktop with
```
cd ~/Desktop
```
then execute the command.

---

### Post by KasRoth on 2010-03-12
THANK YOU ALL!! I feel like an idiot for not figuring this out on my own. I think I was just ... overthinking this or something. THANKS

---


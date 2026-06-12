---
title: "java problems in ubunut 64bit"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by morgan365 on 2010-11-18
ok i love my ubuntu now that i have figured most of it out but today i tried to upload to photobucket and i needed a java plugin i downloaded it and it says that its working but when i go to photobucket it will not work it says i still need the pluggin what do i do thanks

---

### Post by TBABill on 2010-11-18
Which plugin do you have? The open source java plugin is semi-functional, but not nearly as good as Sun Java. I believe it's the iced tea plugin. Anyway, I normally just to go Synaptic, search for Sun or Java and install sun-java6-plugin or whatever it's called. I'm not on a Linux machine to confirm, but search Synaptic, mark for installation, click apply, restart your browser. If you already have the sun java plugin then there is something else at work most likely.

---

### Post by javanaut on 2010-11-25
The plugin, a shared library called **libnpjp2.so**, is part of the JRE, and is found in its lib/amd64 directory.

Download the 64-bit JRE for Linux from [www.java.com]("http://www.java.com"). You get a file jre-xxxx.bin, probably in ~/Downloads (xxxx is the version number, in my case 1.6.0_22).

Run the binary file:
```
user@compname:~/Downloads$ [B]chmod +x 
[/B]user@compname:~/Downloads$ **./jre-xxxx.bin**
```This creates a directory, say it's jrexxxx/ :
```
user@compname:~/Downloads$[B] ls
[COLOR=Blue]jrexxxx/[/COLOR]    jre-xxxx.bin[/B]
```Then copy your JRE directory to somewhere system-wide (I use /usr/lib):
```
user@compname:~/Downloads$ **sudo cp -R jrexxxx /usr/lib**
```Navigate to your browser directory (I use firefox):
```
user@compname:~/Downloads$ **cd /usr/lib/firefox-**<TAB> (to show possible completions)[B]
firefox-3.6.12/    firefox-addons/[/B]
user@compname:~/Downloads$ [B]cd /usr/lib/firefox-3.6.12
[/B]user@compname:/usr/lib/firefox-3.6.12$
```Navigate to your plugins directory and create a soft link:
```
user@compname:/usr/lib/firefox-3.6.12$ **cd plugins**
user@compname:/usr/lib/firefox-3.6.12/plugins$ **sudo ln -s /usr/lib/jrexxxx/lib/amd64/libnpjp2.so**
```Yes, the plugin is in the "**lib/amd64**" directory, **not** in the "**plugin**" directory of the JRE!![B] :o
[/B]
Now you're set. Restart your browser, and Java should work.

---


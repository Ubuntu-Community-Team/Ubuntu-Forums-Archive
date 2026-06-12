---
title: "best wifi controller?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by horse@pples on 2010-09-21
Is there a linux wifi controller that gives this sort of format/info?:

[http://wifihopper.com/screenshots.html](http://wifihopper.com/screenshots.html)

I've found wifihopper invaluable so it'd be great to find a Linux replacement/equivalent of some sort.

Thanks for any help!

---

### Post by beew on 2010-09-21
I am trying to look for something like that too. So far I found Xirrus linux version.

[http://linux.softpedia.com/get/System/Monitoring/Xirrus-Wi-Fi-Monitor-40214.shtml]("http://linux.softpedia.com/get/System/Monitoring/Xirrus-Wi-Fi-Monitor-40214.shtml")

Problem #1: I think it is no longer under development,--dead,-- as there is no mention of it anymore on Xirrus's website, you can't even find a download link there. The Windows and Mac versions are up to date but I think they quietly dropped the Linux version long time ago (it came out in 2008 based on web search)Just another example of software vendors not giving a sh&& to Linux users.

problem #2: You need gdesklet to run this but the current version of gdesklet is broken, it won't even start in Lucid. I don't think it is fixed in Maverick either. So you have to go back to an older version. See the comment by Kumm in the link
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/544840]("https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/544840")

I think SWScanner is supposed to get you those information, but I am not able to get it to work on my laptop. So I will be interested in hearing from someone who is able to get it working.

---

### Post by beew on 2010-09-21
Oh, I forgot,if you are using gnome and want to try Swscanner you have to first make a symbolic link in order to start SWscanner. In the terminal type (you only need to do it once)

```

sudo ln -s /usr/bin/gksudo /usr/bin/kdesudo
```

The reason is that running scanner requires root privilege and since Swscanner is a KDE app the command to invoke root privilege is kdesudo, which is not implemented in gnome.

I got Swscanner started, but it always complained that it could not read scanned data.

---

### Post by horse@pples on 2010-09-22
Well i'm gonna fool around with Wireshark and Prismstumbler and see if they do what they do. i'll give SimpleWirelesScanner a gogo too.

Thanks for the input.

---


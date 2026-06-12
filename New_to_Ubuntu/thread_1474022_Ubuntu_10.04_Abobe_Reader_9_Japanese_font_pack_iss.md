---
title: "Ubuntu 10.04 Abobe Reader 9 Japanese font pack issues"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by CivicSpoon on 2010-05-05
I'm trying to find a way to install the Japanese language pack for Adobe Reader 9.3.2.  I went as far as to upgrade from 9.3.1 to 9.3.2, because the file on Adobe's site said it was a multi language update... it wasn't.  So I've been trying to install the Japanese language pack for Acrobat 8.1, and use it with 9.3.2.  I'm not sure it's possible, but I haven't found any other language packs for the new version.  I followed this link for the most part:
[https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto](https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto)

This command didn't work:
```
sudo ./install
```

So I just double-clicked on the INSTALL file and selected "Run in Terminal", and it started to work.  The problem is that I got to the point where it asks you to choose where to install, and it wouldn't do anything.  Since it showed that it clearly wanted to install it in the /opt folder, I tried pressing Enter, and nothing happened.  I then tried typing "/opt" (minus quotes) and it still didn't do anything.  

So now I'm stuck.  Will it just not work at all because I'm using a newer version of the program?  Am I missing a certain way that I need to type in the location?  Is there an updated Japanese font pack for 9.3.2 available somewhere?  Any help is GREATLY appreciated!

---

### Post by CivicSpoon on 2010-05-07
Bump for some help.

---

### Post by BigBaka on 2010-05-10
I also have the same issue. Trying to find font pack for Japanese but cannot find. Japanese language documents simply come up blank.

---

### Post by CivicSpoon on 2010-05-11
Edit:  I got it to work!!!

I uninstalled the version I had.  Then I downloaded the version from here (the .deb package):
[ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.3.2/jpn/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.3.2/jpn/)

I installed that, and it all works now; Japanese text & English text.

---

### Post by BigBaka on 2010-05-11
Great you got this figured. A quick question though. Is the program itself now entirely in Japanese? Or program itself still in English, but able to view Japanese fonts. For my use, I would have to have the program itself in English language, just with the ability to view Japanese fonts.

I also have a thread going over at the Adobe community forums where they suggested that we could use the 9.1 fontpack, but it didn't quite go as planned.

[http://forums.adobe.com/message/2806031#2806031](http://forums.adobe.com/message/2806031#2806031)

Cheers
BB

---

### Post by BigBaka on 2010-05-12
Hmm, have now tried several different install files and font packs to get this Japanese script working, but no luck. Is it my file? I've attached a file here, see if you can get it working.

Regards,
BB

---

### Post by BigBaka on 2010-05-12
In an act of desperation I installed anything related to Japanese fonts for Adobe in synaptic, and suddenly I can now read the above attachment, but I still cannot read the handout attached to this post. Perhaps, it is just a font not recognised by Adobe reader. Is there a way to manually install fonts into reader?

Regards,
BB

---

### Post by antony_css on 2010-05-13
The asian language pack is included as **acroread-fonts** in the Medibuntu repository. Go and try that.

The following is the instruction for including Medibuntu in your computer:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by BigBaka on 2010-05-14
Removed Adobe, then reinstalled from the Ubuntu Software Center. Then installed the acroread font pack from Medibuntu as you suggested, but still can't get that handout 3 file to open properly. Trying now to install a bunch of other Japanese fonts packs, particularly Mincho and Gothic through the Ubuntu package manager, but I'm guessing that as they are not adobe reader related and therefore probably will not work.

Update - nope, didn't work. Installed all the Japanese fonts I could find, but still nothing. acroread font pack on Medibuntu didn't get me anywhere.

---

### Post by CivicSpoon on 2010-05-14
Sorry it took me a couple days to get back on here to respond.  The program in the link I posted is still in English, but it allows you to read Japanese text.  So it is what you want; if you can get it to work.

I am able to see the Japanese text from the .pdf file you posted, so it's not the file that is corrupt or anything.

Before you tried the .deb file in the link I posted (assuming you did), did you completely remove the previous version of Adobe Reader that you already had installed?  What I did was went through Synaptic Package Manager, and selected "Completely Remove" on the one I had installed.  If you did it another way, it might be worth a try (I'm a noob so I don't know any other way to do it).

---


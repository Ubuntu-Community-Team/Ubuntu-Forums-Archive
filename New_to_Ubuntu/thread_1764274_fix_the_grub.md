---
title: "fix the grub"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-05-21
i have hp dv6 3050tx laptop and i got genuine windows 7 64bit installed with it. Later i installed ubuntu on it and everything was working fine, few days back i installed backtrack also which is working absolutely fine bt now i cannot load ubuntu. 
Please tell me how to fix it...

---

### Post by Redblade20XX on 2011-05-21
So did you dual boot or installed over pre-existing os?

---

### Post by viditgoyal3009 on 2011-05-21
i installed them side by side... i had around 400gb on c: which later became arnd 200gb and the rest were used by ubuntu..

---

### Post by wojox on 2011-05-21
Which BT did you install?

---

### Post by sahabcse on 2011-05-21
Are you getting any error message when you loading the Ubuntu OS?

---

### Post by viditgoyal3009 on 2011-05-21
i didnt get the meaning of BT.

whenever i am trying to load ubuntu, the computer just keeps on showing a blank screen with a cursor blinking but nothing happens after that

---

### Post by oldfred on 2011-05-21
Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by wojox on 2011-05-21
> **viditgoyal3009 said:**
> i didnt get the meaning of BT.

whenever i am trying to load ubuntu, the computer just keeps on showing a blank screen with a cursor blinking but nothing happens after that

BT is short for BackTrack. Which version did you install?

---

### Post by viditgoyal3009 on 2011-05-22
BackTrack 4 R2

---

### Post by wojox on 2011-05-22
> **viditgoyal3009 said:**
> BackTrack 4 R2

I would reinstall [Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

BT-4 still uses grub legacy. Something may have gotten borked.

---

### Post by viditgoyal3009 on 2011-06-05
wen i go to the terminal and type grub, it shows me that no such application called grub is installed. What should i do??

---

### Post by wildmanne39 on 2011-06-05
> **viditgoyal3009 said:**
> wen i go to the terminal and type grub, it shows me that no such application called grub is installed. What should i do??
Hi. here is a guide for reinstalling grub.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---


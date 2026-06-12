---
title: "Newbie needs help."
date: 2010-12-28
forum: New to Ubuntu
---

### Post by AnimatroniK on 2010-12-28
Hello, 
this is my 1st message in the forum.
I downloaded ubuntu (Latest vers.) - AND DELETED win7- :)

I want a new start with this ''new'' -for me- OS.

I had some problems..

The biggest ( I think ) is : [B]Ubuntu Software Center fails [B]to update every single app.
I mean, I can't download anything from there.

[/B]I'll ask for help if I need anything else.
Sorry if the topic has been made again. But I were trying to search the forum,and couldn't find anything.

Thanks in advance,
Alex
[/B]

---

### Post by matt_symes on 2010-12-28
Hi

Welcome to the forums :)

You are definitely connected to the internet?

You could try changing the mirror.

System->Software sources->download from.

If that does not work....

Open a terminal and type 

```
sudo apt-get update
```

Enter your password (you will not see it as you type it) and post the results back here.

Kind regards

---

### Post by JRBye on 2010-12-28
So do you get any messages when you try to download something or can you even search? I have seen it state that the program isn't from a trusted source and things like that. If you can't search then it may be an Internet issue. Post whatever messages you get.

---

### Post by AnimatroniK on 2010-12-28
I did what you said. I found the Soft Sources. Nothing changed. Getting the same problem.

---

### Post by matt_symes on 2010-12-28
Hi

> I tried the next thing You told, typed 
sudo apt-get updateinto the terminal. After 43-45% it was failing to load the items.

We need to see the errors. Open a terminal and type the command again. After the command has finished, errors and all, select the text with the mouse. 

Press Shift + Ctrl + C to copy it from the terminal to the clipboard.

Press Ctrl + V to paste it into your next post. 

Hightlight the text in the post and press the # button in the menu bar. This will wrap the text in code tags and make it easier to read.

EDIT: Yes a typo. Its should have been System->Administration->Software Sources

EDIT2: Fixed typo in this post as well.

Kind regards

---

### Post by AnimatroniK on 2010-12-28
> **matt_symes said:**
> Hi



We need to see the errors. Open a terminal and type the command again. After the command has finished, errors and all, select the text with the mouse. 

Press Shift + Ctrl + C to copy it from the terminal to the clipboard.

Press Ctrl + C to paste it into your next post. 

Hightlight the text in the post and press the # button in the menu bar. This will wrap the text in code tags and make it easier to read.

EDIT: Yes a typo. Its should have been System->Administration->Software Sources

Kind regards

I've tried to copy it. Can't. The text goes off. It closes. :(

---

### Post by Bucky Ball on 2010-12-28
Control+***v*** to copy to forum post! ;)

---

### Post by runeh76 on 2010-12-28
(- AND DELETED win7-) :p

Great job!!  :guitar:

I think u can use ur mouse to copy/paste...

---

### Post by superchef on 2010-12-28
One thing to remember is whenever you copy text from the terminal, always use CONTROL + **SHIFT** + C (and to paste into the terminal use CONTROL + SHIFT + V). That's because CONTROL + [some letter] is used for different keyboard shortcuts in the terminal. For example, CONTROL + C kills (stops) the program that you were running the terminal.

---

### Post by matt_symes on 2010-12-28
Hi

> Control+v to copy to forum post! 


Two typos in one thread? I should go back to bed ;)

Kind regards

---

### Post by matt_symes on 2010-12-28
Hi

How are you opening a terminal?

Applications->Accessories->Terminal.

Then try again. The terminal should not close.

Kind regards

---

### Post by runeh76 on 2010-12-28
OMG !!!   Why u guys teach that kind of stuff if guy have just started and having problems?

Use ur mouse to copy/paste.

Cheers

---

### Post by AnimatroniK on 2010-12-28
Well,guys.. I know the shortcut commands. I've been using windows for more than 8 years.

And thanks for your replies.

BUT.. The problem is still there :)

Matt! If You go to sleep, You'll have nightmares! I'm gonna come in and do terrible things!
Spooky,ya?:)

I can't copy the text from the terminal. The reason is : It closes after finds those errors.

Another solution?

---

### Post by AnimatroniK on 2010-12-28
> **matt_symes said:**
> Hi

Welcome to the forums :)

You are definitely connected to the internet?

You could try changing the mirror.

System->Software sources->download from.

If that does not work....

Open a terminal and type 

```
sudo apt-get update
```Enter your password (you will not see it as you type it) and post the results back here.

Kind regards


Okay Matt,those are the results.

Can't attach the txt file. I gotta paste it here :(

:

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Bucky Ball on 2010-12-28
Doesn't look like you're online to me, but then, I guess you're posting here so you must be!

---

### Post by matt_symes on 2010-12-28
Hi

```
...
Err http://archive.ubuntu.com intrepid-proposed/multiverse Sources
404 Not Found [IP: 91.189.88.40 80]
...
```

Why are you using intrepid. That is an old version that is no longer supported.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29)

It you want to check your dist, open a terminal and type

```
cat /etc/lsb-release
```

This is mine.

```
matthew@matthew-laptop:/usr/bin$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
matthew@matthew-laptop:/usr/bin$ 
```


It looks like you have downloaded an old version. The new versions are here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

10.04 is an LTS and 10.10 is the newest.

Kind regards

---

### Post by AnimatroniK on 2010-12-28
> **matt_symes said:**
> Hi

```
...
Err http://archive.ubuntu.com intrepid-proposed/multiverse Sources
404 Not Found [IP: 91.189.88.40 80]
...
```Why are you using intrepid. That is an old version that is no longer supported.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29)

It you want to check your dist, open a terminal and type

```
cat /etc/lsb-release
```This is mine.

```
matthew@matthew-laptop:/usr/bin$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
matthew@matthew-laptop:/usr/bin$ 
```
It looks like you have downloaded an old version. The new versions are here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

10.04 is an LTS and 10.10 is the newest.

Kind regards

Oh,oh and OH!
Oh Matt,thank You. Well, the title sould say ULTRAnewbie needs help.
Thank You for Your help.
I'm gonna download the latest one and install. If any problem occurs I'll send You a PM ( If I can ? ) with the topic of mine.

One more time. Thank You very much,for Your time and help.
Peace

- Solved ( I think :D )

---

### Post by matt_symes on 2010-12-28
Hi

> I'm gonna download the latest one and install. If any problem occurs I'll send You a PM ( If I can ? ) with the topic of mine.

It's better if you can create a new thread if you have any issues so others can benefit from fixes.

But that being said you can PM me the link to the thread and, if i am online, i will look at it for you.

Kind regards.

---

### Post by Bucky Ball on 2010-12-28
Please mark thread as 'Solved'. See my signature below. Good luck.

---


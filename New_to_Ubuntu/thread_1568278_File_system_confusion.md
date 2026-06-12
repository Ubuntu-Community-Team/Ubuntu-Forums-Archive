---
title: "File system confusion"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-05
Ok, I am really hating myself for asking all of these stupid questions, but I'm simply having no luck with some of this stuff.  It seems the wikis out there for ubuntu just assume that everything will go as planned.  Not so much, unfortunately.  Ok, so here is my issue.

I installed Wine via the Software Center.  No problems there.  Next, I downloaded cabextract and mfc42.cab as per instructions.  When I tried to install cabextract I got the message that cabextract already existed and was current.  Spiffy.  Well, almost.  That fact rendered the instructions for installing mfc42.cab useless.  These are the instructions listed...

```
cd /tmp
cabextract mfc42.cab
wine /tmp/mfc42.exe
```

I've poked around and tried a few guesses but can't get everything where it needs to be to make this bloody thing work.  I know that mfc42.cab is sitting in my downloads.  Where do I put it so that I can use cabextract to extract it?  Do I still need to change directories in the terminal?

---

### Post by Legendary_Bibo on 2010-09-05
> **ubunwhat said:**
> Ok, I am really hating myself for asking all of these stupid questions, but I'm simply having no luck with some of this stuff.  It seems the wikis out there for ubuntu just assume that everything will go as planned.  Not so much, unfortunately.  Ok, so here is my issue.

I installed Wine via the Software Center.  No problems there.  Next, I downloaded cabextract and mfc42.cab as per instructions.  When I tried to install cabextract I got the message that cabextract already existed and was current.  Spiffy.  Well, almost.  That fact rendered the instructions for installing mfc42.cab useless.  These are the instructions listed...

```
cd /tmp
cabextract mfc42.cab
wine /tmp/mfc42.exe
```I've poked around and tried a few guesses but can't get everything where it needs to be to make this bloody thing work.  I know that mfc42.cab is sitting in my downloads.  Where do I put it so that I can use cabextract to extract it?  Do I still need to change directories in the terminal?

cab files need to become unshielded I believe before you can install. If you're trying to use wine though on a file you downloaded you could probably try cd'ing into your downloads folder unless you downloaded it via wget or curl or something. What are you trying to do exactly?

---

### Post by alphacrucis2 on 2010-09-05
> **ubunwhat said:**
> Ok, I am really hating myself for asking all of these stupid questions, but I'm simply having no luck with some of this stuff.  It seems the wikis out there for ubuntu just assume that everything will go as planned.  Not so much, unfortunately.  Ok, so here is my issue.

I installed Wine via the Software Center.  No problems there.  Next, I downloaded cabextract and mfc42.cab as per instructions.  When I tried to install cabextract I got the message that cabextract already existed and was current.  Spiffy.  Well, almost.  That fact rendered the instructions for installing mfc42.cab useless.  These are the instructions listed...

```
cd /tmp
cabextract mfc42.cab
wine /tmp/mfc42.exe
```



cd /tmp isn't going to be any use if mfc42.cab is sitting in Downloads.

Start up the terminal then

```
cd Downloads
cabextract mfc43.cab

```

If the .cab file is somewhere else, then cd into whatever directory it is located in. Or else move it where ever you like first and cd to the new location. Then you will be good to go with the cabextract.

---

### Post by jtarin on 2010-09-05
This was marked solved.

---


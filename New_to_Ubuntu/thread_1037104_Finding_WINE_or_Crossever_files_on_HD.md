---
title: "Finding WINE or Crossever files on HD"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by radi0j0hn on 2009-01-11
I am running Dreamweaver and my HTML pages and JPGs are saved in a folder that is associated with the program's Windows structure, not Ubuntu.  How can I find this folder so I can FTP the content to my site?  Not sure if Crossover or WINE is handling it, but I think it is Crossover.  TIA JOHN

---

### Post by CLomax on 2009-01-11
WINE: ~/.wine/drive_c/Program Files/
CX: ~/.cxoffice/default*/drive_c (or something similar)/Program Files

*Assuming the bottle being used is called 'Default'.
You need to press CTRL+H to show hidden folders when you're in your home folder.

Might be wrong though.

---

### Post by snova on 2009-01-11
> **CLomax said:**
> WINE: ~/.wine/drive_c/
CX: ~/.cxoffice/drive_c (or something similar)/

Might be wrong though.

Close, but Crossover adds an extra directory in between, the bottle name. For example:

```
~/.cxoffice/default/drive_c
```

---

### Post by CLomax on 2009-01-11
> **snova said:**
> Close, but Crossover adds an extra directory in between, the bottle name. For example:

```
~/.cxoffice/default/drive_c
```

Fixed :D

---

### Post by radi0j0hn on 2009-01-11
Thanks for your quick repies but I need to have you go back a few steps.  Where is the WINE folder?  I can get to my computer and the file system, but there are a million places to start looking, things called ETC, MNT and so on.

John

---

### Post by CLomax on 2009-01-11
> **radi0j0hn said:**
> Thanks for your quick repies but I need to have you go back a few steps.  Where is the WINE folder?  I can get to my computer and the file system, but there are a million places to start looking, things called ETC, MNT and so on.

John

The one you're looking for is called 'home'.

For future reference ~/ means 'home'. I should have mentioned that.

Oh, an when you're in /home/ press CTRL+H to show hidden directories. Files and folders begining with . mean they're hidden.

---

### Post by radi0j0hn on 2009-01-11
Hmmm. when I go to the HOME folder, it shows one folder with my name (JACK) and inside that is a lot of stuff I've saved.  But I do not see any files with the "." in front of them.

Please tell me there are not TWO home folders!   :)

---

### Post by radi0j0hn on 2009-01-11
Just read the part about Control H.....doah.

---

### Post by CLomax on 2009-01-11
> **radi0j0hn said:**
> Just read the part about Control H.....doah.

Yeah, I did a lot of editing on my posts because I'd find something incorrect every time I click the save button :D.

Glad you finally found them though.

---

### Post by radi0j0hn on 2009-01-11
Found my files and learned something new today! Thanks!

BTW, for what it's worth, I listed Ubuntu as my personal 2008 "product of the the year" on my site (acpress + com).

I do a bit of radio reviewing and writing on tech, but it's not likely that Ubuntu use will jump dramatically because of my article!   

John

---

### Post by CLomax on 2009-01-11
> **radi0j0hn said:**
> Found my files and learned something new today! Thanks!

BTW, for what it's worth, I listed Ubuntu as my personal 2008 "product of the the year" on my site (acpress + com).

I do a bit of radio reviewing and writing on tech, but it's not likely that Ubuntu use will jump dramatically because of my article!   

John

Awesome :guitar:

It's also good to hear you're doing your bit to spread free software. Many contributions, large and small, over the past 4 years have helped gather ~ 8 million users (Or I could be wrong again :D).

One small request, for the benefit of other users finding themselves with the same problem in the future, may you please mark the thread as 'Solved' in 'Thread tools' near the top of the page.

):P

---


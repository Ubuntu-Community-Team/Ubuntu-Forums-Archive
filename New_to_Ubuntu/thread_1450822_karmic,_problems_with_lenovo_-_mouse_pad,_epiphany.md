---
title: "karmic, problems with lenovo - mouse pad, epiphany and OOo"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by beanco on 2010-04-09
Hi Everybody,

Just did a clean install of Karmic on my Lenovo SL500 Thinkpad.

I was using Jaunty until now...

SO, I cannot get the mouse touch pad turned off.

I use a couple of site I have to log into often and long in up to 40 times/site a day. I use EPiphany and cnanot get the remember password option in Edit/Preferences/Privacy to work....

I also need to open a few MS Word files, I think they are Word 7 or whateve rthe newest version is and I cannot open them in OOo.

I did not have eithe rof these problems in Jaunty.

Thanks for the help.

---

### Post by uRock on 2010-04-09
I would try reinstalling Epiphany and OpenOffice.org. I have used both and never had a problem with passwords nor opening .docx files.

Cheer,
Ronnie

---

### Post by beanco on 2010-04-09
Ok, but then I should remove/purge them first, right?

I have been mucking round with open office but cannot get it ...

so, please giv eme the code for cli to purge then install OOo


I thought it was sudo apt-get purge openoffice but there is sg wrong with this....

Robi

---

### Post by beanco on 2010-04-09
I managed to reinstall OOo and now I can open .docx files.

The Epiphany password thingy is not working.... I iwll keep trying!

Robi

---

### Post by uRock on 2010-04-09
[s]I would use ```
sudo apt-get remove openoffice.org
``` ```
sudo apt-get autoclean
``` ```
sudo apt-get install openoffice.org
```[/s]

I haven't played with Epiphany in a while, so I am not sure how to troubleshoot it.

Cheers,
Ronnie

---

### Post by beanco on 2010-04-11
Ronni,

Thanks, those are the ones that got  OOo working. Still having issues with the Epiphany password thingy. Kind of sucks, because I really do not like alwyas having to log in....


Robi

---


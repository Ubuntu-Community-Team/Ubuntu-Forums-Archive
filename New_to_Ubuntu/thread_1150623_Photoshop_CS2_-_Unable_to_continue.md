---
title: "Photoshop CS2 - Unable to continue"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by aas452 on 2009-05-06
I recently had to recover my system due to a video card issue,

I had PhotoShop working under Wine but I am encountering the same error I dealt with the first time I installed it. I know it has to do with an un-installed font but cant seem to find the document I found the solution from.

At the start up of Photoshop, this is the error

```

Unable to continue because of a hardware or system error. Sorry, but this error is unrecoverable

```

Anyone run into the URL or have a solution

---

### Post by aas452 on 2009-05-06
Before installing Photoshop, install the Times32 font by downloading and running one of the corefont installers, e.g. [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe]("http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe") , else Photoshop will abort with a "hardware error" [see bug 9623]


Found it, 

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=2631]("http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=2631")

---


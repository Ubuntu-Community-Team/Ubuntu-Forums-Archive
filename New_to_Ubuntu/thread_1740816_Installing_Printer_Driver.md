---
title: "Installing Printer Driver"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by sheldonhuelin on 2011-04-27
Hi Everyone;
I am a new Ubuntu user (<2 weeks), so far I am loving it and haven't used windows since the switch. I am wanting to add a Xerox Workcentre 5030 network printer, but I cannot find the driver through the Ubuntu Driver setup. I found this download page, but I am unsure of what to download and what to do with it. Thanks

[http://www.support.xerox.com/support/workcentre-5030-5050/downloads/enus.html?operatingSystem=linux&fileLanguage=en]("http://www.support.xerox.com/support/workcentre-5030-5050/downloads/enus.html?operatingSystem=linux&fileLanguage=en")

Also, I did try searching for a solution to this problem but I could not find any answers. 

Sheldon

---

### Post by wolfen69 on 2011-04-27
Download the .tgz file from [here]("http://www.support.xerox.com/support/workcentre-5030-5050/file-download/enus.html?operatingSystem=linux&fileLanguage=en&contentId=74741&from=downloads&viewArchived=false"). Put it in your home folder. Right click and *extract here*. Then in a terminal, do:
```
sudo ~/XeroxLinuxi386XpxxInstall/setup
```
and follow the prompts.

---

### Post by sheldonhuelin on 2011-04-27
Hi;
I followed the instructions, selected Y for accepting terms to the license agreement (from terminal), and that was it. I went into Printing under the System menu, and only my desktop printer was there. Thanks for the help. 
Sheldon

---

### Post by wolfen69 on 2011-04-27
Go to Printing and then Server>New>Printer>Network Printer>Find Network Printer.

---

### Post by sheldonhuelin on 2011-04-27
It has found the printer but not the driver. Not sure of what to do next.

---


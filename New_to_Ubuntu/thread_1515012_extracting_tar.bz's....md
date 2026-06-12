---
title: "extracting tar.bz's...?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by gabriella on 2010-06-21
OK I'm still confused about these. There's an application I've downloaded. I downloaded the tarball tar.bz. So now it's sitting in my /tmp folder. I can click and extract it but what I don't understand how to specify where it will go, where its extracted to? Or does it automatically go the the right place?

Thank you for answering what is probably a silly question I should already know

---

### Post by wesleybishop on 2010-06-21
> **gabriella said:**
> OK I'm still confused about these. There's an application I've downloaded. I downloaded the tarball tar.bz. So now it's sitting in my /tmp folder. I can click and extract it but what I don't understand how to specify where it will go, where its extracted to? Or does it automatically go the the right place?

Thank you for answering what is probably a silly question I should already know



[LIST]
[*]To extract:
[*]In terminal type the code below
[/LIST]
           tar xvjf package.tar.bz

---

### Post by wesleybishop on 2010-06-21
also check out [http://ubuntuforums.org/showthread.php?t=407556](http://ubuntuforums.org/showthread.php?t=407556)

---

### Post by gabriella on 2010-06-21
> **wesleybishop said:**
> [LIST]
[*]To extract:
[*]In terminal type the code below
[/LIST]
           tar xvjf package.tar.bz

OK thanks...
I can also extract by right clicking on the downloaded folder. However, I concerned about where it will extract to. Right click gives me "extract here" and Archive manager has an extract too. But do I need to specify where or is that already determined by the file?

---

### Post by warfacegod on 2010-06-21
If you extract without telling it to go somewhere, it will default to the folder that the tarball is currently in.

---

### Post by gabriella on 2010-06-21
> **warfacegod said:**
> If you extract without telling it to go somewhere, it will default to the folder that the tarball is currently in.

OK, well I think I'll use the command line it seems more straightforward!

---

### Post by warfacegod on 2010-06-21
> So now it's sitting in my /tmp folder.

You shouldn't be sending downloads there. That folder is meant for streaming or extra disk space for burning CD's or any number of temporary OS uses. You should generally use folders in the /home for downloading or extracting or data storage.

---

### Post by gabriella on 2010-06-21
> **warfacegod said:**
> You shouldn't be sending downloads there. That folder is meant for streaming or extra disk space for burning CD's or any number of temporary OS uses. You should generally use folders in the /home for downloading or extracting or data storage.
 
Thats where it ended up for some reason. But now its vanished anyway!..

---

### Post by warfacegod on 2010-06-21
> **gabriella said:**
> Thats where it ended up for some reason. But now its vanished anyway!..

That's because it's a temporary folder.

---


---
title: "How to install firefox upgrade on lucid"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by tinkles on 2011-07-18
I just downloaded firefox 5.01 to archive.  I then extracted it to the firefox folder.  What do I do next to install it?

---

### Post by Bleak888 on 2011-07-18
You should be able to download and install it easily via PPA.

Add the mozilla PPA

*sudo add-apt-repository ppa:mozillateam/firefox-stable*

Next, type the command below to update your system.

*sudo apt-get update*

Finally, type the command below to upgrade your system along with Firefox

*apt-get upgrade*

---

### Post by wojox on 2011-07-18
[Firefox 5 & Beyond Mega Thread ]("http://ubuntuforums.org/showthread.php?t=1712247&highlight=Firefox+4%2C+Mega+Thread")

---

### Post by gandaran on 2011-07-18
> **tinkles said:**
> I just downloaded firefox 5.01 to archive.  I then extracted it to the firefox folder.  What do I do next to install it?
you just extract the firefox package and put it anywhere you like to run it click the firefox file or create a launcher pointing to the path of the firefox file.
if you want firefox installed properly in the root file system then use the firefox PPA repository don't use what you have downloaded.

---

### Post by tinkles on 2011-07-18
Thank you very much.  It worked.   I had to put sudo in front of the get upgrade command.

---


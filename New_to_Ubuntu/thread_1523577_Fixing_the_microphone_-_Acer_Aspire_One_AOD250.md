---
title: "Fixing the microphone - Acer Aspire One AOD250"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by drusalan on 2010-07-03
I'm trying to fix the microphone on my new Ubuntu 9.04 install.
I am using the guide found here.

[https://help.ubuntu.com/community/AspireOneAOD250](https://help.ubuntu.com/community/AspireOneAOD250)

I'm at this stage :

----
sudo m-a update

More  preparations. 

sudo m-a prepare.

Still more  preparations.
----

However when I type sudo m-a update I get an error saying "sudo: m: command not found"

I'm cutting and pasting into terminal directly from the webpage so I'm not mistyping it. What is the problem here? Any help plz?

Drusalan

---

### Post by cljokla on 2011-01-05
You need to install module-assistant to get the command.

sudo apt-get install module-assistant

---


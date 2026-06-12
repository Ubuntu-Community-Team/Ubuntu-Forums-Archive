---
title: "software center problem"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by swwb on 2010-04-12
Hello everyone, I've only been using ubuntu for about 24 hours so sorry if this is a silly question. I just installed ubuntu on an acer aspire netbook and everything worked fine. I was online with wifi in about 30 minutes with no configuration.   After exploring the OS though I noticed in the Ubuntu Software Center that no matter which application I select it says "not available in the current data" and there is no apparent way to install the software.   I've managed to install stuff like TrueCrypt that I downloaded from their website, and I've been able to uninstall software via the software center. Downloading from the software center is the only impossibility.   Thanks in advance to everyone.

---

### Post by elliotn on 2010-04-12
u need  to open snaptic package manager and enable repos, then reload. Then go back to software centre.

---

### Post by fromthehill on 2010-04-12
start the terminal
run this command:
```
sudo apt-get update
```

according to a quick google search that should do it

---

### Post by codemaniac on 2010-04-12
just follow these steps...press alt+F2..a box will pop up..on the run application box type "terminal" and press enter..a terminal will be up in front of you...key these in..
$sudo apt-get update

This will download all the package informations[not packages] to your local machine ..Now you are allowed to install whatever you want..

---

### Post by swwb on 2010-04-12
> **elliotn said:**
> u need  to open snaptic package manager and enable repos, then reload. Then go back to software centre.

 Awesome, this worked!  Thanks a lot!

---


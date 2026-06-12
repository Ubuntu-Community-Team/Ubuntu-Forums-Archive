---
title: "HELP: Firefox not recognizing Flash."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Grimhound on 2008-12-17
I'm having an issue where Mozilla Firefox refuses to identify Flash(flashplugin-nonfree from the reposity) and use it in the browser. I am completely stumped. Just installed 8.10 fresh for the first time, and this issue has never happened to me before on this hardware when using previous versions of Ubuntu. It just continually says that a Plugin is needed, and even when Flash is selected it just goes back the same in not recognizing it. Please help me.

edit: It also doesn't seem to recognize the Mplayer plugin. WTF is wrong with Firefox?

---

### Post by llamakc on 2008-12-17
Have you restarted Firefox? Do you have another instance of it running in a different workspace?

---

### Post by Grimhound on 2008-12-17
There is no other instance. There are no other windows. Other desktops are disabled. It's a fresh installation of Ubuntu. I'm now tempted to just go over to Fedora, as it sort of seems like Ubuntu just keeps futzing itself up with every version.

---

### Post by Grimhound on 2008-12-17
Fully reinstalling Firefox and rebooting worked.

---

### Post by llamakc on 2008-12-17
Please mark this as [solved]. Good news!

---

### Post by Grimhound on 2008-12-18
> **llamakc said:**
> Please mark this as [solved]. Good news!

Sadly not. Just reinstalled Ubuntu. Now not even that will work. The devs really screwed Firefox up. It can't figure out Flash, and I have no idea how to force it. THIS is why Linux will never be ready for the mainstream.

---

### Post by madverb on 2008-12-18
It won't be ready because occasionally Flash doesn't work? Cool.

Anyway... there are many different fixes around. Like getting an older version of Flash and installing it manually. Do a search on the forum. You should find something helpful.

---

### Post by Grimhound on 2008-12-18
> **madverb said:**
> It won't be ready because occasionally Flash doesn't work? Cool.

Anyway... there are many different fixes around. Like getting an older version of Flash and installing it manually. Do a search on the forum. You should find something helpful.

As someone who has already tested Windows 7, which worked pretty much flawlessly for me, I have to say yeah. Flash is an essential thing these days. If an operating system has issues with it, people won't use the operating system. An OS has to run seamlessly enough where your average computer-illiterate serf can understand it.

Also: The issue appears to be that the version of flashplugin-nonfree in the reposities is bugged. Turns out what had worked the first time was me going and downloading the .deb package from Adobe's website. That one runs fine.

---

### Post by madverb on 2008-12-18
> **flaw·less (flô'l&#301;s)**
adj. Being entirely without flaw or imperfection.
flaw'less·ly adv., flaw'less·ness n.

Sure

---

### Post by Zip247 on 2008-12-18
I do not see flash as being essential at all.  I run noscript on firefox and have only had to allow about 5 pages to run their scripts, most of them being java scripts and not flash.  Just my 2 cents.

---

### Post by kristopher.ives on 2009-01-01
I have problems where flash loads some content but not others. I later figured it out and wrote: [Flash Stops Working in FireFox]("http://santiance.com/kris/?p=30"). It was mostly related to the changes in Flash Player 10 that just came out though.

---


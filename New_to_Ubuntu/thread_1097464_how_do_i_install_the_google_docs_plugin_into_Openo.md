---
title: "how do i install the google docs plugin into Openoffice?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-03-16
you know, when i type some things onto Openoffice. and i want it to synthesis into google docs.

how do i install that?

---

### Post by Zeedok on 2009-03-16
Go to the open office extensions page and find the "docs2google" - I think that's what it is called - extension. Download it and save it somewhere. Open openoffice and find the extension manager (under Tools). It's pretty easy from there, good luck.

---

### Post by shiningkenmonster on 2009-03-16
still lost. not sure whats the official google docs extension to download

---

### Post by LukeyMI on 2009-05-29
Hate to bump this, but I'm having trouble getting the google docs plugin installed in Openoffice. Attached is the error I am getting. I am using release 1.6.0 from here: [http://extensions.services.openoffice.org/project/ooo2gd](http://extensions.services.openoffice.org/project/ooo2gd)

Has anybody else had this issue, and if so did you resolve it and how?

I'm using the x64 release of Ubuntu with all the latest updates if it matters any.

And to answer shiningkenmonster's question, I've used this plugin on my Windows box and it works great. It adds a toolbar where you can import and export form google docs. It's been working pretty well for me (on the Windows box anyways) but I've only been using it for a couple days. Hopefully I can get it fixed up for my Ubuntu laptop though.

---

### Post by jmszr on 2009-05-30
LukeyMI,

You will need to go to Applications > Accessories > Terminal and type (or copy and paste)```
sudo apt-get install openoffice.org-java-common
``` 
Once that's installed you should then be able to install the google docs extension through the OpenOffice extension manager.

---

### Post by LukeyMI on 2009-05-30
Thanks, works great now. :)

---


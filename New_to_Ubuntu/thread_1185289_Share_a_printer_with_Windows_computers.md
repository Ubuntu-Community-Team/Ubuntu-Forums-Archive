---
title: "Share a printer with Windows computers"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-06-12
Dear All,
I have got a HP LaserJet printer connected to an Ubuntu jaunty machine which has Server->Settings->Publish shared printers connected to this system, ON. This printer has also the shared check box enabled. 

I want to share this printer in a networked environment where there are a bunch of (forty) Ubuntu and Windows XP computers. I can add the printer to the Linux machines using Cups without any problem. However I am not so lucky with the Windows machines. 

Whenever I try to add the printer using the URL  http://<hostname>:631/printers/<printername>, I get an error message in the line of not being able to connect to server. Using the printer wizard results in similar messages.

What is it I am missing here and how I can debug the problem?

Thanks in advance.

---

### Post by superprash2003 on 2009-06-12
what error do you get when trying to add?? drivers issue?? when trying to connect , dont search for printer , enter its direct link , like x.x.x.x/printername

---

### Post by Prince Valiant on 2009-06-12
Have you seen[ this]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") install guide?  Also, you could try setting a static IP address for your server...I had the same problem, and this fixed it.

-Val

---

### Post by stinger30au on 2009-06-12
dont foget to install samba

you need this for windows shares

---


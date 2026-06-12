---
title: "Windows Wireless Driver not working"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by tippyknit on 2008-06-25
I'm contemplating fully installing xubuntu (as it is fast, other ways Ubuntu) on an old system. I've been using hardy since its release in Wubi. However, my wireless card driver was only supported in Windows. I installed the windows 'translator' for windows drivers, but still no networks showed up in my network manager window. Basically, the computer can use the driver, but doesn't support wireless networking.

Is there anyway to install wireless support? Or what should I do?

---

### Post by cwbar_1 on 2008-06-25
Do you know the type of wireless card?
or
Post the results of lspci.

---

### Post by tippyknit on 2008-06-25
NETGEAR WG121 (54 Mbps Wireless USB 2.0 Adapter).

---

### Post by cwbar_1 on 2008-06-25
Try this how to.  Great directions!  [https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=(WG121)|(NETGEAR](https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=(WG121)|(NETGEAR))

---

### Post by tippyknit on 2008-06-25
the instructions worked until my terminal told me that I should have a different version. Tried installation, version failed. and... oops I closed the terminal window.

---

### Post by cwbar_1 on 2008-06-26
Sorry to leave you hanging so long.  On vacation/kept Grandson today.....  1. What version of Xubuntu are you working with? 2. Which step of the how to did you get the message?

---

### Post by tippyknit on 2008-06-28
Hope you had a fun time.

I'm running Hardy. Step 3, after it downloads, when installing it gives me the message '1.5.1 is not the current version. Try 1.9.2'. I tried replacing the 1.5.1 (plural) with 1.9.2, and got the message that 1.9.2 doesn't exist.

---

### Post by cwbar_1 on 2008-06-28
[http://kent.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz](http://kent.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz)

This one.

---

### Post by tippyknit on 2008-08-15
Sorry. I've been gone at music school.

Anyway, here's the brief summary (as I see it):

1. WUBI now has a program (ndisrapper) that has installed my wireless card reader and detects the wireless router
2. The system doesn't have an access port for the router
3. So, basically, I have achieved the state of being at which I can feel confident and happy that my router is indeed plugged in and receiving power from the computer, but I am still well protected from internet scams, because the system (not ndisrapper) has no clue how to use the new hardware plugged into it.

What should I do now?

---


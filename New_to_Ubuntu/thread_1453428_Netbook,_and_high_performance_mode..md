---
title: "Netbook, and high performance mode."
date: 2010-04-13
forum: New to Ubuntu
---

### Post by ni_ko on 2010-04-13
Im dual booting win7 and ubuntu 9.10 on my Asus 1005hab. On windows 7 by default i can click on the battery and put the laptop on either power save, balanced, or high performance mode depending on what I'm doing (not to mention im also running super hybrid engine). I was wondering if I can access these types of modes in ubuntu.

---

### Post by manoriax on 2010-04-13
Are you running the Netbook Edition?

---

### Post by ni_ko on 2010-04-13
No, I dont like the layout.

---

### Post by philodice on 2010-04-13
Netbook remix works best on the smaller machines.  The layout is customizable.

---

### Post by 416inversed on 2010-04-13
I'm also a fan of customizing remix. By disabling netbook-launcher & tweaking the panel, it acts like Ubuntu desktop, but more geared toward netbooks.

That said, to attempt to answer your question, there's a power management program called Jupiter  [http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/) that no longer officially supports Ubuntu, but offers the ability automatically (& manually) to change power modes. OMG Ubuntu had an article on it: [http://www.omgubuntu.co.uk/2010/02/jupiter-awesome-new-netbook.html](http://www.omgubuntu.co.uk/2010/02/jupiter-awesome-new-netbook.html)

The program I currently use is powertop. In terminal (install)```
sudo apt-get install powertop
```then to run
```
sudo powertop
```It's a smaller, neater package, that runs in terminal that gives me more control over what I turn on & off in powersaving. It works well with the CPU Freq scaling panel applet that lets you manually shift processor speeds. (right click panel> add to panel> CPU Frequency scaling monitor)

---

### Post by ni_ko on 2010-04-13
how can i safely overclock with powertop

---

### Post by nerdy_kid on 2010-04-13
KDE has an awesome power manager with profile support.

---

### Post by uRock on 2010-04-13
Netbook Edition doesn't change performance. Check out the eee-applet in Ubuntu Software Center.

---


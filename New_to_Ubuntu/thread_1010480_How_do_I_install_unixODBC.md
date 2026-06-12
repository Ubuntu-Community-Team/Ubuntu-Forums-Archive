---
title: "How do I install unixODBC?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by exXPusr on 2008-12-13
I am a semi-newbie with Linux. I am migrating my workstation from XP to Ubuntu Linux. All has migrated well but I ran unto a requirement to load unixODBC to support a application running under WINE.

I cannot find any noob instructions on how to install unixODBC. is there a simple way to install this?

---

### Post by Michael.Godawski on 2008-12-14
The unixODBC is installed by default in intrepid. Perhaps you need the dev and bin files, too?

```
sudo apt-get install unixodbc-dev unixodbc-bin unixodbc
```

---

### Post by exXPusr on 2008-12-14
Thank You. That did the trick!. I am running CircuitMaker2000 pro (Spice SiM) under WINE and it was the final app that I needed to to complete full conversion to Linux. It runs faster under Linux than it did under XP. Now I can Thumb my nose to M$:biggrin:

---

### Post by sallychoon on 2010-05-24
Hi, I'm new in using ubuntu. I tried to manually install unixODBC. But it is fail to install it.
Anyone can help me in solving this problem?

I download the package from [http://www.unixodbc.org/download.html,it](http://www.unixodbc.org/download.html,it) is tar.gz.
Then i unzip it.I tried to configure the file by typing 
./congure
But the terminal read it as directory and i failed to install the it.
Anyone can please help me to solve the problem?
Thanks

---


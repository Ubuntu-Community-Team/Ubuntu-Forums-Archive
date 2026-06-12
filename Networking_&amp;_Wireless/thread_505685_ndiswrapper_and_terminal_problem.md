---
title: "ndiswrapper and terminal problem"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by kbuika on 2007-07-20
Hi, 
I am new to linux and can't find my problem on any of the forums. I have the file:

ndiswrapper-1.47.tar.gz     sitting on my desktop

when i type:   tar xvfz ndiswrapper-1.47.tar.gz to extract the file all it says is "Cannot open: No such file or directory"

I have tried several variations of xvfz including a (-). It never recognizes the file. 

Side note: I just installed fiesty. Navigating through the terminal seems very limited, i.e. i can't find any files with the cd command.

Any thought would be greatly appreciated.

---

### Post by kevdog on 2007-07-20
try this:

```
cd ~/Desktop
tar -zxvf ndiswrapper-1.47.tar.gz
```

That should do it

---


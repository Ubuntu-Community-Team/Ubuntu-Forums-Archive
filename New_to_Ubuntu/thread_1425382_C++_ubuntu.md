---
title: "C++ ubuntu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by lara45 on 2010-03-09
Plz HELP . I'm new with ubuntu and i have to work on C++ within it. I've installed netbeans with the C++ plugin but cannot compile any file. The command cc cannot be recognized in commandline and in netbeans they tell me that the C++ compiler is missing. Any body has any idea ???????????????? Plz HELP

---

### Post by perham on 2010-03-09
> **lara45 said:**
> Plz HELP . I'm new with ubuntu and i have to work on C++ within it. I've installed netbeans with the C++ plugin but cannot compile any file. The command cc cannot be recognized in commandline and in netbeans they tell me that the C++ compiler is missing. Any body has any idea ???????????????? Plz HELP

the command for the compiler is "gcc" for C and "g++" for C++ . if you don't have them, run "sudo apt-get install gcc g++" . a good IDE to use is anjuta, and Kdevelop is very good too. both of them can be found in synaptic. I hope I could help.

---

### Post by GregBrannon on 2010-03-09
Or to be sure that you get everything you need to compile and run programs, use:

```
sudo apt-get install build-essential
```

---

### Post by GregBrannon on 2010-03-09
Here's a good thread describing someone else's struggle to do the same thing, and it has a happy ending:

[http://ubuntuforums.org/showthread.php?t=1420979]("http://ubuntuforums.org/showthread.php?t=1420979")

---

### Post by [Shadow] on 2010-03-09
If you prefer to use an IDE theyre are some good ones out there like

Code::Blocks  

or

Anjuta


If you prefer command line then g++ is your best bet IMO

---


---
title: "Wine crash!"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by pallemusen on 2011-02-16
Hi everyone! 

I'm not that used to ubuntu, but i still fell in love with it some months ago. Afterwards, i have been installing it everywhere!
The thing is, that i'm able to run most games through wine, both on my desktop and on my laptop - until now. Now my laptop won't start ANYTHING! 

Whenever i run a program (both games and others) it is displayed as if it was about to run. So far so good - but then it stops. In the active programs bar (the grey bar in the bottom by default) it's shown, but closes - no error message, no nothing. 

I am getting desperate, and i have tried a lot of things! I have uninstalled wine, deleted it completely (i thought, i wouldn't go away from the main menu) and updated it. If no response is given from this thread, i will have to reinstall ubuntu. I therefore beg you all to help.

Sincerely, a desperate linux fan.

---

### Post by Old *ix Geek on 2011-02-16
> **pallemusen said:**
> If no response is given from this thread, i will have to reinstall ubuntu.I can't help you with your actual problem, but I just wanted to say: This isn't windoze. Reinstalling the OS to solve problems of this nature is [usually] not necessary. It's not like windoze where every few months the system gets so screwed up with viruses and bloatware and malware that it requires a reinstall to fix, or where a little problem like the one you're having requires a reinstall to fix. I hope you'll get out of the Micro$oft mindset because THIS operating system doesn't work that ridiculous way! :)

---

### Post by sandyd on 2011-02-16
> **pallemusen said:**
> Hi everyone! 

I'm not that used to ubuntu, but i still fell in love with it some months ago. Afterwards, i have been installing it everywhere!
The thing is, that i'm able to run most games through wine, both on my desktop and on my laptop - until now. Now my laptop won't start ANYTHING! 

Whenever i run a program (both games and others) it is displayed as if it was about to run. So far so good - but then it stops. In the active programs bar (the grey bar in the bottom by default) it's shown, but closes - no error message, no nothing. 

I am getting desperate, and i have tried a lot of things! I have uninstalled wine, deleted it completely (i thought, i wouldn't go away from the main menu) and updated it. If no response is given from this thread, i will have to reinstall ubuntu. I therefore beg you all to help.

Sincerely, a desperate linux fan.
what happens when you manually run the program from the terminal?
i.e.
```

wine /path/to/application
```

The wine "C" drive is located at
~/.wine
so to run programs manually...

```

cd ~/.wine/drive_c/"Program Files"
ls

```
and take a look at whats there.

to run one of the programs, 
```
cd [B]directoryname

[/B]wine name_of_program.exe
```

---

### Post by pallemusen on 2011-02-17
Hi there! 

I cd'ed via the terminal to a folder with a random game. 
Afterwards, when i was in the gamefolder, i wrote "ls", and it said etc. "Magicka". Then i wrote "wine Magicka", "wine Magicka.exe", "wine "Magicka"" and "wine "Magicka.exe"", but with no luck at all. 
My terminal replied: 
"wine: cannot find L"C:\\windows\\system32\\magicka.exe"

I don't quite know what i am doing wrong O: Please help me. Could it be because of a lack of some i.e. .NET Framework 3.5 or DirectX9??

Thank you in advance.

---


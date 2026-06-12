---
title: "Antivirus program blocking WoW Patch?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by jalehtor on 2009-06-01
I have been having this problem for two weeks now. I can't upload patch 3.1.2 for World of Warcraft as the patch stops loading at 70%. 

The official WoW technical info has two possible solutions to this:

1. "This issue seems to appear if an antivirus program, like Kaspersky, is blocking the patch from starting up. Try temporarily disabling it for the patch process."

Is there an antivirus program that I can temporarily disable for the patch to finish downloading? I just have the stuff I downloaded in the first place with the disk; I haven't added any extra antivirus programs.

2. "If this does not work, you can try to download the patch you need from the mirror links on the bottom post, then try installing it in Safe Mode"

Is there a "safe mode" for Ubuntu? I tried to download the mirror links as they were, and they appear as icons on the desktop, but when you click on them, nothing happens with the patch.

---

### Post by Volt9000 on 2009-06-01
World of Warcraft is a Windows game, hence it runs under WINE.
The patch will also have to be executed under WINE. Maybe it's having problems.

Try running the patch from a command-line

```

wine wow-patch.exe

```

to see what happens.

Oh and the "Safe Mode" they're talking about is for Windows-- it doesn't apply to Linux.

---

### Post by jalehtor on 2009-06-01
> **Volt9000 said:**
> World of Warcraft is a Windows game, hence it runs under WINE.
The patch will also have to be executed under WINE. Maybe it's having problems.

Try running the patch from a command-line

```

wine wow-patch.exe

```

to see what happens.

Oh and the "Safe Mode" they're talking about is for Windows-- it doesn't apply to Linux.

Thank you! I tried running the patch from a command line, and got this:

wine: could not load L"C:\\windows\\system32\\wow-patch.exe": Module not found

What does that mean?

---

### Post by nandemonai on 2009-06-02
> **jalehtor said:**
> Thank you! I tried running the patch from a command line, and got this:

wine: could not load L"C:\\windows\\system32\\wow-patch.exe": Module not found

What does that mean?

Might want to ask in the gaming forum here. I know of a few people who play WoW under Ubuntu, surely someone has figured it out. Can't be going without the Warcrack for too long. :P

---

### Post by jalehtor on 2009-06-02
> **nandemonai said:**
> Might want to ask in the gaming forum here. I know of a few people who play WoW under Ubuntu, surely someone has figured it out. Can't be going without the Warcrack for too long. :P

Great idea, thank you. My family and I are in withdrawal.

---

### Post by Volt9000 on 2009-06-02
> **nandemonai said:**
> Might want to ask in the gaming forum here. I know of a few people who play WoW under Ubuntu, surely someone has figured it out. Can't be going without the Warcrack for too long. :P

Well for starters, you should specify the ACTUAL .exe file name and not the example filename I gave. Make sure to also specify the full path to the .exe file, i.e. wherever you downloaded it to.

---

### Post by Astarroth on 2009-06-02
No sure of the specifics but, copy the patch you download from the mirror site to the WoW folder under wine. Once it is there start wine and tell it to execute the file. It should run fine from there as long as it is not corrupted. ;)

---

### Post by jalehtor on 2009-06-03
> **Astarroth said:**
> No sure of the specifics but, copy the patch you download from the mirror site to the WoW folder under wine. Once it is there start wine and tell it to execute the file. It should run fine from there as long as it is not corrupted. ;)

I tried to open with Wine Windows Program Folder; nothing happens. Is that what you meant? 

I have to apologize profoundly: I don't know what I am doing! All I know is that by some miracle I managed to install WoW and every other patch. This one's beyond me, and what's really frustrating is that I'm absolutely certain that anyone who knows anything about this would be able to do it in two mins flat. 

:(

---

### Post by jalehtor on 2009-06-03
> **Volt9000 said:**
> Well for starters, you should specify the ACTUAL .exe file name and not the example filename I gave. Make sure to also specify the full path to the .exe file, i.e. wherever you downloaded it to.

Hi! As you can tell, I don't know what I'm doing. The file name on the desktop is /home/jaleh/Desktop/WoW-3.1.1.9835-to-3.1.2.9901-enUS-patch.exe

I've tried three mirrors. The same with all three: The computer saves it, but won't download it to Wine/WoW.

Can you assume that I am an idiot and be more specific? I am so very, very sorry.

---

### Post by nandemonai on 2009-06-03
> **jalehtor said:**
> I tried to open with Wine Windows Program Folder; nothing happens. Is that what you meant? 

I have to apologize profoundly: I don't know what I am doing! All I know is that by some miracle I managed to install WoW and every other patch. This one's beyond me, and what's really frustrating is that I'm absolutely certain that anyone who knows anything about this would be able to do it in two mins flat. 

:(

Full path would indeed help, I kind of missed that.

Something like this:

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft\patch.exe
```

Easiest way would be to open terminal, type wine .wine/drive_c/ then use TAB complete to finish the rest of the path (type a few letters like Pro then hit TAB to complete the directory name. Keep repeating till you're inside the directory where the patch resides.

---

### Post by jalehtor on 2009-06-03
> **nandemonai said:**
> Full path would indeed help, I kind of missed that.

Something like this:

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft\patch.exe
```

Easiest way would be to open terminal, type wine .wine/drive_c/ then use TAB complete to finish the rest of the path (type a few letters like Pro then hit TAB to complete the directory name. Keep repeating till you're inside the directory where the patch resides.

Thank you. I'll try it tonight.

---


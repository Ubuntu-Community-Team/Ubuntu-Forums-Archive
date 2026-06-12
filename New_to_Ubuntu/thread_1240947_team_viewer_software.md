---
title: "team viewer software"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by pafire on 2009-08-15
I'm using Ubuntu 8.04 and after downloading the program Team Player and using Wine to install this .exe the icon will  change, however the program will not open. There are no errors to post.  I have uninstalled & reinstalled both the Team viewer and the wine software several times with the same result. The team viewer software was downloaded from the Wine site as approved to work with Wine.

---

### Post by enli on 2009-08-15
You will get more usable messages when TeamViewer is run from terminal.

To do this, browse to Teamviwer folder from terminal and type
```
wine MainProgram.exe
```

Replace MainProgram with correct filename to that of teamviwer.

You can find out the correct path from Applications > Wine > Browse C: drive and navigate to program files.

---

### Post by pafire on 2009-08-15
enli - I am able to get to the team viewer files by doing the browse on c:, however whatever I type in terminal comes up with no such file or directory

---

### Post by enli on 2009-08-15
Post the output of
```

 wine ~/.wine/dosdevices/c:/Program\ Files/TeamViewer/Version4/TeamViewer.exe

```

Have you installed any additional packages? If not, I think your problem is with not having the runtimes installed. If that is the case:

```
sudo aptitude install wine-doors
```

Start it from Applications > System Tools > Wine-Doors. Fill up the prompts and it should install few necessary packages for your wine installation. 

You then will see list of applications in main window. From top left corner select Show "All available" and enter in Filter "runtime". Install packages : Visual C++ runtimes, Visual Basic runtimes and quit wine-doors. Try running TeamViwer again.

Mine Teamviwer opens but I haven't used it for remote sessions yet, but it should work.

---


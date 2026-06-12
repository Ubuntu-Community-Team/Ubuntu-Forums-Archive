---
title: "How to send command line info to a text file"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by justinmiller87 on 2010-07-05
I'm trying to submit a bug to the Wine forums and in order to do it, I'm running [FONT="Courier New"]wine MafiaBotPro.exe[/FONT] and seeing the log come to the terminal window. I was trying to figure out how to use cat to export it to a text file, but my brain isn't working right now. Can someone please give me a refresher?

---

### Post by sisco311 on 2010-07-05
Redirect stdout and stderr to a file:
```
comamnd &> path/to/error.log
```

---

### Post by amauk on 2010-07-05
You can do something like this to redirect all output to a single file
```
wine windowsapp.exe 2>&1 > ~/Desktop/winapp.log
```

Or if you want to keep the standard output and error output separate, then
```
wine winapp.exe 2>~/Desktop/winapp_error.log > ~/Desktop/winapp_output.log
```

---

### Post by justinmiller87 on 2010-07-05
Much appreciated. Thanks.

---


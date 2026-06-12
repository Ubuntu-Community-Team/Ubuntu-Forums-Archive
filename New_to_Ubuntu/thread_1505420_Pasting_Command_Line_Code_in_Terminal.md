---
title: "Pasting Command Line Code in Terminal"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by oneNF on 2010-06-09
As a new Ubuntu user it is a breath of fresh air, and hours of entertainment.  However to get my Wacom Tablet going I need to run this code [http://ubuntuforums.org/showpost.php?p=9119518&postcount=782](http://ubuntuforums.org/showpost.php?p=9119518&postcount=782). After my third attempt and second install of Ubuntu (don't ask ;-) ) I though, better get some guidance before proceeding.  

In MS-DOS I would just run this as a batch file, in Terminal can I just paste multiple lines of code and run them? 

... or is each line to be copied/pasted and run separately? 

... or is this the time I should be using an && in the code.  

Basic question I'm sure, but I'd appreciate some help.  

Thanks

---

### Post by blchinezu on 2010-06-09
either run each command individually or create a file like this:
```
#!/bin/bash

YOUR COMMANDS
```

and run it from terminal with: bash /path/to/file/filename

---

### Post by KdotJ on 2010-06-09
This is the install code, so Id say you have to do it line by line.
You could write a shell script for it, but it's only a one off to install so I would personally just do it line by line, and that way you get to see the errors (if any) when they occur

---

### Post by oneNF on 2010-06-09
Thanks, Just what I need to know.  
Cheers

---


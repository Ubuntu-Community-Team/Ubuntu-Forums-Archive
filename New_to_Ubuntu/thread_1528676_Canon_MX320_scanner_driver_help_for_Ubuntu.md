---
title: "Canon MX320 scanner driver help for Ubuntu"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by myzenden on 2010-07-11
I just received a Canon Pixma MX320 as a gift.  
 
I am currently running the Ubuntu 10.04 OS
 
I was able to get the printer up and running by downloading the printer  driver for debian linux (3.1) from the Canon site  without any problems.
 
Unfortunately I am not having the same luck with the scanner.
 
I tried downloading ScanGear MP for Linux (deb) (1.3) from the same  Canon site but have not yet been able to get the XSane Image Scanner to  recognize this scanner driver for my Canon.

If I need to add any additional information to help you diagnose the problem please let me know!
 
Any help would be greatly appreciated. 
 
I am not what you would call "computer literate" so please provide me  with a step by step troubleshooting answer if you have an idea on what I  might need to try to get the scanner operational.
 
Thanks for your time!

---

### Post by myzenden on 2010-07-11
Still  haven't had any luck and can't find any additional help online . . .

Anyone have any idea?

---

### Post by myzenden on 2010-07-11
bump

Looking for some driver installation advice for Canon MX320 . . .

Thank you!

---

### Post by myzenden on 2010-07-12
Found this after HOURS of searching in case anyone else runs into the same problem getting their Pixma Canon MX320 scanner working . . .

To quote : 
"Drivers are available in RPM, DEB and also as source files. So after  installing them, I found that the printer works automatically but not  the scanner. To use the scanner, it seems you need to run the command:  scangearmp from the terminal and you get the scanner software you can  use to scan."

The result:

After running the command: scangearmp from the terminal, I was able to actually get the scanner to work. 

This is obviously not a perfect solution because my scanner is still not actually "recognized" by "Simpe Scan" or "XSane Image Scanner".

At this point, every time I want to scan something, I do have to run the actual command in the terminal.

Like I said, it is not a perfect solution but at least my scanner is now operational.

If anyone has anything to add or happens to have a better solution, please let me know as I'd prefer not to have to run a command in the terminal every time I need to scan something.

This isn't a < SOLUTION > per se but at least something to work with . . .

---


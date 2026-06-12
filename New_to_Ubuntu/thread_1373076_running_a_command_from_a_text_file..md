---
title: "running a command from a text file."
date: 2010-01-05
forum: New to Ubuntu
---

### Post by davbren on 2010-01-05
Hey all, I've just started playing about with printers and commands and stuff. So in the terminal, I'm entering in ```
echo -en "\x1bd2" >/dev/usblp0
```

this triggers the blade from the printer to work.

However, if i stick that in a file ```
#!/bin/sh

echo -en "\x1bd2" >/dev/usblp0;

exit 0
```

The printer just prints the line once I run the executable file. 

Any help would be appreciated.

---

### Post by kaibob on 2010-01-06
I'm not familiar with the commands that you are using, but I don't believe the dash (sh) shell supports the -e option with echo. Perhaps you should try your script with the bash shell.

---


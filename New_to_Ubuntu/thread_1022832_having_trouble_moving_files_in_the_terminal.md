---
title: "having trouble moving files in the terminal"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Static_Flow on 2008-12-27
Hello, I'm having trouble moving files from a file to another file. It is telling me that the file .wine/drive_c/Program Files/World of warcraft/dbc is not there even though thats the directory im in this is the code i have been using:

            ```
sudo cp -R .wine/drive_c/Program\ Files/World\ of\ Warcraft/dbc .wine/drive_c/AC\ Web/MaNGOS
```

and its giving me this error: 

                              ```
cp: cannot stat `.wine/drive_c/Program Files/World of Warcraft/dbc': No such file or directory
```

---

### Post by squaregoldfish on 2008-12-27
The destination of the copy command is relative to your current position. Therefore putting .wine as the start of the destination will mean that the copy command will try to find a directory of that name where you are. If you're already in the .wine directory, you need to use:

```
sudo cp -R drive_c/Program\ Files/World\ of\ Warcraft/dbc drive_c/AC\ Web/MaNGOS
```

Steve.

---

### Post by Static_Flow on 2008-12-27
Thanks very much it worked great!

---


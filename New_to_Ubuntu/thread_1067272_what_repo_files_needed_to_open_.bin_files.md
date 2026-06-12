---
title: "what repo files needed to open .bin files"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by bu2971x on 2009-02-11
what do you need to open .bin files like google earth???

---

### Post by taurus on 2009-02-11
You just change the permission to executable and run it from the terminal to install it.

```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
-or-
sudo ./GooglEarthLinux.bin
```

---

### Post by donkyhotay on 2009-02-11
.bin files are like windows .exe files. You just run them, you need to make certain you have execute privileges then run it. A common example is
```
chmod 755 ./somefile.bin
./somefile.bin
```

//edit: be aware like windows executables, unix binaries are generally closed source and can't be reviewed. Make certain the file is downloaded from a source you trust, especially if it requires root access to run correctly.

---


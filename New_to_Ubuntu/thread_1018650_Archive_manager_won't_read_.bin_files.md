---
title: "Archive manager won't read .bin files"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Eldar11 on 2008-12-22
where can I get the implementaion to be able to use .bin files to intall software?

---

### Post by theozzlives on 2008-12-22
> **Eldar11 said:**
> where can I get the implementaion to be able to use .bin files to intall software?

.bin files are kinda like .iso files. I use Power ISO, I don't know if it'll run under wine.

---

### Post by taurus on 2008-12-22
You can run it from a terminal.  Assuming you have saved it to your desktop, 

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x filename.bin
./filename.bin
-or-
sudo ./filename.bin  <-- If you need root privilege
```

---

### Post by Eldar11 on 2008-12-22
see well normally and with all the other systems I've worked with, the archive manager just opens the .bin no problem.  I don't know whats going on, but I know I don't need to use wine to do that.  To install wine itself I would need to un-archive a .bin file so I'd be stuck anyway.

---

### Post by Eldar11 on 2008-12-22
ah thanks taurus!

---

### Post by snova on 2008-12-22
> **Eldar11 said:**
> To install wine itself I would need to un-archive a .bin file so I'd be stuck anyway.

That shouldn't be necessary. It's in the repositories.

---

### Post by Eldar11 on 2008-12-22
how would I access these repositories?

---

### Post by taurus on 2008-12-22
If you want to install wine, try running these commands from a terminal.

```
sudo apt-get update
sudo apt-get install wine
```
Once it's installed, you need to configure it before you can use it.

```
winecfg
```

---

### Post by Eldar11 on 2008-12-22
sweet thanks! i'll do that

---

### Post by Eldar11 on 2008-12-22
when I said to install wine using that command, it gave me this error:

ryan@ubuntu:~/Desktop$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by igknighted on 2008-12-22
> **Eldar11 said:**
> when I said to install wine using that command, it gave me this error:

ryan@ubuntu:~/Desktop$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Can you post the results of the command "cat /etc/apt/sources.list"?  I think you don't have all of the repositories enabled, this should show which ones they might be.

---

### Post by taurus on 2008-12-22
Go to System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for the first four lines (not the Source code).  Then, go to Third Party Software and put a check mark on the first line.  Click Close and Reload.  Now in Quick Search, type **wine** and install it from there.

---

### Post by snova on 2008-12-22
Open System -> Administration -> Synaptic Package Manager. Settings -> Repositories, and make sure the second box is ticked (universe). Then press the Reload button, and try again.

---

### Post by Eldar11 on 2008-12-22
Ah ha! There we go! That did the trick, thanks so much.

---


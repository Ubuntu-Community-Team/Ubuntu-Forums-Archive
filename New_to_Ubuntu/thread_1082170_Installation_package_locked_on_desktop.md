---
title: "Installation package locked on desktop"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by serros88 on 2009-02-27
Hello,

I tried to install Openoffice 3.0 and I unzipped a package on my desktop. So I started the installation but everything went wrong, pages of errors and I stopped!

Finally, I found another way to install Openoffice 3.0 and now it works well.

My problem is that the directory on my desktop is locked (picture) and I dont know why and what to do to erase.

Thanks,
Serge:confused:

---

### Post by taurus on 2009-02-27
Maybe root is the owner of that new directory.  Run nautilus with root privilege to remove it and don't forget to empty the trash bin (for root).

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by hotstovejer on 2009-02-27
It's as simple as opening a terminal, and typing ```
sudo rm /Desktop/nameofdirectory
```

Type your password when it asks for it, and you should be good.

Thanks!

Jeremy

---

### Post by smani on 2009-02-27
As you probably tried to install OOo with root privileges, files modified or created during the installation will also be owned by root. You can delete the folder by typing in the terminal
```

cd ~/Desktop
sudo rm -rf OOO300_m15_native_packed-1_en-US.9379
```
Caution: rm -rf recursively deletes everything from the specified directory without asking confirmation!

---

### Post by dannyboy79 on 2009-02-27
please open a terminal window, hit the alt button and f2 at the same time, this should bring up a dialog box (the run command dialog box). if you're running gnome, type in gnome-terminal in the dialog box that comes up. otherwise you can go to the pseudo start menu and go to accessories and click on Terminal. now within the terminal window, type this in and tell me what it returns.
```
pwd
```
if it returns something like this:
/home/ralph/
than I want you to type this in:
```
cd Desktop
```
now the command
```
pwd
```
should return this
/home/ralph/Desktop
now enter this command
```
ls -la
```
paste the results of this in your response.

---

### Post by thtrgremlin on 2009-02-27
As far as rm,there is no reason to include the -f argument. -f means "ignore nonexistent files, never prompt". While this MIGHT be necessary, it is a terrible thing to assume. -r is recursive such that it will look in folders and remove everything in there too.

I think it would be a much better habbit and advice to say to use ```
sudo rm -rI <path>/<filename>
```

But the best way to do it / learn initially was proposed by taurus; just run nautilus as root, just be careful that you only use that to do what you need to do as root, then close the window.

---


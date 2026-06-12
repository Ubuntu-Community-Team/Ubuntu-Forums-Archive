---
title: "[SOLVED] Trouble with installation of files"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by WiseMaturin on 2008-12-19
Namely, TrueCrypt.
I go to the site, and try to download it.
It says it's supposed to be a .deb file, but when it's downladed it just comes as tar.gz
And when I go to Konsole and try and install it, it shows a shell script on my desktop.
But when I try to run the setup that's been extracted to Desktop, it saves that I can't save the file because it will be corrupted.
Also a problem is that all the file looks like is a bunch of Chinese characters and squares.

I don't have a clue what's going on here.

---

### Post by Elfy on 2008-12-19
Double click it - choose run in terminal and it gives you the option to extract the deb or install it

---

### Post by Michael.Godawski on 2008-12-19
this worked for me
```
chmod a+x truecrypt-6.1a-setup-ubuntu-x86 
./truecrypt-6.1a-setup-ubuntu-x86
```

assuming your file is on the Desktop navigate in terminal to it and run these commands.

---

### Post by JoshuaRL on 2008-12-19
You also might check out Easy Crypt in the repos.  It's a GUI frontend for Truecrypt.

---

### Post by Elfy on 2008-12-19
> **Michael.Godawski said:**
> this worked for me
```
chmod a+x truecrypt-6.1a-setup-ubuntu-x86 
./truecrypt-6.1a-setup-ubuntu-x86
```

assuming your file is on the Desktop navigate in terminal to it and run these commands.

It did just work on a double click - I downloaded it to see what was going on :)

---

### Post by WiseMaturin on 2008-12-20
It's on my Desktop as a tar file, so I double-click it and it goes straight to Ark. It does not give me an option from here to Run in terminal.
It is never a deb file, so all it tries to do is extract the binary, and it won't let me save it because it will "become corrupt".

But the command line functions worked, I just had to extract the deb instead of choosing to install. Then I installed it using the deb that the command line functions gave me.

Thanks so much guys! ^_^

---


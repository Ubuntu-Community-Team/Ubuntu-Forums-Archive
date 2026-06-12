---
title: "Installing Open Watcom C/C++"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by CrystalMV on 2011-06-30
[LEFT]Hello everyone,
First of all, I want to say that Ubuntu is a really great OS. It's easy to get used to - it's only two days since I tried it and it's already easy for me to use. I like it much more than Windows :)
There is, however, a little problem. I use Open Watcom C/C++ for programming and I want to install it on Ubuntu. So I downloaded Watcom for Linux. But I don't know how to install. When I ran the downloaded file, I got an error message: "There is no application installed for executable files". Then I went to properties, permissions and gave the permission to execute the file as program. But when I run the file, nothing happens at all. Am I doing something wrong?
[/LEFT]

---

### Post by seawolf167 on 2011-06-30
I'm not familiar with Open Watcom C/C++, but I'm going to guess that this is a .exe program? If so, you'll need to run it in WINE.

```
sudo apt-get install wine
```I found [this page ]("http://www.openwatcom.org/index.php/Win32ver_on_Linux")showing how to set it up.

That said - if there any reason you don't want to use a native linux program like Geany?

```
sudo apt-get install geany
```

---

### Post by CrystalMV on 2011-06-30
Oh, my bad, I hadn't noticed there were instructions for installing Open Watcom on Linux. No, it's not exe, it's a file without any extension. I tried running Windows version of Open Watcom using Wine and it worked, but I hope I will manage to install Linux version :)

---

### Post by seawolf167 on 2011-06-30
Here is a [install instruction page ]("http://www.openwatcom.org/index.php/Unattended_Installation")I found for it. You may want to take a look at that.

If you don't have to compile anything, but it doesn't have any extension, see if you can find better linux-specific installation instructions. Otherwise I'd start with making the file executable and attempting to run it and see if that works

```
cd /path/to/name.of.file
sudo chmod +x name.of.file
./name.of.file
```

---


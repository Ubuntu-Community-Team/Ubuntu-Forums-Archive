---
title: "Exe?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by bingobingo on 2010-02-09
Why would anyone ever name a command exe to run on linux? What an oxymoron, and a stupid thing to do. I saw this running and killed it.

---

### Post by Bachstelze on 2010-02-09
:???:

I don't know of any command named [font=monospace]exe[/font]...

---

### Post by mechro on 2010-02-09
... if there was a command exe it would depend what it did. I see no problem with calling a command exe?? :???:

---

### Post by tom.swartz07 on 2010-02-09
> **bingobingo said:**
> Why would anyone ever name a command exe to run on linux? What an oxymoron, and a stupid thing to do. I saw this running and killed it.

the process EXE is used by Chrome(ium) for Flash. Im sure you probably saw it because it was hogging your cpu, thats why- the exe process has been known to 'overtask' the CPU.



As far as I could tell, the newer versions of Chrome- dev and daily release- have gotten rid of that. Perhaps if it bothering you, you could update?

---

### Post by falconindy on 2010-02-09
```
find /proc -name exe 2>/dev/null
```
It's not just chromium... The below is outdated, but still mildly valid.

> Under Linux 2.2 and 2.4 exe is a symbolic link containing the actual path name of the executed command. The exe symbolic link can be dereferenced normally - attempting to open exe will open the executable. You can even type /proc/[number]/exe to run another copy of the same process as [number].
Under Linux 2.0 and earlier exe is a pointer to the binary which was executed, and appears as a symbolic link. A readlink(2) call on the exe special file under Linux 2.0 returns a string in the format:

[device]:inode

For example, [0301]:1502 would be inode 1502 on device major 03 (IDE, MFM, etc. drives) minor 01 (first partition on the first drive).

find(1) with the -inum option can be used to locate the file.

---

### Post by lovinglinux on 2010-02-09
Just for the sake of curiosity, there is a xhtml editor called exe. I'm currently using the Windows version under wine, because the Linux version is outdated and I didn't want to compile it. So when I look the System Manager, the program process shows up as exe.exe :)

See attached screnshot.

---

### Post by bingobingo on 2010-02-10
Thanks guys/gals, for the info, I love linux. I am using what ever version of Chrome, Ubuntu passes. And I would have never knew about that command line,  find /proc -name exe 2>/dev/null. Cool thanks again.

---


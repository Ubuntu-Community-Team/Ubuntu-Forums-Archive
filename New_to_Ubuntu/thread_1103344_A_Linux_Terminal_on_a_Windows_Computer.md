---
title: "A Linux Terminal on a Windows Computer"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-03-22
I have always helped my less-computer-literate friends who have Windows. I prefer to run mostly from a CLI, and since Window's DOS prompt is so much different and less versatile from Linux's "Terminal", I was wondering if there was a Linux-type-"Terminal" for Windows that used the same commands (ls, pwd, ps, etc., etc.).

Would anybody be able to point me to a program?

Thanks in advance.

---

### Post by kpatz on 2009-03-22
cygwin ([http://www.cygwin.com](http://www.cygwin.com))

---

### Post by SunnyRabbiera on 2009-03-22
I agree that the linux terminal is actually quite easy, DOS made things harder then they needed to be.

---

### Post by SoulMazer on 2009-03-22
Sounds exactly like what I am looking for!

Thanks kpatz.

---

### Post by Bachstelze on 2009-03-22
Quick FYI: DOS died long ago, the Windows command prompt has no DOS in it anymore.

---

### Post by SoulMazer on 2009-03-22
@Hymn: Oh really? What you you refer to Windows'..."cmd" then? (Not trying to be sarcastic - I actually am curious)

Also, I have installed Cygwin, and it does not seem to want to start once installed. I assume I start it by running the .bat file in the root dir, but it errors and closes itself.

Did I not install correctly or what is my problem?

---

### Post by kpatz on 2009-03-22
> **SoulMazer said:**
> @Hymn: Oh really? What you you refer to Windows'..."cmd" then? (Not trying to be sarcastic - I actually am curious)

Also, I have installed Cygwin, and it does not seem to want to start once installed. I assume I start it by running the .bat file in the root dir, but it errors and closes itself.

Did I not install correctly or what is my problem?Run the .bat file from a command window so you can see the error message...

---

### Post by SoulMazer on 2009-03-22
Oh sorry I was incorrect before. The error message says that "bash" is not recognized as a command.

EDIT: Reinstalled from a different mirror and it is working now. Sorry for the trouble guys. And thank you!

---

### Post by gibxam on 2009-03-23
not to hijack this thread too much but where is the xinit package in cygwin? I've been trying to find it so that I can run apps remotely from a my ubuntu workstation on a windows xp computer. I can find all the packages such as xorg-server, or openssh but I can't seem to find the xinit package. Because of this when I try to run the specified apps I get an Error about the app not being able to be displayed.

---

### Post by kevdog on 2009-03-23
Usually if you have installed cygwin correctly, it should place an Xserver icon on the desktop.  If not you need to start the xserver which for me is located here:
C:\cygwin\lib\Singular\startxserver.bat

---

### Post by anewguy on 2009-03-23
You can also install Mingw and Msys in Windows and get a linux command line by starting msys.  I use it a lot on cross-platform development.

Dave :)

---

### Post by gibxam on 2009-03-23
This is so strange because now I'm on a mac and my school and I know that its using Mac OS X server. I can connect to my computer via ssh 
```
ssh -p #### max@'ipaddress'
``` then I get in. but when I try to run firefox: ```
max@max:~$ firefox &
[1] 6655
max@max:~$ Error: no display specified
```. When I try doing this method from a laptop that I have running Damn Small Linux this method works fine. Why am I getting this error message?

---

### Post by Bachstelze on 2009-03-23
You must enable X forwarding for that to work:

```
ssh -X -p #### max@'ipaddress'
```

---

### Post by gibxam on 2009-03-23
oops sorry Hymntolife I forgot to mention that I also tried that :/ this is the output: ```
max@max:~$ firefox&
[1] 6867
max@max:~$ X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:10.0
```

---

### Post by GepettoBR on 2009-03-23
> **HymnToLife said:**
> Quick FYI: DOS died long ago, the Windows command prompt has no DOS in it anymore.

Funny, even Vista still has a few 16-bit DOS executables hidden in the C:\WINDOWS folder. Why'd they rewrite the command prompt from the actual DOS codebase into a DOS emulator yet keep a bunch of useless legacy programs around?

---

### Post by Kareeser on 2009-03-23
Backwards compatability.

16-bit programs run in a 16-bit shell in the 32-bit or 64-bit environment.

---

### Post by GepettoBR on 2009-03-23
Well, I like the saying about how Windows is a 32-bit shell to a 16-bit OS based on 8-bit code by a 2-bit company that can't stand 1-bit of competition... or something like that.

---


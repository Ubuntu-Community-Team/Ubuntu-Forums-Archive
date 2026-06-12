---
title: "How to run sXe Injected Client on ubuntu"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by sniper7137 on 2010-12-17
Hi all!
I just successfully managed to install ubuntu 10.10 on my PC.

I play counterstrike 1.6 on servers that require sXe Injected to be running.

It works in windows naturally, but how can i run it in ubuntu?

I have tried WINE. sXe installs just fine but returns the error: "MSVPC60.dll not found. Please reinstall the application"

Any ideas will be appreciated. Thanks in advance.

---

### Post by NCLI on 2010-12-17
> **sniper7137 said:**
> Hi all!
I just successfully managed to install ubuntu 10.10 on my PC.

I play counterstrike 1.6 on servers that require sXe Injected to be running.

It works in windows naturally, but how can i run it in ubuntu?

I have tried WINE. sXe installs just fine but returns the error: "MSVPC60.dll not found. Please reinstall the application"

Any ideas will be appreciated. Thanks in advance.

Try downloading MSVCP60.dll. You can get it [here]("http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60"). Extract the ZIP-file, then open your Wine C:/ drive, go to "windows/system32" then copy the extracted MSVPC60.dll into it.

---

### Post by napoleon3665 on 2010-12-17
make sure that you initially have WINE configured correctly, this could be the problem.

---

### Post by sniper7137 on 2010-12-18
Thanks guys. I did as u said and pasted mscvcp60.dll in C:\Windows\System32 dir of WINE. The error did not occur i.e. the program was executed but i got an error from WINE that said the program sXe has encountered a serious error blah blah bhah.

Thanks for your help. Maybe the program isn't meant for linux.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by sameerkof on 2011-04-24
same  problem

---


---
title: "Problem lauching program in Rdekstop and Tsclient"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Lintunen on 2006-08-28
Tsclient and Rdesktop problem.

when trying to make -s and -c tags and correct path. In this case:

-s c:\Program File\Microsoft Office\OFFICE11\MSACCESS.exe
-c c:\Program File\Microsoft Office\OFFICE11\


either it wont find file and says c:program... does not exist or it says that something about \ mark.

Path is indeed corrent and same .rdp file works in Windows Clients and program starts correctly.

If someone have had similiar problems please info me how to start program correctly. Thanks.

---

### Post by f00buntu on 2006-08-28
> **Lintunen said:**
> 
-s c:\Program File\Microsoft Office\OFFICE11\MSACCESS.exe

Hi,

"Program File" should be "Program Files" 

and you need to put the whole command line in quotes like this:

rdesktop -s "c:\Program Files\Microsoft Office\OFFICE11\MSACCESS.exe" MyServerName

f00

---

### Post by Lintunen on 2006-08-28
thank mate

---


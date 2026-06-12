---
title: "Newbie question about viruses in Ubuntu"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Wayne Twine on 2009-05-22
Hi
 
Excuse this ignorant question, but if I get sent a MS Word file with a macro virus, and I open the file in Open Office in Ubuntu, will the file still be infected? If I send it from Open Office saved as a .doc file in Ubuntu, to somebody else using Windows, will they get infected.?.
 
 
 
Thanks

---

### Post by milton1 on 2009-05-22
yes. While ubuntu may not be damaged by the virus, it does not automatically clean it. If you suspect a file has a virus, delete the file or attempt to clean it using an anti-virus program.

---

### Post by mprince on 2009-05-22
From OpenOffice help file:

> 

Macros in Microsoft Office and OpenOffice.org

Microsoft Office and OpenOffice.org cannot run the same macro code. Microsoft Office uses VBA (Visual Basic for Applications) code, and OpenOffice.org uses Basic code based on the OpenOffice.org API (Application Program Interface) environment. Although the programming language is the same, the objects and methods are different.
If you use macros in one of the applications and want to use the same functionality in the other application, you must edit the macros. OpenOffice.org can load the macros that are contained within Microsoft Office files and you can then view and edit the macro code in the OpenOffice.org Basic IDE editor.

My guess would be that it won't save the macro properly. You could test this by saving a macro in a word document... then open it with OpenOffice... then save it with OpenOffice and see if the macro works on Windows side.

---

### Post by juancarlospaco on 2009-05-22
Virus don't infect Ubuntu, but they can infect MS Windows, and in some cases Mac too.
*I recommend you to use .odf .odt .odg file extensions, since OpenOffice is freely avaliable to Windows users.*

---

### Post by Wayne Twine on 2009-05-22
Ok.  Thanks for the replies

---

### Post by donkyhotay on 2009-05-22
> **juancarlospaco said:**
> Virus don't infect Ubuntu, but they can infect MS Windows, and in some cases Mac too.
*I recommend you to use .odf .odt .odg file extensions, since OpenOffice is freely avaliable to Windows users.*

OpenOffice is also freely available for osX users and the most recent versions work very well.

---


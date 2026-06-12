---
title: "Cannot locate '/home/user/Desktop' and &quot;/&quot;"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by User_ on 2011-07-21
Ok, so this is odd... Everyime that I try to either create an empty file/folder or move an application on the desktop I get a message about an error creating/copying the file. In the first situation (creating a file) if I expand the message by clicking on "more info" it says that the file or path '/home/user/Desktop' does not exist. When I try to move an application on the desktop, it will prompt me with a messege that the "/" is not supported.


**Creating a folder/file:**
> "Error while copying to "Desktop"

There was an error getting information about the destination.
[I]
Show more details[/I]
Error stating file '/home/user/Desktop' : No such file or directory



**Moving an application to desktop:**
> Error while copying

There was an error getting information about "/"

*Show more details*
The specified location is not supported


Any ideas why this is happening and how to solve it? (I will post the exact messages in a bit). 

Thanks in advance.

[B]
EDIT[/B]: It seems that the problem is language specific. If I change my language to English the same message appears but with the word "Desktop" changed to my language. The same thing applies when I change from English to my language again.

---

### Post by computerandu on 2011-07-21
Do you see Desktop in the file manager? (In the left side bar when your are accessing your disk in gui)

---

### Post by User_ on 2011-07-21
> **computerandu said:**
> Do you see Desktop in the file manager? (In the left side bar when your are accessing your disk in gui)

Yep it is right there.

---

### Post by computerandu on 2011-07-21
What is the output of ls -a /home/user  ?

---

### Post by babakott on 2011-07-21
Its not a fix, but a work around until you get an answer is to copy the file to /home/<user>/Desktop using your file manager.

---

### Post by User_ on 2011-07-21
> **computerandu said:**
> What is the output of ls -a /home/user  ?


I looked into properties and indeed it is /home/user (if that's what you mean).


> **babakott said:**
> Its not a fix, but a work around until you get an answer is to copy the file to /home/<user>/Desktop using your file manager.

Thanks!

---

### Post by computerandu on 2011-07-21
> **User_ said:**
> I looked into properties and indeed it is /home/user (if that's what you mean).




Thanks!

No...I actually wanted to take a look whether you have Desktop in your home folder or not...if you have accidently deleted or hid it...

---


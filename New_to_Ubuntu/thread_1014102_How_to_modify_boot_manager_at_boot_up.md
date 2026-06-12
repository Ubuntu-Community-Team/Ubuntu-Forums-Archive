---
title: "How to modify boot manager at boot up"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by theamber on 2008-12-17
Hi I have dual boot Vista and Ubuntu but in the start up menu I still have 3 choices one is the old windows version. I have deleted that XP version so how can I remove it from the start up menu?
I use bcdedit under windows but I don't know how to remove the description the old windows version form the start up menu.
Anyone knows how to do that?
Thanks.

---

### Post by icanfly0307 on 2008-12-17
Did you have XP *and* Vista when you installed Ubuntu?

---

### Post by icanfly0307 on 2008-12-17
Okay, back to the procedure.

1. Login to Ubuntu
2. Open up Terminal. Applications > Accessories > Terminal
3. Type *sudo gedit /boot/grub/menu.lst*
4. Scroll down and you should see something like "Windows XP Home Edition".
5. CAREFULLY, get rid of the lines from *title* to *chainloader +1*

That's it! Reboot and you should no longer see you XP entry anymore.

---

### Post by theamber on 2008-12-17
> **icanfly0307 said:**
> Did you have XP *and* Vista when you installed Ubuntu?

Yes I did that is why I need to modify bcdedit in Windows.

---

### Post by theamber on 2008-12-17
> **icanfly0307 said:**
> Okay, back to the procedure.

1. Login to Ubuntu
2. Open up Terminal. Applications > Accessories > Terminal
3. Type *sudo gedit /boot/grub/menu.lst*
4. Scroll down and you should see something like "Windows XP Home Edition".
5. CAREFULLY, get rid of the lines from *title* to *chainloader +1*

That's it! Reboot and you should no longer see you XP entry anymore.

Did not work because Windows boot up menu was installed first.

---

### Post by edwardTheGreat on 2008-12-17
> **theamber said:**
> Hi I have dual boot Vista and Ubuntu but in the start up menu I still have 3 choices one is the old windows version. I have deleted that XP version so how can I remove it from the start up menu?
I use bcdedit under windows but I don't know how to remove the description the old windows version form the start up menu.
Anyone knows how to do that?
Thanks.
Have you tried (From an Windows Admin Command Line)```
bcdedit /?
``` to get a list of all the options.

Then have you run ```
bcdedit /enum
``` to list all the entries in the boot manager and note the id of the one you want to delete

Then use ```
bcdedit /delete ID
``` where ID is the id of the entry in the boot manager you want to delete.

I haven't got my Vista laptop in front of me, but I'm pretty sure that will do the job

Let us know how you go...

---

### Post by c4rson on 2008-12-17
> **icanfly0307 said:**
> Okay, back to the procedure.

1. Login to Ubuntu
2. Open up Terminal. Applications > Accessories > Terminal
3. Type *sudo gedit /boot/grub/menu.lst*
4. Scroll down and you should see something like "Windows XP Home Edition".
5. CAREFULLY, get rid of the lines from *title* to *chainloader +1*

That's it! Reboot and you should no longer see you XP entry anymore.
Thanks!!! U R awesome ive been messing around forever to try to fix the boot loader.
How do i post a question on here im having nvidia problems, with 3d. thanx again -Carson

---

### Post by theamber on 2008-12-17
> **edwardTheGreat said:**
> Have you tried (From an Windows Admin Command Line)```
bcdedit /?
``` to get a list of all the options.

Then have you run ```
bcdedit /enum
``` to list all the entries in the boot manager and note the id of the one you want to delete

Then use ```
bcdedit /delete ID
``` where ID is the id of the entry in the boot manager you want to delete.

I haven't got my Vista laptop in front of me, but I'm pretty sure that will do the job

Let us know how you go...

Can't do it, my ID is {ntldr}
I try:
bcdedit /delete {ntldr}
Does no t delete it I got an error.

---

### Post by edwardTheGreat on 2008-12-17
What was the error?

---

### Post by edwardTheGreat on 2008-12-17
> **theamber said:**
> Can't do it, my ID is {ntldr}
I try:
bcdedit /delete {ntldr}
Does no t delete it I got an error.
Maybe try ```
bcdedit /delete {ntldr} /f
```

I think the '/f' forces the deletion of {legacy} and {ntldr} entries...

---

### Post by theamber on 2008-12-17
It was use the /f option, but I checked /enum and it was not there I restarted it and is gone, thanks a lot problem solved.

---

### Post by edwardTheGreat on 2008-12-17
Good stuff.:guitar:

---

### Post by icanfly0307 on 2008-12-17
@Carson: Go to the "Hardware and Laptops" section in this forum. Click on Thread Tools -> Post New Thread. Good to know you got it working. :)

---


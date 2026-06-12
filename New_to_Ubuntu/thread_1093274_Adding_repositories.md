---
title: "Adding repositories"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-03-11
I am trying to add repositories to my software sources , but the " ADD " button is greyed out . I am signed in as administrator so do I need further permissions ? I have double checked I am typing in the correct URL , but when I click on " add " nothing happens .

---

### Post by kanikilu on 2009-03-11
Are you able to add repositories via the command line?

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by skymera on 2009-03-11
Add the correct repository to the list:

```
 gksudo gedit /etc/apt/sources.list 
```

---

### Post by alexandari on 2009-03-11
well...double check again cuz that can`t be right...

---

### Post by ex-wirecutter on 2009-03-11
Do I need to put the " deb " first before the http:// ?

---

### Post by skymera on 2009-03-11
What are you trying to add??

Are there not instructions or a repository listed?

---

### Post by kanikilu on 2009-03-11
Also, what do you mean by "signed in as administrator" - you should be using a "regular" user account and then using sudo/gksudo to gain temporary root privileges.

Also, try this:

- Press ALT+F2 to get to a "run command" dialog
- Type **gksudo software-properties-gtk** and press enter
- The screen should gray out and ask for your password, enter it
- You should get the Software Sources dialog, go to the Third-Party Software tab and see if the "Add..." button works now.

---

### Post by kanikilu on 2009-03-11
> **ex-wirecutter said:**
> Do I need to put the " deb " first before the http:// ? Yes

---

### Post by ex-wirecutter on 2009-03-11
Thanks thats it then , much obliged .

---

### Post by dubhear on 2009-04-20
> gksudo gedit /etc/apt/sources.list
helped me out somehow too, thanks again.

rgrds

---


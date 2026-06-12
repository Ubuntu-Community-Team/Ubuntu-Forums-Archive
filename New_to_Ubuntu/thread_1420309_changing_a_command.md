---
title: "changing a command"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by nitstorm on 2010-03-02
how do i change a command that is used to start a program?

i have a twitter client called Spaz
and everytime i want to start the program from the terminal i have to type

/opt/Spaz/bin/Spaz

how do i start the program by just typing Spaz in the terminal?

---

### Post by sandyd on 2010-03-02
> **nitstorm said:**
> how do i change a command that is used to start a program?

i have a twitter client called Spaz
and everytime i want to start the program from the terminal i have to type

/opt/Spaz/bin/Spaz

how do i start the program by just typing Spaz in the terminal?
```

sudo -s ln /opt/Spaz/bin/Spaz /usr/bin/Spaz

```

---

### Post by nitstorm on 2010-03-02
i understand that command creates a link to the place where all the other apps are stored, tried it but i get this error message from Adobe AIR which was originally required to install Spaz:

> This installation of this application is damaged. Try re-installing or contacting the publisher for assistance.

if this is of any significance, the /opt folder has 2 sub-folders Adobe AIR and Spaz

---

### Post by x33a on 2010-03-02
> **carlee said:**
> ```

sudo ln /opt/Spaz/bin/Spaz /usr/bin/Spaz

```

or you can add this to your ~/.bashrc
```
alias spaz='/opt/Spaz/bin/Spaz'
```

---

### Post by delectate on 2010-03-02
alias is good  

edit ~/.bashrc

---

### Post by sandyd on 2010-03-02
> **nitstorm said:**
> i understand that command creates a link to the place where all the other apps are stored, tried it but i get this error message from Adobe AIR which was originally required to install Spaz:



if this is of any significance, the /opt folder has 2 sub-folders Adobe AIR and Spaz
try the edit i just made.
after deleting the current link i mean.
or add to your path, like the above posters said.

---

### Post by nitstorm on 2010-03-02
thread  solved :D alias works. thanks x33a, delectate and carlee for all ur super-quick replies. cheers!

---

### Post by nitstorm on 2010-03-02
> **carlee said:**
> try the edit i just made.
after deleting the current link i mean.
or add to your path, like the above posters said.


nah still the same issue, alias seems to work though, hence problem solved :D thanks again everyone :D

---


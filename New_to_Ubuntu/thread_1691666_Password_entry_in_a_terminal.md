---
title: "Password entry in a terminal"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Phil's Dad on 2011-02-20
I have Ubuntu 10.10 installed and am trying to install my HP Deskjet 3050 printer so I need to install hplip. Following the instructions on the HP web site and info picked from a forum, I have prefixed my first command line with 'sudo' (no apostrophes) followed by the hplip file name and am then asked for my user password. When I type the password in, nothing happens. There is no indication that anything has been entered - the flashing cursor does not move, there are no dots - nothing. After three attempts the program exits so hplip is not installed. Can anybody help, please?

---

### Post by JC Cheloven on 2011-02-20
An HP printer should work out of the box. Have you tried to simply plugging it and see if it works?
JC

EDIT: as for the password thing, it's normal behaviour. Simply type in, and press enter. Security rules in linux ;)

---

### Post by nick_goodfate on 2011-02-20
Just type your password. It's normal to not see anything when you type your password in terminal.

---

### Post by Phil's Dad on 2011-02-20
I have tried most things to get this to work. If I start from scratch and go to System-Administration-Printing then use "Add" I can follow the wizard but my printer model is not listed. I have tried the driver which is suggested but the printer does not print a test page when requested.

---

### Post by Phil's Dad on 2011-02-20
I tried that but after three attempts, the program exits.

---

### Post by hakermania on 2011-02-20
alternatively, you can use
```
echo "password" | sudo -S hplip file
```
where password is your login passwd.

---


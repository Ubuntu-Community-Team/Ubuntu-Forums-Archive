---
title: "Does anyone know how to make Lucid lynx from asking me for password everytime ?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by cool Cpu on 2010-08-22
hi every time i open shell im asked for password and thats the problem cuz my password has 20 letters numbers and symbols.

so every time i want to open a shell i have to type password again and again how to stop Ubuntu from asking me for password ?

---

### Post by surfer on 2010-08-22
you mean while you are logged in, when you open a terminal you are asked for a password? that shouldn't be like that? or did i misunderstand something?

---

### Post by nebu on 2010-08-22
u can use policykit....

check this thread [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308528](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308528)
pjomegas postwas useful when i had tried this out

---

### Post by cool Cpu on 2010-08-22
> **surfer said:**
> you mean while you are logged in, when you open a terminal you are asked for a password? that shouldn't be like that? or did i misunderstand something?


i mean every time i want to open a shell ubuntu is asking for password and im tired of it thats all

---

### Post by cool Cpu on 2010-08-22
> **nebu said:**
> u can use policykit....

check this thread [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308528](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308528)
pjomegas postwas useful when i had tried this out

i did and it is working im not asked for password any more tnx

---

### Post by aysiu on 2010-08-22
> **cool Cpu said:**
> i mean every time i want to open a shell ubuntu is asking for password and im tired of it thats all
Use ```
sudo -i
``` It'll give you a persistent root prompt so you won't be asked for a password for every *sudo* command.

P.S. If you run a lot of *sudo* commands frequently, consider changing your password to something easier to type. There's a fine line between security and usability, and you're clearly too far on the security side if you don't want to type your own password.

---

### Post by Iowan on 2010-08-22
> **aysiu said:**
> There's a fine line between security and usability, and you're clearly too far on the security side if you don't want to type your own password....Which makes the pendulum swing the other way if you  want to bypass the password...

---


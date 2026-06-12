---
title: "unable to access system configuration"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by minimagician on 2009-08-19
I have added the username to sudoers file, giving this particular username all access rights. Then I create a new user through terminal, which gets created. When i try to access System->Administration->Users and groups to modify the properties of the newly created user, i get a error message:
Configuration cannot be loaded
you cannot access the system configuration.


I am new to ubuntu and using ubuntu 9.04. how do I solve this issue and access the System Configuration?

Thanks!

---

### Post by SuaSwe on 2009-08-19
Looks like you've somehow lost system privileges!

Try booting into recovery mode (there should be an option in the GRUB menu), type 'visudo' (no quotes) in Terminal and add your username to the sudoers file.

More details:

[http://linux.about.com/library/cmd/blcmdl8_visudo.htm](http://linux.about.com/library/cmd/blcmdl8_visudo.htm)

---

### Post by minimagician on 2009-08-30
Hey thanks!

---


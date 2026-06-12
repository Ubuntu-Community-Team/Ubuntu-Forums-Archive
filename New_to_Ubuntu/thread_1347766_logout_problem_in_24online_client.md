---
title: "logout problem in 24online client"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by sajib on 2009-12-06
hi guys,i've just stepped into linux world.installed ubuntu 9.10 with vista,as dual os.established connection through 24online client.the problem here is i can't logout by using "./crclient -u (my user name)>".after pressing enter the following line appears on the terminal:'non-option ARGV-elements: (my user name)'.need some help!!!!!!!thanks in advance.........

---

### Post by talsemgeest on 2009-12-06
> **sajib said:**
> hi guys,i've just stepped into linux world.installed ubuntu 9.10 with vista,as dual os.established connection through 24online client.the problem here is i can't logout by using "./crclient -u (my user name)>".after pressing enter the following line appears on the terminal:'non-option ARGV-elements: (my user name)'.need some help!!!!!!!thanks in advance.........
Try running ```
./crclient --help
```, that should tell you what the correct syntax is. As it is, it is not accepting the username as a valid argument.

---


---
title: "Using chown to change permissions"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-14
Hi,

I am trying this command to change permissions so that Vuze4 can update:

> sudo chown myusername:myusername/usr/share/vuze


But receive the following problem:

> chown: missing operand after `myusername:myusername/usr/share/vuze'

Try `chown --help' for more information.

I want to allow vuze access to the folder so it can update. 

Could someone be so kind to post the correct command I need to type into the terminal. Thanks.

---

### Post by insane_alien on 2008-12-14
there should be a space between the second 'myusername' and the /

---

### Post by Swerve1000 on 2008-12-14
Thanks insane_alien!

---


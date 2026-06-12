---
title: "System variables in init.d"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by jsloan on 2009-03-08
I'm trying to define some variables that can be used in the init.d scripts in a server configuration (i.e. no user logins).

I tried /etc/profile.d but I don't think the variables are available when the init.d scripts are run. 

Is there an easy way to do this? 

i guess i could write an init.d script that starts early and exports variables before the other init.d scripts start.

---

### Post by sdennie on 2009-03-08
Try editing /etc/init.d/rc.  You'll see how the path is set at the top of the file.

---


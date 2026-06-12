---
title: "add users with only game and office menu"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by tommynz1975 on 2009-11-09
Hi guys I haven't been too successful searching, maybe using the wrong words.

I am wanting to know about when adding a user can it be customized durring the add-user stage.

for example to only have the games menu or the office menu , adding **places** and other menu and sub menu options if and when required by that user


I would appreciate being pointed to a howto. If its not a cut and dry task should this be something posed on [HTML]brainstorm.ubuntu.com[/HTML] to be added to the admin users account

---

### Post by phillw on 2009-11-09
Hi.

Off the top of my head, I'd suggest trying out edbuntu.

It lives over here and may suit your needs to a 'T' -->> [http://edubuntu.org/](http://edubuntu.org/)

Regards,

Phill.

---

### Post by tommynz1975 on 2009-11-09
Many thanks Phill.

I know of Edubuntu but wondered if their was another way ofI increase my learning.

---

### Post by phillw on 2009-11-09
> **tommynz1975 said:**
> Many thanks Phill.

I know of Edubuntu but wondered if their was another way ofI increase my learning.


For customisation like you want, I think that the team have done all the hard work already - I'm not a fan of re-inventing the wheel :lolflag:

I'm sure, as all ubuntus, are ubuntu, that it can be done - but that route may be a lot more straight forward. As for learning, that is a real good site & you'll learn loads :p

General background stuff for Ubuntu can be found via my info link, follow it to linux area, then resources, there's enough there to keep you busy ;-)

Regards,

Phill.

---

### Post by tommynz1975 on 2009-11-09
Thanks again Phill

I have found another starting point (learning process) Possibly somethng like what I wanted, I dont yet know

This link talks about the config files for the menu system (how it works) and editing them.

[HTML]https://help.ubuntu.com/community/CorporateUbuntu#GNOME%20Menu [/HTML]

> 
**GNOME Menu**

 Although the GNOME menu system has improved greatly in 2.12, there still is a lack of a tool for editing the GNOME menu on a system-wide basis. GNOME menu configuration, therefore, still needs to be edited on the command line. 
The GNOME menu consists of a collection of desktop files in the /usr/share/applications directory. Inside each file is a Categories line which determines where the menu entry exists. A small number of system tool desktop files exist in /usr/share/control-center-2.0/capplets. 
The first step in "trimming the fat" from the GNOME menu is to create a disabledapps directory under /usr/share/applications: 

```
ncampbell@naaman:~$ sudo mkdir /usr/share/applications/disabledapps
```Next, determine which apps stay and which apps go.


I hope my question has helped others with their learning.

---


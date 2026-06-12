---
title: "Why does ubuntu create new group for every desktop user?"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by bbala2020 on 2010-11-14
Why is that every desktop user in ubuntu have a default group with the same name as username and it is created automatically? Why not have a common group by default group like desktopusers ? I know this can be done later, but why not by default?

---

### Post by bbala2020 on 2010-11-15
No replies yet. :(
Is it a trivial question?

---

### Post by oldos2er on 2010-11-15
No it's not trivial, it's fundamental to Linux security. Maybe something here: [http://www.vtc.com/products/linux-security-tutorials.htm](http://www.vtc.com/products/linux-security-tutorials.htm) under the Users and Groups section will help.

---

### Post by sisco311 on 2010-11-15
> **bbala2020 said:**
> Why is that every desktop user in ubuntu have a default group with the same name as username and it is created automatically? Why not have a common group by default group like desktopusers ? I know this can be done later, but why not by default?

In case of 3 or more users, it's easier to share a file or directory with only one of them. 

The "common group" approach is also valid. In that case, it's easier to share a file with all of the users.

---

### Post by endotherm on 2010-11-15
I think it's largely because every dir is expected to have a group associated, but there will always be files that are just for me. if I have to have a group, but there is no group with just me in it, how could I make sure that I am the only one who can get to the file?

PS: I do add all my users to the Users group, and use it as owner group on most of my shares. that + setgid makes sure that everyone can do what they need to with shared files(except delete; that is for me alone).

---

### Post by bbala2020 on 2010-11-20
> **endotherm said:**
> I think it's largely because every dir is expected to have a group associated, but there will always be files that are just for me. if I have to have a group, but there is no group with just me in it, how could I make sure that I am the only one who can get to the file?

PS: I do add all my users to the Users group, and use it as owner group on most of my shares. that + setgid makes sure that everyone can do what they need to with shared files(except delete; that is for me alone).

If you want a file just for you, you can set read write permissions only to you. Like chmod 700 the_file.
What is the use of a single person group?

---


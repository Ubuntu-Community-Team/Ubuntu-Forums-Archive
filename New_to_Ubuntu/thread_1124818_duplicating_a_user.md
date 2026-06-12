---
title: "duplicating a user"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-13
how to duplicate user?

**example:** i have my user account and then another for brother..

assuming 'brother' is second username..
how to make 'brother2' with all same settings, down to desktop preferences, permissions, etc..

**side note 1:** what is the proper term for "username" as i have used it above? is it account? or just simply user? or is it something else.

**side note 2:** sometimes, while im typing stuff, like here, the keystroke gets recorded one or two times more.. its usually only the space bar every few two paragraphs or so.. also its random (meaning not consistently occuring in the begining, middle, or end of a sentence, paragraph, etc... how to fix?

**thanks!**

---

### Post by supersonicdarky on 2009-04-13
1) create new user
2) copy over everything from original account's home folder to the new one

you'll probably want to chown all the files to the new user

---

### Post by antikristian on 2009-04-13
If you are planning on creating alot of users, you could copy the changes you would like to include into /etc/skel which is the default directory that gets copied into every new users home folder

But if it's only for one or two users, the above suggestion about copying and changing permissions would suffice:)

sidenote 1 
According to RFC 3421, a UNIX profile is to be reffered to as a "user account"***

Sidenote 2
Can't help here, but that sounds really annoying, It doesn't sound like I had the same problem, but it brings me back to a couple of laptops I have had with oversensitiv touchpads that suddently make you continue a sentence in the middle of a page you have just written:-P 

On the otherhand I used to have a similar problem on a toshiba laptop (sluggish performance, repeated keypress) when I ran the opensource nvidia drivers, problem disappeared when I installed the closed source drivers.



***Just kidding, I really have no clue about the naming;-D As long as it sounds sensible in the context I guess all of your suggestions would be just fine, I call it either the home folder or the profile of a user:-)

---

### Post by mprince on 2009-04-14
> **ayastona said:**
> 
**side note 2:** sometimes, while im typing stuff, like here, the keystroke gets recorded one or two times more.. its usually only the space bar every few two paragraphs or so.. also its random (meaning not consistently occuring in the begining, middle, or end of a sentence, paragraph, etc... how to fix?




You might want to take a look at 'Bounce Keys' under 

System>Preferences>Keyboard>Accessibility tab

---


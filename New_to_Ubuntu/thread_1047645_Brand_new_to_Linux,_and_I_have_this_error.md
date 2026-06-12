---
title: "Brand new to Linux, and I have this error"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Quijada on 2009-01-22
Hi, I am new to Linux. I installed Ubuntu hardy heron about two weeks ago on a computer a friend built me. Everything worked fine, but now I get a error message saying that I am not authorized to access system configuration. I tried going to System, Admin, Login window, Security, Allow local system admin login. I cannot acess my network ect... 

 I do apologize if this is a frequent question, and I missed it...

---

### Post by StOoZ on 2009-01-22
does it require a password? if so , use the root password..

---

### Post by Muffinabus on 2009-01-22
Did you create a new user?  If so you probably don't have admin privileges on your new user and you'll have to go back to the original user and give yourself access.

---

### Post by Coreigh on 2009-01-22
Actually if it is asking for a password the correct password to uses is the same password that you use to login with.

If it is not asking for a password what does it say? Is there an alert or error message? Specifically what are you trying to access and how are you getting there?

---

### Post by Patricrawley on 2009-01-22
Tell us exactly what you did leading up to it no longer working.

---

### Post by Quijada on 2009-01-22
I am the admin account. I can use my  password to validate admin only things in terminal, but I am blocked from accessing system configurations. The message says that I am not authorized, but I am the admin account.

---

### Post by Quijada on 2009-01-22
I added a new account that had restricted privileges.

---

### Post by Quijada on 2009-01-22
When I am on the admin account, I try to access network, or user accounts and it tells me that I am not authorized to access system configuration. I understand that I may not be giving exactly what you want to hear, but I am about as knowledgeable about Linux as my grandparents on computers. Not very much.

---

### Post by Patricrawley on 2009-01-22
Post the exact error message that you're recieving. We might be able to understand the problem a little better if we had that information.

---

### Post by Quijada on 2009-01-22
The configuration could not be loaded

You are not allowed to access the system configuration.





*(I am able to access the internet by using the terminal- sudo pppoeconf)

---

### Post by Patricrawley on 2009-01-22
Are you sure you did not accidently restrict all users privledges?

---

### Post by Facetious Falcon on 2009-01-22
When does this error message appear, as soon as you login?

---

### Post by Quijada on 2009-01-22
Thanks guys, got a friend to solve problem. I would have to say the response was almost immediate to my question. Kudos to all of you who tried to help. :popcorn:

---


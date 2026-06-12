---
title: "Evolution Mail password request"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by johnnie1uk on 2010-12-10
Hi 
has anyone got the answer
although i have checked remember password, without fail everytime i send/recieve mail the password request window opens. i can cancel it and still recieve mail, although occasionally i have to put in my password to complete the process.

i am useing version Ubuntu 10-10

---

### Post by karthick87 on 2010-12-10
May be you have configured it wrongly.Check out your seetings once again with the following link..

[http://www.simplehelp.net/2007/08/11/how-to-set-up-evolution-for-email/](http://www.simplehelp.net/2007/08/11/how-to-set-up-evolution-for-email/)

---

### Post by johnnie1uk on 2010-12-10
Thanks, the link you refer to tells you how to set up evolution mail when you first start useing it,
when you later set up another new account i dont get a request for password anywhere and no new window for password
If i leave Evolution open my emails are coming through automatically as evolution checks at the specified interval of time. but if i click send recieve i get the password request.


A-brit-in-spain.blogspot.com

---

### Post by grojo on 2010-12-13
Hi,

I had the same problem and I found a solution.

*Note*: being French, I may not give the proper names to all the shortcuts, files or applications I mention here.

The problem came from Seahorse, which had a default keyring folder I couldn't delete. I think Evolution used that folder, although another one ('login' in my case) was ticked as 'default'.

**Solution:**
- delete all Evolution password entries in Seahorse (*Application/accessories/Passwords and Encryption keys*): expand the login folder (or the one you have the Evolution pwd in) and delete them.
- open *~/.gnome2/keyrings/* folder. You should have there a **default.keyring** file (or something similar), along maybe a **login.keyring **and so on. The **default.keyring **file is the one to get rid of.

```
sudo rm ~/.gnome2/keyrings/default.keyring
```- check in Seahorse that the default folder has gone.
- open Evolution and you should from now have to retype your password only once.

Hope it works for you.

---

### Post by johnnie1uk on 2010-12-14
Thanks i will give it a go

regards
 A-brit-in-spain.blogspot.com

---


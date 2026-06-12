---
title: "How do i password protect a folder??"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-15
and can i use a different password from my log in password?

---

### Post by spiderbatdad on 2009-12-15
here's one way
```
sudo adduser private
mkdir private
chmod 700 private
sudo chown private:private private
```
This makes a user named private, creates a directory named private in your home directory, changes the permissions so that only the owner can see it, and finally, changes the owner to the user private.

---

### Post by Diametric on 2009-12-15
Good post.  Also, good explanation about how to create a user to protect any sensitive data.  While the information I've come across suggests to do just that, create a new user for different task you may need to perform, I've always wondered why simple password locking of files/folders wasn't readily available.

---

### Post by spiderbatdad on 2009-12-15
I was trying to find something better as I was posting. I did find ccrypt in synaptic. It works on files and is a command line utility, but pretty straight forward in its use.
```
ccrypt ~/somefile
you get prompted for password (encryption key)
and voila.
ccrypt -d ~/somefile
...and so on
```
Not what most of us want when we want to password protect a single directory in our home directories.

---

### Post by spiderbatdad on 2009-12-15
Another afterthought, if you make the permissions 733 you'll be able to write to it without switching users.

---

### Post by Ong on 2009-12-15
You can use Cryptkeeper (in the repos) if you want something graphical.

---

### Post by JamesParnell on 2009-12-16
thanks for the cryptkeeper, its easier for the novice linux user :P.

---

### Post by bluelamp999 on 2009-12-16
There's also TrueCrypt - [http://www.truecrypt.org/](http://www.truecrypt.org/)

Might be overkill but it's extremely secure...

---

### Post by wojox on 2009-12-16
There's also seahorse-plugins in the repo's. Nice right click and encrypt.

---

### Post by Hampster on 2009-12-17
Wow.. Thanks people from a very appreciative forum surfer.

---


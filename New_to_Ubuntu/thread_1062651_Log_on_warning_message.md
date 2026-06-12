---
title: "Log on warning message"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by OllieGab on 2009-02-07
When logging on now I get a a warning message (which stops the booting process until I OK it).
It reads "users $HOME/.dmcr file is being ignored....user's $HOME directory must be owned by user and not writeable to other users"

It doesn't stop me booting the system but it's a bit annoying and as far as I know I haven't done any major changes to the system.

Ollie

---

### Post by theinnercityhippy on 2009-02-07
This can be solved using the solution found here:

[http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/](http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/)

It seems to be a fairly common error and revolves around ownership of files and your home folder.

First open a terminal by going to Applications > Accessories > Terminal

Then, for the remainder we will assume your username as ubuntu, but change this to your username where it appears eg bob, susan etc

First we need to set the ownership of your home directory so that only you (and root) have full read/write/execute access to it

```
ubuntu@computer-$ sudo chmod 700 /home/ubuntu
password:
```

Remember, substitute ubuntu for your username. Enter your user password and then type the following to sort out the permissions for that file;

```
sudo chmod 644 /home/ubuntu/.dmrc
```

Now when you reboot, this problem should be solved.

:-)

Hope this helps

-JimDog*-

---

### Post by OllieGab on 2009-02-07
Cheers JimDog
That sorted the problem out right away!

I'm really impressed each time I "consult the community" for the quick responses and the willingness to help out!
:D

Ollie

---


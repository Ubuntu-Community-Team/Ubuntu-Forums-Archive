---
title: "error message at Terminal"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by al.adab on 2009-05-22
hello

I've tried to install Picasa (following the directions at [http://www.dedyisn.net/2009/05/how-to-install-picasa-3-on-ubuntu-jaunty-904/](http://www.dedyisn.net/2009/05/how-to-install-picasa-3-on-ubuntu-jaunty-904/) to 

and after adding *deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free* and running *sudo apt-get update* I get the following message: 

[I]Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems[/I]

Can you help? (also to install Picasa...) Thanks!

---

### Post by raymondh on 2009-05-22
At terminal, type (replacing KEY with the exact code you were given on the error message.... A040830F7FAC5991 )

```
    gpg --keyserver subkeys.pgp.net --recv KEY
```

Then (again replacing capitalized KEY with the same code)

```
      gpg --export --armor KEY | sudo apt-key add -
```

Then

```
 sudo apt-get update
```

Regards

---

### Post by al.adab on 2009-05-22
it worked! thanks!!!

---

### Post by raymondh on 2009-05-22
your welcome.  Keep those commands handy :)

Happy Ubuntu-ing

---


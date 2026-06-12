---
title: "Passwording Files So that apps and users need to give a password to access them"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-26
Said by: [http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

> **Store a password(s) behind a password**. Basically this means that we require you to type in some passphrase as Pidgin or Finch starts in order to read the accounts.xml file, and, to be truly secure, require you to type it again if you write to it. Windows ICQ does something very similar to this if you set it to its highest security settings.

How can I do this in Ubuntu? Creating a PGP key doesn't help at all, because pidgin can't open a pgp file.

---

### Post by coldReactive on 2009-08-29
Bump

---

### Post by ainsworth_t on 2009-08-29
Since it can't read a pgp file, by default, try writing a script that decrypts and re-encrypts everytime you run pidgin as suggested by the same site:
> If you really wanted to, you could write a script to wrap Pidgin or Finch that would decrypt accounts.xml and re-encrypt it when the application exits. You wouldn't be able to encrypt it while they are running, because libpurple clients write to accounts.xml for things like info change

---

### Post by coldReactive on 2009-08-29
> **ainsworth_t said:**
> Since it can't read a pgp file, by default, try writing a script that decrypts and re-encrypts everytime you run pidgin as suggested by the same site:

Sadly, I have no coding experience in computer programming languages at all.

---

### Post by ainsworth_t on 2009-09-03
> Sadly, I have no coding experience in computer programming languages at all.

Fortunately, if you know the commands to run at the command line to un-encrypt the file, launch Pidgin, then re-encrypt the file when you close Pidgin, you know all the "programming language" you need to know.

At it's basic level, a shell script is just a collection of commands stored in a text file. So all you would have to do is create a Bash script to perform the above mentioned items.

Check out the following guides:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

If you don't want to deal with all this, check out the Empathy IM client, which will become the default client in Ubuntu 9.10. It uses the gnome-keyring to store all passwords in an encrypted format.

---

### Post by coldReactive on 2009-09-03
> **ainsworth_t said:**
> Fortunately, if you know the commands to run at the command line to un-encrypt the file, launch Pidgin, then re-encrypt the file when you close Pidgin, you know all the "programming language" you need to know.

At it's basic level, a shell script is just a collection of commands stored in a text file. So all you would have to do is create a Bash script to perform the above mentioned items.

Check out the following guides:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

If you don't want to deal with all this, check out the Empathy IM client, which will become the default client in Ubuntu 9.10. It uses the gnome-keyring to store all passwords in an encrypted format.

I'm sorry but, empathy really makes me want to hurl. So that's a no go both ways. They're also thinking of bringing pidgin back to Ubuntu because of the video/audio support. But they were too late in putting it back into 9.10.

---


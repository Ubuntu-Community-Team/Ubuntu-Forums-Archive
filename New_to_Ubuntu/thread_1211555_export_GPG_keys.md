---
title: "export GPG keys?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by nynoah on 2009-07-12
How do I export GPG keys on my system.  I want to do a fresh install but don't want to lose those keys.  It will save me the time of relooking for all the extra repos that I have added.

Thanks

Why is it that I can never get help?  What is it.  I have had like 10 un answered threads in the last year.

---

### Post by nynoah on 2009-07-12
Bump.......... help?  I have the repos from BT4 and I don't want to lose them.  I can't remember how I got them to work but I do.

---

### Post by lindsay7 on 2009-07-12
This is a great write up and may save you some time.

[http://georgia.ubuntuforums.org/showthread.php?p=7418021](http://georgia.ubuntuforums.org/showthread.php?p=7418021)

---

### Post by nynoah on 2009-07-12
Great post......... i scanned it and nothing about what I was asking.  I am just going to reinstall and worry about it later.  I am itching to try Ultimate edition 2.2 :)  So off for another 5 hours wasted reconfiguring my rig.  But its fun and free.

---

### Post by lindsay7 on 2009-07-12
Just copy the key numbers down somewhere, you just need the last 8 digits.

Here is how you add them, where is says KEY put in the key number xxxxxxxx



gpg --keyserver subkeys.pgp.net --recv KEY

gpg --export --armor KEY | sudo apt-key add -


Here is the info from another post

>  Re: No_pubkey
That is asking you for the public key to that repository. In linux you will see lots of people sign programs,emails, etc with a public key. Some repositories have a public key which you need to download to access. There are a few pages on wikipedia about it [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
All you need to know is the process to use when you see that. This is the template
Code:

    gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

When you get an error message, replace the word "KEY" with the numbers in the eror message. For your error you would enter this command
Code:

 gpg --keyserver subkeys.pgp.net --recv F120156012B83718

After you press enter and it sends the command, you would enter the second line
Code:

 gpg --export --armor F120156012B83718 | sudo apt-key add -

After that, the key will be added to a list and the error will not appear.

---


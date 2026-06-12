---
title: "apt-get to install a specific php version"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by amodpandey on 2011-09-03
Hi,

I have 11.04. The apt-get is picking up 5.3.5 version of PHP. I want to install 5.3.6. In this regard I have the following questions:

> How do I instruct apt-get to pick 5.3.6 and not 5.3.5?

> Is the source of the packages (the ppa locations) maintained by third party. Say, not by php.net in case of php?

> suppose if I have tar of php5.3.6 how do I achieve a similar behavior as 'apt-get install php5'

Regards
Amod

---

### Post by gnometorule on 2011-09-03
For very specific requests, I suggest going to the software center instead of doing apt-get. You won't find every version of every software ready for install using apt-get etc, and if you confirm you can't get the version you would like using the software center or apt-get, I'd think long and hard if you really need the most recent one. If not, just take the most recent offered via apt-get.

If you do need, or want, the most recent, try to track it down as a so-called '.deb' file someplace. Go to the ubuntu documentation and check 'installing .deb files' or 'using alien' or similar, also read the man page of tar. Installing a .deb is also pretty easy as it handles dependencies. 

If you're new to Ubuntu, i wouldn't recommend doing anything but .deb files or getting it easy via apt-get.

---


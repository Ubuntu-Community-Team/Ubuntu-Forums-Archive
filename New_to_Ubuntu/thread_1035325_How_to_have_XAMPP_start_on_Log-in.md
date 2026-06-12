---
title: "How to have XAMPP start on Log-in"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by jlhaslip on 2009-01-09
Recently upgraded from Ubuntu 8.04 to 8.10. All went well, except I had an XAMPP installed on 8.04 to start on Log-in but now it must be started manually, and I would like to have it set as a service on Log-in.

As a Rookie Linux user, I prefer to use the Development software from XAMPP rather than installing all the Modules separately rather than get my hands dirty with the individual packages, if that makes a difference.

Thanks in advance.

---

### Post by supererki on 2009-01-09
system -> preferences -> sessions -> add..

---

### Post by Raynman37 on 2009-01-09
Go to *System > Preferences > Sessions*, click Add and in the command area type:

```
sudo /opt/lampp/lampp start
```

EDIT: Whoops, yeah put sudo in front.

---

### Post by supererki on 2009-01-09
sudo /opt/lampp/lampp start

is the command you probably want to add...

---

### Post by jlhaslip on 2009-01-14
Sorry about the delay getting back to this issue, but the instructions above do not seem to be effective. I can find the opt/lampp/lampp file on my filesystem okay, and I copied the sudo command directly from here, but the method suggested does not work to start apache on Log-in. And the command is still in the session list when I check it.

I can use the Applications panel to start the server, but would really prefer that it fire up on system startup.

any other ideas?

and thanks for the help so far. appreciate your time.

---

### Post by knobuddixspexdazpanishinq on 2009-01-14
[Xampp Linux FAQ]("http://www.apachefriends.org/en/faq-xampp-linux.html#fsl") has the steps to enable this for you. It's a good idea to make sure you are running the [latest version of Xampp]("http://www.apachefriends.org/en/xampp-linux.html#374") first and to make sure [Xampp is secured]("http://www.apachefriends.org/en/xampp-linux.html#381"). :p

see: [http://www.apachefriends.org/en/faq-xampp-linux.html#fsl](http://www.apachefriends.org/en/faq-xampp-linux.html#fsl)
and: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)
and: [http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)

hth
cheers,
M

---


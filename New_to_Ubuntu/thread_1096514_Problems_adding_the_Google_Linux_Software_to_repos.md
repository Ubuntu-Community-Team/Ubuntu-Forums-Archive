---
title: "Problems adding the Google Linux Software to repository"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ed89 on 2009-03-15
I'm trying to follow instructions listed [here]("http://www.google.com/linuxrepositories/apt.html"), but what Terminal gives me back is this (after running the first command):

```
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

```

What to do? Thanks!

---

### Post by RetchingRabbit on 2009-03-15
Did you download this first?

[https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub)

---

### Post by ed89 on 2009-03-15
I didn't do that first, but I tried now and I get the same error. It says "Run these commands as root" on the google-website - what exactly does that imply? Thanks.

*I got it! Thanks!*

---

### Post by mocoloco on 2009-03-15
You might have missed the phrase before the instructions "Run these commands as root".  If you want to be able to past in their commands, first run "sudo -i" to become the root user in your terminal.
Since it looks like you're new to Ubuntu though, I would suggest using their [GUI instructions]("http://www.google.com/linuxrepositories/ubuntu704.html").  It says Ubuntu 7.04 but it will work in newer versions as well.

---

### Post by ed89 on 2009-03-15
Thanks, mocoloco. I figured it out - and I got to use the command line :-)

---

### Post by teamcoltra on 2009-03-15
Google actually lays out some pretty good step-by-step instructions, you should not even have to do it in the command prompt.

[http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html)


However, if you want to do it in the command line type the following (or actually I would suggest copy and paste to paste into the comand prompt use CTRL SHIFT V)

```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
apt-get update
```

```
gksudo gedit /etc/apt/sources.list
```

when the window pops up please scroll to the bottom, and under the bottom entry paste this:

> # Google software repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

now in the command use 

```
sudo apt-get update
```

Now apt-get at will my friend

---

### Post by hyper_ch on 2009-03-15
or you can use the generator in my sig and follow instructions there

---


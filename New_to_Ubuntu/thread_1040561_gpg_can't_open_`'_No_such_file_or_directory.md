---
title: "gpg: can't open `': No such file or directory"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Santooka on 2009-01-15
Dear all,

2 weeks ago i've got the ubuntu 8.10 intrepid ibex, and i am trying to install, download google programs but i can't.

whenever i write:

```
fadythebassist@fadythebassist-desktop:~$ sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add
gpg: can't open `': No such file or directory
```


i dunno what's wrong or what am i supposed to do , can u ppl help me?

---

### Post by kingmonkey on 2009-01-15
Try 

```
 wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | apt-key add 
```

---

### Post by Santooka on 2009-01-15
the same message:

```
fadythebassist@fadythebassist-desktop:~$  wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | apt-key add
gpg: can't open `': No such file or directory

```

---

### Post by wirelessmonkey on 2009-01-15
wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -



don't forget your sudo ;)

---

### Post by albinootje on 2009-01-15
> **Santooka said:**
> ```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add
gpg: can't open `': No such file or directory
```


Should be :
```

sudo wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -

```
So .. that's with a "-" sign in the end.

See also here :
[http://answers.yahoo.com/question/index?qid=20080713045327AAAmb59](http://answers.yahoo.com/question/index?qid=20080713045327AAAmb59)

---

### Post by Santooka on 2009-01-15
cool!!!
very nice it worked after i added the "-"

thank you very much 

what am i supposed to do now?
after adding the gpg for google

---

### Post by Santooka on 2009-01-15
ok now do u know how to add wine's gpg?

---

### Post by albinootje on 2009-01-15
> **Santooka said:**
> ok now do u know how to add wine's gpg?

You want a newer Wine version ? Instructions here :
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by albinootje on 2009-01-15
> **Santooka said:**
> cool!!!
very nice it worked after i added the "-"

Good :)
> 
what am i supposed to do now?
after adding the gpg for google
Which application were you trying to install ? Or which howto were you following ?

You just only added the public key for signing (by developers/maintainers) software packages.

---

### Post by Santooka on 2009-01-15
google earth for example

but i wanna know how to browse google's products

---

### Post by albinootje on 2009-01-15
> **Santooka said:**
> google earth for example

but i wanna know how to browse google's products

Here's the howto for that :
[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

After adding this to your repositories :
```

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free  

```
You should be able to see the google application in Synaptic Package manager.
And probably also with -> Applications -> add/remove but there you might need to enable the visibility of "all" available packages.

---

### Post by Santooka on 2009-01-15
yeah i got picasa now:)

but i remember that i used to know a command that shows all google application like google earth and stuff like that, any idea what i am talking about?

---

### Post by albinootje on 2009-01-15
> **Santooka said:**
> yeah i got picasa now:)

but i remember that i used to know a command that shows all google application like google earth and stuff like that, any idea what i am talking about?

You mean this perhaps ? See attached screenshot of the add/remove menu item.

---

### Post by Santooka on 2009-01-15
well nope :S

i tried to find google earth or even picasa that i installed but i couldn't find them

so i used synaptic package manager and searched for google and i found lots of stuff and now i am downloading google earth

---

### Post by afkun on 2010-02-27
I was having the same problem, that little hyphen was all it took! Thank you much

---


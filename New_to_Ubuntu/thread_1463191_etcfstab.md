---
title: "/etc/fstab"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by bj218 on 2010-04-26
How can I open & look at what is in  /etc/fstab. Also how would I add something to this?

---

### Post by arrrghhh on 2010-04-26
> **bj218 said:**
> How can I open & look at what is in  /etc/fstab. Also how would I add something to this?

Well I can tell you, but you seem... for lack of a better word, naive.

Do you know what that file does?  Or why you're digging into it?




To get it open, you have to be root.  ```
sudo gedit /etc/fstab
``` Would do it.  But again, this file is very picky and you can easily screw things up in it.  What are you trying to do?

---

### Post by snowpine on 2010-04-26
All your questions are answered here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The short answer is, by using your favorite text editor (gedit, nano, kate, etc.). :)

---

### Post by bj218 on 2010-04-26
I think you have ans. my question? Now I have 2 more ? In sudo gedit /etc/fstab can I
edit or make changes here? How do I get a text editor into terminal? Now why am I so
interested about fstab yesterday a friend took me thru moving my Home Dir. to a new partition. Today I got a little intrested about what we did & how we did it & why we had to use atext editor. I tried to put a text editor into terminal today & was
unsuccessful!! I want to thank both of you for helping me to understand a bit more
about Ubuntu.

---

### Post by P4man on 2010-04-26
> **bj218 said:**
> I think you have ans. my question? Now I have 2 more ? In sudo gedit /etc/fstab can I
edit or make changes here? 

Yes. But please note the correct command is actually 

```
gksudo gedit /etc/fstab
```

gksudo launches a graphical application with root ("administrator" privilidges. In this case the app you are launching is gedit, a text editor. fstab is the configuration file you want to edit, /etc/ is its location. You can also do 

```
gedit /etc/fstab
```

if you just want to look at the file. You wont have permission to save your changes.

> How do I get a text editor into terminal? 

Nano is a non graphical editor. 

```
nano /etc/fstab
```

or as root

```
sudo nano /etc/fstab
```

(note that sudo is like gksudo, but for terminal applications).

To quit nano,  press control+x. It will ask you to save the changes

---

### Post by arrrghhh on 2010-04-26
Thanks for that explanation.  sudo works the same as gksudo, but gives you a graphical password prompt.

P4man, why would you consider my command "incorrect"?  It functionally works, is it because you're running a graphical program, so you should authenticate graphically?  To me they both achieve the same goal, without the annoying GUI password prompt (I don't like how it takes over the whole screen, dimming everything behind it...)

---

### Post by zekopeko on 2010-04-26
> **arrrghhh said:**
> Thanks for that explanation.  sudo works the same as gksudo, but gives you a graphical password prompt.

P4man, why would you consider my command "incorrect"?  It functionally works, is it because you're running a graphical program, so you should authenticate graphically?  To me they both achieve the same goal, without the annoying GUI password prompt (I don't like how it takes over the whole screen, dimming everything behind it...)

This is way using sudo on GUI apps is a bad idea: [https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by ajgreeny on 2010-04-26
Sudo used for a graphical application can, but usually doesn't, cause a big problem and stop you logging in next time.

For more info see
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by arrrghhh on 2010-04-26
Good to know, thanks!!

---

### Post by P4man on 2010-04-27
> **arrrghhh said:**
> Thanks for that explanation.  sudo works the same as gksudo, but gives you a graphical password prompt.

P4man, why would you consider my command "incorrect"?  It functionally works, is it because you're running a graphical program, so you should authenticate graphically?  To me they both achieve the same goal, without the annoying GUI password prompt (I don't like how it takes over the whole screen, dimming everything behind it...)

There is more to it than meets the eye. see the posts above with their links.

---


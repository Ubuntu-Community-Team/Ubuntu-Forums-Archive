---
title: "Security Issue's"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by L.J on 2009-05-22
Hey all,
             I am a relative newbie when it comes to Linux as i have had it for 3 days now, I have come to terms with most of the main uses and moving around the GUI, i found while i was using terminal in certain ways or authorising administrative actions it asks me for the root password or somekind of admin password, this is already becoming annoying and i am sure there is a way of changing the security settings so that it remember's the password for a set time etc..., i am sure i have seen and accessed this feature but i am unable to find it again, does anybody know where and how i can find it ?? All help is appreciated.

Thank in advance.

---

### Post by spiderbatdad on 2009-05-22
You can add a default timeout for password requests to the sudoers file, in the form:```
Defaults passwd_timeout=20
```Editing the sudoers file can be tricky if you are new to linux. The default editor is vim. You might need a brief tutorial on using vim, or you can change the default text editor with command ```
sudo update-alternatives --config editor
```Then choose 3 to select nano...a simpler editor with on screen instructions for saving and exiting.

---

### Post by albinootje on 2009-05-22
> **L.J said:**
> 
             I am a relative newbie when it comes to Linux as i have had it for 3 days now, 

Welcome to Ubuntu! :)
> 
I have come to terms with most of the main uses and moving around the GUI, i found while i was using terminal in certain ways or authorising administrative actions it asks me for the root password or somekind of admin password

For the record, after a default Ubuntu installation, it is asking you for your own username password.
Ubuntu has been customized to be working with sudo. Setting a root password is not recommended.

See here for more information :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And I think the sudo time out only works when you stay in the same terminal, the moment you start using Synaptic Package Manager or Gdebi, then it will probably ask you again, even though you just used sudo in the terminal already.

---

### Post by L.J on 2009-05-23
Thanks Guys,
So i am wrong in saying there is an easy way to do that as i don't want to go to deep into linux as i might mess up haha, If only the password root is able to have a time out then maybe i saw a session time out or something of the same kind :? then again my eyes could have been deceiving me :lolflag: ... thanks

---

### Post by 3rdalbum on 2009-05-23
1. As you get everything in your Linux system the way you want it, you'll very rarely switch to root; so it will be rare that you'll get asked your password.

2. Sudo already has a timeout of 15 minutes; I think this is the same with gksudo (the graphical password prompt).

---

### Post by L.J on 2009-05-23
ok thanks alot, that has cleared it all up for me :)

---

### Post by alphacrucis2 on 2009-05-23
> **L.J said:**
> ok thanks alot, that has cleared it all up for me :)

Another thing you can do in a terminal session is:

```
sudo -i
```

It will ask for your password and your command prompt will then have root privileges until you type exit. Quite useful if you need to do a series of tasks in a terminal as the system administrator. As someone else said this should be rare.

---

### Post by L.J on 2009-06-08
haha thats a handy trick, ill be using that now its better than what i wanted i reackon.

cheers :D

---


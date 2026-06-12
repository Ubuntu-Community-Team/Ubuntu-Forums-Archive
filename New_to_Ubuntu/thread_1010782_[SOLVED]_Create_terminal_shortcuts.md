---
title: "[SOLVED] Create terminal shortcuts"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-14
For example, could I have a hotkey (ctrl+alt+h) to do 'sudo apt-get update', or maybe a keyword such as 'up'?

If so, how?

---

### Post by roelpeeters on 2008-12-14
> **adobrakic said:**
> For example, could I have a hotkey (ctrl+alt+h) to do 'sudo apt-get update', or maybe a keyword such as 'up'?

If so, how?
In bash (the shell running in your terminal) you can create so-called aliases which create shortcuts to long commands. For instance in your example you could make an alias for 'up'
```

alias up="sudo apt-get update"

```

Then in the terminal you just type 'up'.

You need the double quotes to make sure the bash interpreter sees the command as a single command instead of separate words.
To make aliases permanent you can include them in .bashrc a file you find in your home directory.

Hope this helps,
Roel.

---

### Post by kerry_s on 2008-12-14
you can use aliases in your ".bashrc" or ".bash_aliases"

i use .bashrc cause i only have a couple so i don't have a need for a separate file.

---

### Post by Primefalcon on 2008-12-14
A couple of useful ones if your doing web dev are

```
alias apachestart="sudo /etc/init.d/apache2 start"
alias apachestop="sudo /etc/init.d/apache2 stop"
alias apacherestart="sudo /etc/init.d/apache2 restart"
```

the idea is basically to save a lot of typing

---

### Post by Pjotrovitz on 2008-12-14
Well, if you want it to do it by hotkey from the gui, you should look into the "run command" interface in Compiz. You can find it in the general tab in CompizConfigSettings. There, you could make one of the commands to read " gksudo apt-get update && gksudo apt-get upgrade" (The gksudo is there to let you type your password in a gui window).

---

### Post by adobrakic on 2008-12-14
I don't have a .bashrc in my home folder, should i create one?
All I have is bash_history and bash_logout.

---

### Post by kerry_s on 2008-12-14
> **adobrakic said:**
> I don't have a .bashrc in my home folder, should i create one?
All I have is bash_history and bash_logout.

you can copy the 1 from /etc/skel/.bashrc which is the 1 you should have had.

**cp /etc/skel/.bashrc ~/.bashrc**

---

### Post by adobrakic on 2008-12-14
I get:

```

ado@ado-desktop ~ $ cp /etc/skel/.bashrc ~/.bashrc
cp: cannot stat `/etc/skel/.bashrc': No such file or directory
ado@ado-desktop ~ $ 

```

And I manually went into /etc/skel and all I have is:

- .bash_logout
- .profile

---

### Post by theozzlives on 2008-12-14
> **adobrakic said:**
> I don't have a .bashrc in my home folder, should i create one?
All I have is bash_history and bash_logout.

The "." means it's hidden just  type:
```
gedit ~/.bashrc
```

---

### Post by kerry_s on 2008-12-14
strange, i'll attach mine for you.
it's the original from my /etc/skel unmodified.
rename it to .bashrc and you should be good to go.

---

### Post by adobrakic on 2008-12-14
Worked perfectly, thanks!

---

### Post by tommygunner on 2008-12-20
Here is what I've added to both my /home/<user>/.bashrc and to my /root/.bashrc files:

alias update='sudo apt-get update'
alias install='sudo apt-get install'
alias dist-upgrade='sudo apt-get dist-upgrade'
alias upgrade='sudo apt-get upgrade'
alias autoremove='sudo apt-get autoremove'
alias clean='sudo apt-get clean'
alias autoclean='sudo apt-get autoclean'
alias check='sudo apt-get check'
alias remove='sudo apt-get remove'
alias search='apt-cache search'

This computer is a home system, so I don't have any apache or mysql aliases listed.

---


---
title: "Need help....someone help lol."
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Light Knight on 2009-06-29
I'm trying to remove nvidia-glx-new

apt-get remove nvidia-glx-new
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I'm guessing I need to be in root or what ever that is.  I'm brand new to ubuntu....

Anyway the reason I'm trying remove nvidia-glx-new is because I am trying to manually install the drivers from Nvidia for my 9600gt.

I am running Hardy.

---

### Post by halitech on 2009-06-29
you need to use sudo if you are doing it from the terminal

---

### Post by studiodude on 2009-06-29
What the post above means is that to execute that command in the terminal window as root you need to type  ```
sudo apt-get remove nvidia-glx-new
```

sudo stands for I think "**s**uper **u**ser **do**"

---

### Post by prvteprts on 2009-06-29
To add on to the previous posts, sudo is useful because it gives you super user privileges for around 15 minutes, eliminating the need for you to enter your password everytime you need the privileges. Correct me if I am wrong, but gksudo does pretty much the same thing, except it prompts you with a dialog box instead of a command line input prompt. I think it's useful in programming for launching things that need super user privileges without scaring the user by popping up a terminal window heh heh. Like in C you could have:

```
 system("gksudo"); 
```

Apologies if I got carried away :D.

---

### Post by Mornedhel on 2009-06-29
> **prvteprts said:**
> To add on to the previous posts, sudo is useful because it gives you super user privileges for around 15 minutes, eliminating the need for you to enter your password everytime you need the privileges. Correct me if I am wrong, but gksudo does pretty much the same thing, except it prompts you with a dialog box instead of a command line input prompt. I think it's useful in programming for launching things that need super user privileges without scaring the user by popping up a terminal window heh heh. Like in C you could have:

```
 system("gksudo"); 
```

Apologies if I got carried away :D.

It's mostly useful for not having to launch an xterm everytime you want to run something with administrator rights.

---

### Post by jimv on 2009-06-29
Notice:  Sudo is not a replacement for assertiveness and will not work in real-life situations.  "Sudo make me a sandwich" will not get you a sandwich, it will only get you strange looks.

---

### Post by Light Knight on 2009-06-29
Thank you for the very quick replies. The sudo thing solved my issue. :)

---

### Post by decoherence on 2009-06-29
> **jimv said:**
> Notice:  Sudo is not a replacement for assertiveness and will not work in real-life situations.  "Sudo make me a sandwich" will not get you a sandwich, it will only get you strange looks.

Nooo!!! XKCD does not lie!!!!

or should that be

sudo XKCD does not lie!!!!

hmmm... command not found.... ok you might be right, then...

---

### Post by philcamlin on 2009-06-29
> **decoherence said:**
> Nooo!!! XKCD does not lie!!!!

or should that be

sudo XKCD does not lie!!!!

hmmm... command not found.... ok you might be right, then...

what :P

and thats great that its fixed :)

---


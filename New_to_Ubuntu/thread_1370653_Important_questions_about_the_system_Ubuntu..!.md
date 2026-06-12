---
title: "Important questions about the system Ubuntu..!"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by 0863588 on 2010-01-02
[SIZE=2]**First:** [/SIZE][SIZE=2]How to Adjust the Settings screen??

[/SIZE]  [SIZE=2]**Second:** [/SIZE][SIZE=2]How to Make Your Windows is the operating system. [/SIZE][SIZE=2]When the computer starts automatically be entered into ubuntu after less than 8 seconds..??how can chang ..?[/SIZE]

---

### Post by sandyd on 2010-01-02
> **0863588 said:**
> **[SIZE=4]First:[/SIZE]** [SIZE=4]How to Adjust the Settings screen??[/SIZE]

[SIZE=4]**Second:**[/SIZE] [SIZE=4]How to Make Your Windows is the operating system. [/SIZE][SIZE=4]When the computer starts automatically be entered into ubuntu after less than 8 seconds..??how can chang ..?[/SIZE]
2. ```

gksudo gedit /etc/default/grub

``````

GRUB_TIMEOUT #Controls the time until the OS is started

```

---

### Post by 0863588 on 2010-01-02
> **carlee said:**
> 2. ```

gksudo gedit /etc/default/grub

``````

GRUB_TIMEOUT #Controls the time until the OS is started

```
 
 
[SIZE=2]**"THANK YOU"**
[/SIZE] [SIZE=2]Can I use something other than the code .... Any other way?? Because I am a new user :oops:[/SIZE]

---

### Post by Methuselah on 2010-01-02
> **0863588 said:**
> [SIZE=5][/SIZE] 
[SIZE=5]**"THANK YOU"**[/SIZE]
[SIZE=4]Can I use something other than the code .... Any other way?? Because I am a new user :oops:[/SIZE]

It's not too hard.
After you execute the first command in the Terminal you'll see a text editor.
Then you can change the GRUB_TIMEOUT option and save the file.

---

### Post by 0863588 on 2010-01-03
> **Methuselah said:**
> It's not too hard.
After you execute the first command in the Terminal you'll see a text editor.
Then you can change the GRUB_TIMEOUT option and save the file.
 [SIZE=2]Thank u ..:)[/SIZE]

---

### Post by ubername on 2010-01-03
After you have saved the file you need to run

```
sudo update-grub
```

---

### Post by 0863588 on 2010-01-08
> **ubername said:**
> After you have saved the file you need to run
 
```
sudo update-grub
```
 [SIZE=2]Thank you. But What is this code??[/SIZE]

---

### Post by jlhaslip on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

read that link and download the book

---

### Post by 0863588 on 2010-01-09
> **jlhaslip said:**
> [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
 
read that link and download the book
 [SIZE=3]thank you ..... [/SIZE]

---

### Post by corncob on 2010-01-09
Did it work?  You are using Karmic (9.10)? Grub was different before that.

---

### Post by Bartender on 2010-01-09
Jeez, guys, give him a break.  He doesn't want to use the terminal.

Assuming you can get online, start up Synaptic, go to Search, type in "startup manager".  I attached a screenshot.  The one you want to get is the second file of the three that will come up.  Download that, then you'll find the application in 'System>Administration'.  The rest is really easy - you just start the app, and pick which OS you want to be the default.  You'll still get the GRUB screen when the PC is starting up, it's just that whichever OS you picked will be marked as the default one to start.

---


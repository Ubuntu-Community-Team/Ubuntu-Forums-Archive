---
title: "Synaptic issue."
date: 2010-03-09
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-03-09
Hello again.

This time I'm her on behalf of my father. He installed Ubuntu netbook-remix (Christian Edition) a while ago. It worked just fine until a while ago. Now he cannot access synaptic, update manager or use the command  ```
sudo apt-get update && sudo apt-get upgrade
```

They all result in the following error message. How can we fix this.

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to
correct the problem.
E: _cache->open() failed, please report.
```


I would be thankful if you cold kindly keep the responses as simple (non-technical) as possible.

---

### Post by audiomick on 2010-03-09
Have you tried the command that the error message suggests? That is this
   
 ```
    E: dpkg was interrupted, you must manually run '[COLOR=Red]**sudo dpkg --configure -a**[/COLOR]' to
correct the problem.
E: _cache->open() failed, please report.
```That means open a terminal
applications> accessories> terminal

type into the terminal
```
sudo dpkg --configure -a
```you will be asked for a password. That is the one used to log on with. You will not see what you are typing when you type the password at the prompt.
<Enter>, and let it finish.

---

### Post by lockalidiot on 2010-03-09
No, we haven't because I have no idea what the code does. Or what should I do after that.

Thank you for the input. we'll give it a shot.

---

### Post by audiomick on 2010-03-09
> **lockalidiot said:**
> No, we haven't because [COLOR=Red]I have no idea what the code does[/COLOR]. Or what should I do after that.

Thank you for the input. we'll give it a shot.
According to the man pages, which you can access with
```
man dpkg
```
in a terminal
it configures packages that have been de-compressed but not configured. It is safe, anyway.

---

### Post by lockalidiot on 2010-03-09
Thanks for your answers. The code worked well. SOLVED.

---


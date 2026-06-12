---
title: "How to allow execution of programs from terminal"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by cyberjar09 on 2011-07-21
I know this problem has a simple solution but I have no idea how to go about it. 

I want to be able to run software like my eclipse IDE directly from the terminal by just typing "eclipse" from any folder I am in. 

I understand I have to make some changes in the ~/.bashrc file but I dont know what text to add to it. 

my eclipse is installed in the folder ~/development/java/


Thanks in advance.

---

### Post by nothingspecial on 2011-07-21
Put this at the end of your .bashrc

```
PATH=$PATH:$HOME/development/java
```

Then type ```
. ~/.bashrc
```

---

### Post by cyberjar09 on 2011-07-21
> **nothingspecial said:**
> Put this at the end of your .bashrc

```
PATH=$PATH:$HOME/development/java
```

Then type ```
. ~/.bashrc
```

Great! I got it going .. added play to the path too ! 

```
export PLAY_HOME=/home/rudy/development/java/play
export ECLIPSE_HOME=/home/rudy/development/java/eclipse/
export PATH=$PATH:$PLAY_HOME:$ECLIPSE_HOME
```

Thank you very much! =D 

thread marked solved.

---

### Post by cyberjar09 on 2011-07-21
One related question though:

Is it the normal behavior of the terminal to not give me prompt when I run eclipse ? 

Is there a workaround? (just asking out of curiosity, I know I can use Ctrl+Shift+T)

---


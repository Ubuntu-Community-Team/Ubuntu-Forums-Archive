---
title: "bash error: command not found"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by dwlamb on 2011-03-18
Good day all,

I've googled this error.  While there are many results for the topic, none of the situations addresses what I am experiencing.

I've started a tutorial on bash scripting found [here]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html").  I tried the typical:

```
#!/bin/bash          
echo Hello World
```saved to the file test.sh.  But when I go to run it ```
sudo ./test.sh
``` I receive the error:```
sudo: ./test.sh: command not found
```Using which and whereis, the response points to /bin/bash.  whereis also yields /etc/bash.bashrc and /usr/share/man/man1/bash.1.gz but I am discounting those as not being the executable binary I need to execute a script.

I'm using gedit and have looked at the script in nano.  No differences.  I've also rewritten it in nano without a different result.  The script is saved to my root folder and the prompt is in that directory.

I'm running Koala.  Thanks for taking the time to read this,

dw

---

### Post by andrewthomas on 2011-03-18
1: don't run that with sudo, not necessary

2: You need to make the script executable

```
chmod +x test.sh
```or

```
/bin/bash ./test.sh
```

---

### Post by papibe on 2011-03-18
> **dwlamb said:**
> 
```
sudo ./test.sh
```

I would advice you NOT to sudo your learning scripts, in case you made a mistake, you would make it worse.

> **dwlamb said:**
> 
```
sudo: ./test.sh: command not found
```

This error means that the file "test.sh" is not in the directory you're positioned while executed the command. You have to see it when you do a "ls". Dot forget to chmod the file as andrewthomas suggested.

Regards.

---

### Post by dwlamb on 2011-03-18
Thanks!  That fixed it.

---

### Post by dwlamb on 2011-03-18
> **papibe said:**
> I would advice you NOT to sudo your learning  scripts, in case you made a mistake, you would make it worse.


This error means that the file "test.sh" is not in the directory you're  positioned while executed the command. You have to see it when you do a  "ls". Dot forget to chmod the file as andrewthomas suggested.

Regards.


andrewthomas was correct.  If you read my post closely, the command  prompt was in the directory where the script was located.  I checked  that when I was troubleshooting.

Changing the file to 744 solved the problem

---


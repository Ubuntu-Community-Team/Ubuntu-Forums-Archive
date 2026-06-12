---
title: "What to learn bash"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by kranthi457 on 2011-07-23
hi everybody ,

i am new to linux ,and also new to programming ,i want to learn bash scripting ,when i check on my system it shows bash is installed ,but i am not sure how to bring it up in terminal window .

Also could you please suggest some good books i can follow to learn this scripting please ..


I have installed Ubuntu 11.04 version on my system,with unity enabled ..

Thanks in Advance ...

---

### Post by sectshun8 on 2011-07-23
That "bash" that is installed... I'm pretty sure it's just like a information file, basically a thing that allows bash to run on the machine.  It's not like you can open it and learn scripting.

Anyhow, I suggest the way I've recently written and adjusted some scripts.  Think of an easy task on your machine.  Then do an online search for a script that does that task, or something similar.  There are tons of forums and loads of information out there giving example scripts and advice... including this one.

---

### Post by mcduck on 2011-07-23
> **kranthi457 said:**
> hi everybody ,

i am new to linux ,and also new to programming ,i want to learn bash scripting ,when i check on my system it shows bash is installed ,but i am not sure how to bring it up in terminal window .

Also could you please suggest some good books i can follow to learn this scripting please ..


I have installed Ubuntu 11.04 version on my system,with unity enabled ..

Thanks in Advance ...

The very second you open a terminal window, you see Bash. That's the default shell used for normal users. You don't need to do anything to bring it up. :)

---

### Post by doas777 on 2011-07-23
> **kranthi457 said:**
> hi everybody ,

i am new to linux ,and also new to programming ,i want to learn bash scripting ,when i check on my system it shows bash is installed ,but i am not sure how to bring it up in terminal window .

Also could you please suggest some good books i can follow to learn this scripting please ..


I have installed Ubuntu 11.04 version on my system,with unity enabled ..

Thanks in Advance ...

think of it as Bash IS your terminal. in this case though, you are probably using dash (ubuntu recently changed teh default).
for the most part, scripting for dash, bash, ksh, etc is no differant, so most people call it shell scripting rather than  bash/dash/ksh scripting.

shell scritps are a lot like windows batch files or windows powershell scripts. they are essentially a list of commands to be executed in order.

bash supports all the common flow control mechanisms like storing and retrieving variables, decisions, loops, etc.

to write a bash script, just create a text file, and put this at the top:
```
#!/bin/bash
```

then try adding some commands. 

to run your script, you must make it executable:
```
sudo chmod u+x /path/to/file
```

then to execute your file you just call it by name:
```
/path/to/script/file
```

if you are executing a script that is stored in your terminals working directory, you must put ./ in front of the filename
```

cd /path/to/scripts/directory/
./scriptname.sh

```

---

### Post by mcduck on 2011-07-23
> **doas777 said:**
> think of it as Bash IS your terminal. in this case though, you are probably using dash (ubuntu recently changed teh default).
Nope, he's using Bash. :)

Dash is the default system shell, while Bash is still the default shell for users.

---

### Post by nothingspecial on 2011-07-23
> **doas777 said:**
> think of it as Bash IS your terminal. in this case though, you are probably using dash (ubuntu recently changed teh default).



Nope, it's still bash

```
echo $0
bash
```

Have a look at this guide, it's the best I've ever seen

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by androssofer on 2011-07-23
tutorials for making bash scripts:

[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

---


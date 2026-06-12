---
title: "[SOLVED] give script executable permission"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by mdewet on 2008-12-21
hi

I'm quite new to hardy, and i'm trying out to write my own scripts.  I've read the bash scripting tutorial at [https://help.ubuntu.com/community/Beginners/BashScripting]("https://help.ubuntu.com/community/Beginners/BashScripting"), but I still cant run the script.

```
muerte@muerte:~$ /home/muerte/scripts/toets.sh
bash: /home/muerte/scripts/toets.sh: Permission denied
```

I have done both 
```
 sudo chmod a+x /home/muerte/scripts
```

and

 ```
sudo chmod 700 /home/muerte/scripts
```

as prescribed by the tutorial to give the appropriate permissions, but it still gives me the permission denied error.

---

### Post by shredder12 on 2008-12-21
well try running.. 
```
sh script.sh
```
or 
```
./script.sh
```

---

### Post by arckeda on 2008-12-21
Your only giving the directory executable permissions.  Make sure you put in the full path name of the script of something like:

```
sudo chmod a+x /directory/directory/*
```

---

### Post by albinootje on 2008-12-21
> **mdewet said:**
> 
I'm quite new to hardy, and i'm trying out to write my own scripts.  I've read the bash scripting tutorial at [https://help.ubuntu.com/community/Beginners/BashScripting]("https://help.ubuntu.com/community/Beginners/BashScripting"), but I still cant run the script.


You should try :
```

chmod +x /home/muerte/scripts/toets.sh

```
and then :
```

./home/muerte/scripts/toets.sh

```

---

### Post by mdewet on 2008-12-21
thanks for all the replies, I tried everything, still no luck..

> **albinootje said:**
> You should try :
```

chmod +x /home/muerte/scripts/toets.sh

```
and then :
```

./home/muerte/scripts/toets.sh

```

after executing this I got this
```
muerte@muerte:~$ sudo chmod +x /home/muerte/scripts/toets.sh
muerte@muerte:~$ ./home/muerte/scripts/toets.sh
bash: ./home/muerte/scripts/toets.sh: No such file or directory

```

when I try to open /home/muerte/scripts in the file manager it refuses access to the folder, and when I opened the folder with nautilus the file is there

why do I all of the sudden get the no such file error?

---

### Post by albinootje on 2008-12-21
> **mdewet said:**
> 
when I try to open /home/muerte/scripts in the file manager it refuses access to the folder, and when I opened the folder with nautilus the file is there

why do I all of the sudden get the no such file error?

What do you mean with "the file manager" ?
In Ubuntu the default file manager is Nautilus.

It could be possible that "bash" does respond like that because of the content of your script.
And do you have a separate /home partition with noexec mount options ?
Probably not, but just wondering.

Can you copy your toets.sh to /tmp/ and then run :
```
sh /tmp/toets.sh
```

---

### Post by Dedoimedo on 2008-12-21
Please enter the directory where the script is.

First, make sure you OWN it:

```

sudo chown your-user:you-user script-file

```

Example:
```

sudo chown roger:roger script.sh

```

Next, chmod it:

```

chmod +x script.sh

```

This is enough, as you own the script ...

Run it:

```

./script.sh

```

Dedoimedo

---

### Post by mdewet on 2008-12-21
yes, that worked!..

I meant I couldn't view the contents of the folder when I tried Places > Home folder..I had to open nautilus from the terminal with 
```
gksudo nautilus
``` 

thanks for the help! I will save all my future scripts in the /tmp folder

---

### Post by mdewet on 2008-12-21
> **Dedoimedo said:**
> Please enter the directory where the script is.

First, make sure you OWN it:

```

sudo chown your-user:you-user script-file

```

Example:
```

sudo chown roger:roger script.sh

```

Next, chmod it:

```

chmod +x script.sh

```

This is enough, as you own the script ...

Run it:

```

./script.sh

```

Dedoimedo

This also works great!

Thanks for the help!

---

### Post by albinootje on 2008-12-21
> **mdewet said:**
> yes, that worked!..

cool :)
> 
thanks for the help! I will save all my future scripts in the /tmp folder
If you want to save your scripts permanently, then /tmp is a bad idea because after each reboot it will be wiped.
(/tmp can sometime be handy to quickly test things, because it has 1777 permissions, and is used for temporary files by several programs anyway.)

---


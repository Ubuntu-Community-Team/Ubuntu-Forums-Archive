---
title: "How to add a new command"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by kushvarma on 2010-12-31
need a help... 

if i want to make a command like:

$ abc 

and it runs something...  how to do that..

for example

$ls shows files n folder in director, i want to make a command which directly runs...

$abc.... 

Please some one help me...

---

### Post by Red Raven on 2010-12-31
> **kushvarma said:**
> need a help... 

if i want to make a command like:

$ abc 

and it runs something...  how to do that..

for example

$ls shows files n folder in director, i want to make a command which directly runs...

$abc.... 

Please some one help me...
  does this help? [http://en.kioskea.net/faq/2540-linux-create-your-own-command](http://en.kioskea.net/faq/2540-linux-create-your-own-command)

---

### Post by Crusty Old Fart on 2010-12-31
An easy way to do this is to add custom functions at the bottom your ~/.bashrc file.

```

function sheeplover()
{
  echo Montana: Where men are men and sheep are scared.
}

```If you do that, whenever you're in a shell and you issue the following command:
```

sheeplover

```You'll learn about Montana.

_Note:_ You'll need to open a new shell after editing your ~/.bashrc file for the system to load your changes.

---

### Post by Paqman on 2010-12-31
You can also use alias to set up custom commands. For more info:
```
man alias
```

---

### Post by cyb3r_sn4k3 on 2010-12-31
What I do is make a new text document and start it with #!/bin/bash then I write all the functions then use chmod a+x on the document for eg. I want to make a command or script called storage which mounts a partition say sdb3. So the script goes like this...


#!/bin/bash
sudo mount /dev/sdb3/ /media/Storage/

Hope it helped :)

---

### Post by hakermania on 2010-12-31
Nonono listen, the simplest way is to do the following:
1) Write your script and make it executable (chmod +x script_name)
2) Give ```
sudo cp script_name /usr/bin/
```
3) You are ready, now, whenever you give 'script_name' in the terminal your script will run. :)

---

### Post by QLee on 2010-12-31
As well as hakermania's advice which is correct for scripts available to all users, it is often recommended to create a /bin in your home folder for your personal scripts. It will be in only your path by default.

---

### Post by kevdog on 2011-01-01
And just to chime in

/usr/bin is usually reserved for kernel binaries (meaning this is the convention

/usr/local/bin is for locally compiled binaries and such

and 
~/bin is for user scripts, binaries only available to the user.  Make sure that ~/bin or $HOME/bin is in your path however.

---

### Post by QLee on 2011-01-01
[QUOTE=kevdog]...  Make sure that ~/bin or $HOME/bin is in your path however.[/QUOTE]

In a default Ubuntu install ~/bin is in the user's path.


[Edit] I might as well add, it is first in the path so it is searched first.

---


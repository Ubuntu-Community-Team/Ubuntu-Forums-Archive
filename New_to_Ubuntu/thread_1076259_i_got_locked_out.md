---
title: "i got locked out"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by drjackal on 2009-02-21
while changing permissions to my folders i think i locked myself out.. in the sense i can no longer use sudo. earlier i got the message "sudo: must be setuid root". please help.

---

### Post by Doug11 on 2009-02-21
> **drjackal said:**
> while changing permissions to my folders i think i locked myself out.. in the sense i can no longer use sudo. earlier i got the message "sudo: must be setuid root". please help.
You locked yourself out of your folder or system?

---

### Post by drjackal on 2009-02-21
okay...i did ot get locked out of my own system..(how could i be writing this now??) but i did lose a few things as in...i cannot get permissions like installing amarok and stuff !!   

this thingy comes "sudo: must be setuid root"!!! what the heck is it supposed to mean?

---

### Post by drjackal on 2009-02-21
also, on opening user settings i cannot access root! and neither can i change my permissions!!

---

### Post by lukjad on 2009-02-21
If this a folder/file issue, go to the Terminal (Applications->Accessories->Termina) and paste this command:

```
sudo chown lukjad007 myfile
```

Be sure to replace "lukjad007" with your own login name and "myfile" with the actual file name.

EDIT: Before you run this command, could you tell us just a bit more about what happened? It would help to know so that we can give you better advice. Were you trying a command out in the terminal? If so, could you paste it here? (To view the history of commands typed hit the up arrow while in the terminal.)

---

### Post by drjackal on 2009-02-21
same  thing again.. "sudo: must be setuid root"!!! 

and guess what i cannot browse my e drive i had left over from windows now!!

---

### Post by lukjad on 2009-02-21
Can you tell us what you were doing when the permissions were messed up? (See edit in previous post.)

---

### Post by drjackal on 2009-02-21
tried to use the recovery console and then change permissions but that did not seem to work..

---

### Post by lukjad on 2009-02-21
Is this a personal folder? One that you created? Or is it a system file? What's it called?

---

### Post by mister_pink on 2009-02-21
You need to do exactly what it says - set uuid for sudo.
Go to recovery mode and type the following.
```

chmod 4755 /usr/bin/sudo

```
then type exit and select to reboot. This should solve that error, there might be others if you've changed permissions on system folders though. Lesson here is don't do that!

---

### Post by Elfy on 2009-02-21
What was it that you did before you needed the recovery console.

Also can you paste the result of these

```
ls -al /usr/bin/sudo
ls -al /etc/sudoers
```

Run this and paste it here too please - it will should give us the commands you have run from the terminal

```
cat .bash_history |grep sudo
```

---

### Post by drjackal on 2009-02-21
thank you all so much for helping me! i finally solved my puzzling thingy . the sudo problem is solved! it seems i had to log on as root using sudo -i and then gone on!!

but another thing. i seem to see that almost all the stuff from adobe are for intel proscessors. what can i do to browse youtube videos?

@forest pixie: what will the first two commands do? i see that the last command will get back my history of all commands.

---

### Post by drjackal on 2009-02-21
the results of the second box' commands are:

chown root:root /usr/bin/sudo
chown 4755 /usr/bin/sudo
chmod 4111 /usr/bin/sudo
chmod 0440 /etc/sudoers
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

---

### Post by drjackal on 2009-02-21
also i need some pdf reader.

---

### Post by lukjad on 2009-02-21
@drjackal  
There is a PDF reader preinstalled in as far as I know all versions of Ubuntu

---

### Post by drjackal on 2009-02-21
sorry..but it seems it is not working properly...

---

### Post by Elfy on 2009-02-21
> @forest pixie: what will the first two commands do? If you are not sure it is good to ask :) If you want a quick answer it is good to use the manuals - you can access them in a terminal with 'man'

So ```
man ls
```woudl tell you that the command would list directory contents - the -al are options

a - do not ignore entries starting with .
l - use a long listing format

I wanted to see what permissions you had on those 2 files.

The default pdf reader should work - try running from a terminal to see if there are errors ```
evince
```

If you start getting odd errors it might be worth posting the result of the first cat command I gave earlier.

---

### Post by drjackal on 2009-02-22
thank u pixie! i can now finally view my pdf files. thank u all!


until my next problem comes along!

---


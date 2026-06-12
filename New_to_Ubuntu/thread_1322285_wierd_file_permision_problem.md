---
title: "wierd file permision problem"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by ronald74437 on 2009-11-10
Hey there. I am very new to ubuntu and linux as a whole. i have had mostly success in learning the ins and outs as i go. i am however having a problem with the file permissions on the file that contains my world of warcraft. i have gone into the file properties and changed the permissions for the files. i even went with the gksudo nautilus command after hitting F2 to change the permissions to read all/write all and anything else that seemed to lock the file. the changes arent staying put, and the file is reverting back to locked and what not. 

thank you for any help you can provide. if you need more information about my problem, ask away

thanks guys :D

---

### Post by doas777 on 2009-11-10
ok, by "lock" what do you mean? that you see a padlock on the file icon, or are you getting a message that file x is "locked"? they both have completely differant causes so, is an important distinction.

most likely you are not the owner of the files. 
open a  terminal (applications-accessories-terminal)
and navigate to teh directory in question with the cd command (let me knwo if you need advice on that.) once there, paste in this:
```
ls -al
``` and post back the results. that will tell us teh current permissions, and the owner.

a word of caution. most applications do not like it when you modify their default permissions. in linux, you should have permissions on almost nothing except the stuff within your /home/<username> directory. that is by design, and once you get used to it, it isn't terribly inconvenient.

---

### Post by ronald74437 on 2009-11-10
drwxr-xr-x  4 john john  4096 2009-11-10 18:49 .wine


this?
 or all the results?

also there is an x icon as well as a padlock icon on the folder

---

### Post by doas777 on 2009-11-10
> **ronald74437 said:**
> drwxr-xr-x  4 john john  4096 2009-11-10 18:49 .wine


this?
 or all the results?

also there is an x icon as well as a padlock icon on the folder

if that is the object that you changed permissions on, then yes.

that folder gives the user 'john' full control (read write/delete and execute). are you logged in as john?

changing  afolders permissions does not automatically change the permissions on teh files within it. what permissions did you change? just that dir?  btw, why did you need to change them. does the game not run?

---

### Post by ronald74437 on 2009-11-10
i would go to run the game and it would say i couldnt access the contents of the file and it would then say which file it was.

i am logged in as john

i changed the permissions of the folder "world of warcraft" to be read/write and to allow myself to create and delete. after that i could access the contents, but upon rebooting the permissions would be reset. 

also after i went and changed the permissions of the file i hit the apply permissions to enclosed files button as well

---

### Post by doas777 on 2009-11-10
I hope that wine will run alright with the permissions reset, but worst comes to worst, you can reinstall it. in general I only touch permissions on content files,  or things that i put somewhere myself. 

lets try this. go back to your terminal and give yourself ownership and 777 on all sub objects. 

this is a nuclear kind of option. **please don't try this unless if you feel uncomfortable about it**. 
```

sudo chown -R john:john ~/.wine
sudo chmod -R 777 ~/.wine

```

---

### Post by ronald74437 on 2009-11-10
> **doas777 said:**
> I hope that wine will run alright with the permissions reset, but worst comes to worst, you can reinstall it. in general I only touch permissions on content files,  or things that i put somewhere myself. 

lets try this. go back to your terminal and give yourself ownership and 777 on all sub objects. 

this is a nuclear kind of option. **please don't try this unless if you feel uncomfortable about it**. 
```

sudo chown -R john:john ~/.wine
sudo chmod -R 777 ~/.wine

```
what does that do?

---

### Post by doas777 on 2009-11-10
> **ronald74437 said:**
> what does that do?

it will take ownership of everything in .wine, and set permissions for everyone to full control.
perhaps I am being overdramatic in my warning. the dangers are precisely this: that wine will no longer have teh correct permissions that it needs to run and thus will fail. you would have to purge it and reinstall it to get it working agian. 

most parts of teh system are not meant to be exclusively owned by the user, so wine might not run. it won;t hurt anything else as long as you use the commands correctly. just make sure you don't forget the path that you are targeting.

**sudo chown -R john:john ~/.wine**

**sudo** runs the command following it as an administrator.
**chown** is "change owner". 
**-R** means chown will "recursively" apply that action to all sub-objects in the target directory.
**john:john** is "user:group" that you want the file to be owned by
**~/.wine** is the target folder you want to change. ~ means your home directory (/home/john presumably). 

so we are setting john as the owner and group of all the objects in ~/.wine

**sudo chmod -R 777 ~/.wine**

 **chmod** is "change mode" (permissions)
**-R** is recursive. see above.
**777** means full control, to all users. read write and delete. google unix permissions for details as to what the numbers signify.
**~/.wine** is the target directory

---

### Post by aPaSv5 on 2009-11-10
Those commands recursively set the file owner to your username and the file permissions to such that you can read and write them.

I prefer the "other" syntax, in which you specify permissions not with numbers (like 777) but with the letters 'u' for user, 'g' for group, and 'o' for other to select a target, then either '+' or '-' to set or remove a permission, then 'r' for read, 'w' for write, and 'x' for execute.

An example:

```

chmod u+x myscript.sh

```

This would allow me to run a script that I wrote, for example.

You can supply multiple arguments at once, e.g.:

```

chmod u+x, og= *.sh

```

would give me permission to execute all shell scripts (all files ending in '.sh') and would remove all permissions from the other users.

Note that permissions for 'user' and 'group' are in regards to the owner and group of that file -- 'chown' and 'chgrp' allow you to change the owner and group, respectively.

I'm not sure if you're aware of man pages (manual pages, that is), but you can read up on all of those commands (and most others) by typing 'man [command name]', where you would substitute '[command name]' for a given command.

It is important to note that many so-called commands are not actually "commands" but programs.

'cd' is an example of a command built-into the bash shell; find is a stand-alone program.

---

### Post by doas777 on 2009-11-10
ok, appearently this is a wow specific issue. check out this thread:
[http://ubuntuforums.org/showthread.php?t=1321762](http://ubuntuforums.org/showthread.php?t=1321762)

so you could run the commands I provided each time before launching (you could make a quick script for your wow launcher), or check out the suggestions there.

---


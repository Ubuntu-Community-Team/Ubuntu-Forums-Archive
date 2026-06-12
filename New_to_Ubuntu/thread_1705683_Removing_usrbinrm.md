---
title: "Removing /usr/bin/rm??"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by thagza911 on 2011-03-12
Hi,

I accidentially deleted a file the other day and read that 'rm' can be redirected to the trash in order to help with recovery. 

I found a script that needed me to replaced /bin/rm with a script that would redirect rm to move the files in the trash... i created a backup of rm to /bin/rm.bak. The script didn't work so I put the script in /usr/bin. That didn;t work either so I reverted back to the original (restored /bin/rm.bak to /bin/rm) and want to get rid of /usr/bin/rm (i.e. have everything back to normal). Now whenever I try to use the rm command I get "Permission denied", even under root.

How can I remove /usr/bin/rm? I tried 'sudo rm /usr/bin/rm' and other variants but none of those worked (permission error). I also tried re-installing the coreutils from synaptic but that didn't work either.

Any suggestions would be great.

Thanks!

Using ubuntu 10.04.

---

### Post by fabricator4 on 2011-03-12
Your script has to be executable.

```

sudo chmod +X rm

```

Don't know why the old rm is not working, except the ownership or permissions have been messed up.  Here's mine:

```

-rwxr-xr-x 1 root root 54928 2010-09-22 04:33 rm

```

Chris

---

### Post by thagza911 on 2011-03-12
I tried the following...

```

$sudo chmod -X rm
chmod: cannot access `rm': No such file or directory

$ sudo chmod -X /usr/bin/rm
$ rm /usr/bin/rm
bash: /usr/bin/rm: Permission denied

-rw-r--r-- 1 root root 54928 2011-03-12 15:56 /usr/bin/rm
-rw-r--r-- 1 root root 54928 2011-03-12 15:00 /bin/rm

```Didn't seem to work..

---

### Post by yeats on 2011-03-12
Okay...

First of all - no need to resort to hack-y scripts for a safeguard against accidental file deletion.  From 'man rm':

> If the -I or --interactive=once option is given,  and  there  are  more than  three  files  or  the  -r,  -R, or --recursive are given, then rm prompts the user for whether to proceed with the entire operation.   If the response is not affirmative, the entire command is aborted.


So you could add:

```
alias rm="rm -I"
```

to ~/.bashrc and that would probably be enough for most users.

As to your permissions issue, you would need to do:

```
sudo chmod +x /bin/rm
```

to get it to work again.

---

### Post by thagza911 on 2011-03-12
> 
Okay...
First of all - no need to resort to hack-y scripts for a safeguard against accidental file deletion.  From 'man rm':


I didnt want the script for accidental deletion. I wanted the script so that all rm calls would put files in the trash where I could delete them. So if I delete something today and want to get it back a week from now, i could just pull it out of the trash.

By the way..

```

$ sudo chmod +x /bin/rm

```

worked for me! :)

Thanks for the help.

---

### Post by jerome1232 on 2011-03-12
There is a cli tool called "trash" that will put files you delete using the command trash in trash.

Just a suggestion

---

### Post by sandyd on 2011-03-12
> **thagza911 said:**
> I didnt want the script for accidental deletion. I wanted the script so that all rm calls would put files in the trash where I could delete them. So if I delete something today and want to get it back a week from now, i could just pull it out of the trash.

By the way..

```

$ sudo chmod +x /bin/rm

```worked for me! :)

Thanks for the help.
```
sudo nano ~/.bashrc
```
Plant this at the end of the file.
```
alias rm="trash"
```.

Just don't use sudo when running rm and youll be fine.

---

### Post by fabricator4 on 2011-03-12
> **thagza911 said:**
> 
```

-rw-r--r-- 1 root root 54928 2011-03-12 15:00 /bin/rm

```

Yes, you lost the execute permission somehow when moving the files around.  "sudo cp" should have kept the permissions as they were, so not sure.

> 
$sudo chmod -X rm
chmod: cannot access `rm': No such file or directory


Sorry, since you were already moving files around and obviously using paths, I assumed you would know to either change to /bin or give the full path.

My bad.

Chris

---

### Post by Hippytaff on 2011-03-12
sorry - deleted..dind't fully read the thread :?

---

### Post by fabricator4 on 2011-03-12
> **Hippytaff said:**
> sorry - deleted..dind't fully read the thread :?

Here, have another bean.  :bean:

:-)

---


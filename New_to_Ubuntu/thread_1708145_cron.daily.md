---
title: "cron.daily"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Nerflander on 2011-03-16
Hey there peeps,

If i would put the automysqlbackup script in the /etc/cron.daily

will it auto do it daily? it seemed that it didt last time i put it in there. Anything i could have missed? i filled out most of the file like DB name / password / user etc.....

i changed the file location now i hope it works but im afraid it aint gonna be working.

Maybe i should chmod the file or folder? 

any advices?

---

### Post by SeijiSensei on 2011-03-16
First, make sure that the script runs from the command prompt.  It will be running with root permissions from /etc/cron.daily, so run your script with "sudo" to test it.

Next, make sure that the [script's file name has no extensions]("http://ubuntuforums.org/showpost.php?p=9918251&postcount=10") (like myscript.sh).  Ubuntu, like Debian, won't run scripts from /etc/cron.* that include an extension.

Finally, I'd leave the script in a directory in root's path, then create a symlink to /etc/cron.daily.  I usually put scripts like yours in /usr/local/sbin, then

```

cd /etc/cron.daily
sudo ln -s /usr/local/sbin/myscript

```

You'll see a link to myscript appear in /etc/cron.daily after that.

---

### Post by Paqman on 2011-03-16
Chmod it so that it's executable. Apart from that, it should just run when you drop it in that folder. Have you tested the script to make sure it runs alright as root when you run it manually?

---

### Post by Nerflander on 2011-03-16
I did what you said senjeisensei , 

i created the symlink etc and before that i removed the .sh extension from it. Now to test it i tried to type in 


```
sudo automysqlbackup
```

but then it just says commmand not found...

more help ?:)

---

### Post by SeijiSensei on 2011-03-16
> **Nerflander said:**
> 
```
sudo automysqlbackup
```

but then it just says commmand not found...


What's the full path to the script?  Try "sudo /path/to/automysqlbackup".  If you're in the directory that contains the script, you must use "sudo ./automysqlbackup" or give the full path.

You can only run scripts without a pathname if you have that path defined in the $PATH environment variable.  Type "echo $PATH" to see what directories are included.  Since the default PATH includes all the logical places the script could be stored in, I'm guessing it's not in /usr/local/bin or /usr/local/sbin.  (You need sudo to put files in those directories.)

Using a symlink avoids the path issue since cron will tell root to run the script the link points to.

---

### Post by Nerflander on 2011-03-17
i used sudo mv "..." /usr/local/sbin 

to place it in the directory then i used your command to make a symlink before this i removed the .sh extension. Must i give it permissions to make it run?

---

### Post by SeijiSensei on 2011-03-17
> **Nerflander said:**
> i used sudo mv "..." /usr/local/sbin 

to place it in the directory then i used your command to make a symlink before this i removed the .sh extension. Must i give it permissions to make it run?

Yes, it needs "[execute]("http://www.perlfect.com/articles/chmod.shtml")" permissions.  If the file is owned by root, you just need to run "sudo chmod u+x /path/to/script".  That's the safest approach since it only lets the root user run the script.  If the file is owned by someone other than root, then run

```

sudo chown root.root /path/to/script
sudo chmod u+x /path/to/script

```

---

### Post by Nerflander on 2011-03-17
Alright , thats done , do i have to recreate the symlink again?


Edit: Its exucutable but it gives an error: line 752 mail command not found?

but thats weard caus i havnt changed anything in line 752 i only filled in the stuff you have to fill in in the begin,

---

### Post by SeijiSensei on 2011-03-17
> **Nerflander said:**
> Edit: Its exucutable but it gives an error: line 752 mail command not found?

Ubuntu doesn't ship a command-line mail client by default.  Use "sudo apt-get install bsd-mailx" to fix the problem.

---

### Post by Nerflander on 2011-03-17
Owke it works now as executeble! woooooh cheers for that :) took a bit but we got the point now and also , i will now await the daily routine if it does the job or not!

Thanks man :)


edit: Il post if the routine also works and il mark this as solved!

---


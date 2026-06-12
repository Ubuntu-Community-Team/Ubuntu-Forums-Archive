---
title: "A little help with a script"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-05-27
Hey guys,

I'm trying to run [_this 360 remux script_](http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html). I have all the packages installed, I have my script installed(and chmod'd), and I even setup and alias to start it.

But the thing is, when I input the alias into Terminal to start the script, I get this:

```
Usage: vidconv.sh <MKV>
```

So how exactly do I start this script to start remuxing a .mkv? I'm obviously new to scripts(I've only used two so far), so I'm sure there's something wrong that I'm doing.

Any help will be greatly appreciated.

Thanks.

---

### Post by anglican on 2010-05-27
> **h8uthemost said:**
> Hey guys,

I'm trying to run [_this 360 remux script_]("http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html"). I have all the packages installed, I have my script installed(and chmod'd), and I even setup and alias to start it.

But the thing is, when I input the alias into Terminal to start the script, I get this:

```
Usage: vidconv.sh <MKV>
```So how exactly do I start this script to start remuxing a .mkv? I'm obviously new to scripts(I've only used two so far), so I'm sure there's something wrong that I'm doing.

Any help will be greatly appreciated.

Thanks.
A quick look at the script and it seems you will get the usage message if you do not run it with one argument, which is the name of your mkv file. Are you typing:
```
vidconv.sh <filename.mkv>
```where <filename.mkv> is the name of the file you want to remux?

H

---

### Post by h8uthemost on 2010-05-28
Thanks for the reply anglican.

Well, first I tried it with the <> around the file name(with the name of the actual file name before the .mkv) and I get this error:

```
bash: syntax error near unexpected token `newline'
```

Then without the <> and I get this error:

```
vidconv.sh: command not found
```

---

### Post by benson444 on 2010-05-28
If you put the alias in the ~/.bashrc file then you'll need to logout and then back in, or call bash first so that .bashrc is read.

```
bash
vidconv.sh filename.mkv
```

Once you log back in you don't need to run the bash command.

Does it work when you run the script with the actual name and not your alias?

---

### Post by h8uthemost on 2010-05-28
How exactly would I run the script without the alias? Just enter the location to the script in terminal?

---

### Post by benson444 on 2010-05-28
When you enter a command, all the directories in your PATH environment variable are searched. If the command can't be found there then your current directory is searched (or maybe it's the other way round...). You can see the PATH settings with

```
echo $PATH
```

If you put the script in one of those directories, and it's executable, then you can run it from anywhere by just typing in the name of the script.

If it isn't, then you can cd to where it is and run it:

```
cd /home/username/scripts
scriptname.sh /home/username/filename.mkv
```

or run it with the full path name:

```
/home/username/scripts/scriptname.sh /home/username/filename.mkv
```

Does the alias still not work?

---

### Post by anglican on 2010-05-28
> **benson444 said:**
> 

If it isn't, then you can cd to where it is and run it:

```
cd /home/username/scripts
scriptname.sh /home/username/filename.mkv
```
This may not work - if the current directory isn't on your PATH, in which case
```
./scriptname.sh /home/username/filename.mkv
```Is needed.

> **benson444 said:**
> 
```
or run it with the full path name:

/home/username/scripts/scriptname.sh /home/username/filename.mkv
```Should always work.

BTW sorry (to h8uthemost)  about confusing you with the angle brackets<> - it's a unix convention that I obviously shouldn't take for granted people know.

---


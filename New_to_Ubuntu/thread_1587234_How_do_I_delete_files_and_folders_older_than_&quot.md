---
title: "How do I delete files and folders older than &quot;X&quot; days?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-10-03
Hi Ubuntu Community:

I record alot of streaming audio with streamripper andarchive the radio programs that I've recorded.

Well, guess what? I'm running out of hard disk! :cry:

I need to delete files and folders that are older than 60 days.

I found a nice website ([http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")) that provides some advice on this.

The recommendation there is to use:

[COLOR="blue"]**find*/path/to/files* -mtime +15 -exec rm {} \;**[/COLOR]

When I try to do this I get a problem.....

In my specific application I used:

[COLOR="Blue"][B]cd "/home/philipsmith/Music/MPR - Radio Heartland"
find . -mtime +15 -exec rm -R {} \;[/B][/COLOR]

and it wiped out the entire directory: **/home/philipsmith/Music/MPR - Radio Heartland**

I am quite the directory slayer! :rolleyes:

[COLOR="Blue"]**I didn't what the directory wiped out! How do I modify my code to only eliminate files older than 15 days?**[/COLOR]

Thanks!
Phil Smith

---

### Post by nothingspecial on 2010-10-03
If you want find to find only files and not directories you need to specify files

find /path [COLOR=Red]-type f[/COLOR] -rest of find command

---

### Post by Hippytaff on 2010-10-03
You can schedule a shell script by putting it in system>preferences>startup applications, by using contrab

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

---

### Post by sisco311 on 2010-10-03
Use the -type option:
```
find /path/to/dir -type f -mtime +15 -exec rm {} +
```

If you rm files, you don't need the -R (recursively) option and you can use the **-exec command {} +** syntax. For more info check out the man page:
```
man find
man find | less +2/"-type c"
man find | less +/"-exec command \{\} \+"
```

EDIT: I'm a little bit slow today... [noparse]:)[/noparse]

---

### Post by bprins on 2010-10-03
> **Phil Smith said:**
> Hi Ubuntu Community:

I record alot of streaming audio with streamripper andarchive the radio programs that I've recorded.

Well, guess what? I'm running out of hard disk! :cry:

I need to delete files and folders that are older than 60 days.

I found a nice website ([http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")) that provides some advice on this.

The recommendation there is to use:

[COLOR="blue"]**find*/path/to/files* -mtime +15 -exec rm {} \;**[/COLOR]

When I try to do this I get a problem.....

In my specific application I used:

[COLOR="Blue"][B]cd "/home/philipsmith/Music/MPR - Radio Heartland"
find . -mtime +15 -exec rm -R {} \;[/B][/COLOR]

and it wiped out the entire directory: **/home/philipsmith/Music/MPR - Radio Heartland**

I am quite the directory slayer! :rolleyes:

[COLOR="Blue"]**I didn't what the directory wiped out! How do I modify my code to only eliminate files older than 15 days?**[/COLOR]

Thanks!
Phil Smith

Hi,

not sure if I can help you, but let me give a try.

if you change your command to;
find . -mtime +15 -exec **echo** {} \;
then you will see which files and folders are found by your find command. you probably also will see that your directory is listed there as well.

Now, what goes wrong (I think) is that all files are deleted, which leaves your directory empty. Thus, rm is allowed to delete your directory as well. 

How to exclude your directory from being found can be done by extending your command with find '/path' -type f -mtime +X etc.

Just try it out a bit and verify the output by replacing "rm" with "echo". 

Good luck

---

### Post by Old Jimma on 2010-10-03
Wow! The Ubuntu Deities has spoken!

Many thanks!


Phil Smith
Duluthistan, GA

---


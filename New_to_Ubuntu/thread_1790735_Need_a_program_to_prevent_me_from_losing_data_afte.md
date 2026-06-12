---
title: "Need a program to prevent me from losing data after overwrite"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by tdrusk on 2011-06-25
Hey guys,
last night I was working on a project, the program crashed and overwrote  the file with a blank file. I had to start over. Is there a way to  basically create a folder that keeps a backup of every file that goes  into it automatically. For example, I create X.txt. After I overwrite it  it pushes the original to X0.1.txt and makes a new X.txt. I am looking  for the easiest and simplest solution possible. 
Thanks!

---

### Post by -kg- on 2011-06-25
What software were you using for your project?  From your description of what you want, I assume it was a written project?

Depending on which distro you're using, either OpenOffice or LibreOffice Writer has a facility "To save recovery information automatically every n minutes" (copied from the help files on LibreOffice).  Use that setting and you should be good to go.

Many of the better software titles will have such a facility.  Whatever you're using, pull up the help files and see if it has such a setting.

---

### Post by josephmills on 2011-06-25
remastersys is your friend [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by tdrusk on 2011-06-25
> **-kg- said:**
> What software were you using for your project?  From your description of what you want, I assume it was a written project?

Depending on which distro you're using, either OpenOffice or LibreOffice Writer has a facility "To save recovery information automatically every n minutes" (copied from the help files on LibreOffice).  Use that setting and you should be good to go.

Many of the better software titles will have such a facility.  Whatever you're using, pull up the help files and see if it has such a setting.
It was wxglade, which is very minimal but does the job well when it doesn't mess up.

---

### Post by TeoBigusGeekus on 2011-06-25
What about this:
Create a cron job that starts whenever you launch the program you work with.
The cron job will backup the folder you want to another folder, say every 15~30 minutes or so.
Just an idea...

---

### Post by tdrusk on 2011-06-25
> **TeoBigusGeekus said:**
> What about this:
Create a cron job that starts whenever you launch the program you work with.
The cron job will backup the folder you want to another folder, say every 15~30 minutes or so.
Just an idea...
Yep :) Just did this. A lot faster than messing with other software.

Just save the code as savemystuff and execute 
```
./savemystuff
```one level above the directory of the folder(so you can see it). It will back up ever minute to a folder with the same name as the folder you chose only +.backup. So for example the folder work would backup to work.backup.

When it asks do not type in the full directory name(/home/bob/Desktop/work), just the name of the directory(work).

I am sure there are more efficient ways to do this, but this script works.
```
#! /bin/bash


echo "This will save a copy of what you are working on every 3 minutes."
echo "Enter a directory to backup every 3 minutes."
read dir
mkdir "$dir.backup"
i=0
while [ $i == 0 ]
do
    date=`date +%m%d%y%H%M%S`
    cd $backup
    mkdir $date
    cd -
    rsync -auvr --progress --delete $dir/ "$dir.backup"/$date
    sleep 5
done
```

---

### Post by -kg- on 2011-06-25
I just went through a couple of tutorials on wxGlade and could find no setting that autosaves, so I'd say TeoBigusGeekus' suggestion of setting up a cron job would be the avenue you need to explore.

Pull up a terminal window and type:

```
man cron
```

That will give a fair description of the cron process, and undoubtedly there are many good tutorials on the 'net concerning setting up cronjobs.

<Edit> And I see we posted almost simultaneously. :lolflag:

Glad to see you have your problem dealt with!

---

### Post by The Cog on 2011-06-25
It might be worth looking at subversion. Maybe it's overkill, but it can keep track of every change you make. You could run a commit as a cron job every few minites - if there's no change it won't do anything.

---


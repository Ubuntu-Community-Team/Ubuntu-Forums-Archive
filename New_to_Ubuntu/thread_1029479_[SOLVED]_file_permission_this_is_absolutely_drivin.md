---
title: "[SOLVED] file permission this is absolutely driving me crazy"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-03
i get the following error message when i open the help files on a number of games. "the file  /usr/share/sgt-puzzles/help/index.html could not be read. this file might be missing or you do not have permission to read it.
no the files are there and i can open them using the application dillo (which opens a list of help files for various games)  it is just when i try to open the help files from the various games themselves that they wont open. any ideas been playing around for this for a few hours/tks cheesemaker

---

### Post by BDNiner on 2009-01-03
What are the permissions of the files? you can see the permissions by running ls -l while inside the directory from a terminal. I use 755 when setting file permissions so that i have read, write and execute permissions and everyone else just has read and write.

---

### Post by rburkartjo on 2009-01-03
bd,

drwxrwxrwx    3 root root  4096 2009-01-03 12:04 sgt-puzzles
/cheesemaker

---

### Post by BDNiner on 2009-01-03
Oh ok the files are owned by root. Are these files in your home directory or in a system directory. I would try changing the owner of the files and the group to your username using chown command.

---

### Post by lloydkuhnle on 2009-01-03
> **BDNiner said:**
> Oh ok the files are owned by root. Are these files in your home directory or in a system directory. I would try changing the owner of the files and the group to your username using chown command.

How do you do that?
On my 2nd. install of UBUNTU, I seem to have no permissions!

---

### Post by lswb on 2009-01-03
With the permissions you have shown the file should be readable by any user or process. Have you checked that the path to the files from your games is the same path that dillo is using?

---

### Post by jerome1232 on 2009-01-03
> **rburkartjo said:**
> bd,

drwxrwxrwx    3 root root  4096 2009-01-03 12:04 sgt-puzzles
/cheesemaker

That shows world readable writeable permissions, just to break that down the first letter d, inidcates that it's a directory, the next 3 letters are the Owners permissions, the middle 3 letters are the Groups permissions, the last 3 are everyone else's permissions.

So the owner,group, and everyone else has **r**ead, **w**rite, and e**x**ecute permissions (for directories execute means you can cd into the folder and see it's contents)

---

### Post by BDNiner on 2009-01-03
lswb brings up a good point, everybody has read, write and execute permissions. to change the owner of a file use the command:
```

sudo chown username:username /sgt-puzzles

```

to explain the command
*chown* is the command *username:username* is your username followed by your group or any group that you also want to have ownership of the file(s) */sgt-puzzles* is the path to the file you want to change to owner of.

---

### Post by rburkartjo on 2009-01-03
bd, tks for all your help good help will bookmark this thread for ref but still doesnt work and i tried a bunch of combos my user name is ray and the group is root. the problem maybe be because all of the help files are in .html

any way look this over tried all and still wont work
ray@ray-desktop:~$ sudo chown ray:root /usr/share/sgt-puzzles/help/index.html
ray@ray-desktop:~$ sudo chown root:ray /usr/share/sgt-puzzles/help/index.html
ray@ray-desktop:~$ sudo chown ray:ray /usr/share/sgt-puzzles/help/index.html
ray@ray-desktop:~$ sudo chown root:root /usr/share/sgt-puzzles/help/index.html
tks cheesemaker

---

### Post by BDNiner on 2009-01-03
I am sorry that it did not work out for you. the third option that you type is the one i would have used. You can try running the application as root and then see if you can access the help html files. just type *sudo* and then the *command* that starts the application.

---

### Post by Kareeser on 2009-01-03
Your group should be your own name.

ray:ray

Also, just because the directory itself gives you permissions, the files themselves do NOT.

Be careful with permissions. Applying them liberally can be a security risk.

```

sudo chmod -R 775 /usr/share/sgt-puzzles

```

the -R causes the command to run recursively, so that all of the files therein are also applied that permission.

---

### Post by rburkartjo on 2009-01-03
bd,
   thanks i already checked with the members of the linux board i host and they said they sometimes had help with html help files. just a thought note this
ray@ray-desktop:~$ sudo -i
root@ray-desktop:~#  /usr/share/sgt-puzzles/help/index
-bash: /usr/share/sgt-puzzles/help/index: No such file or directory
root@ray-desktop:~# 
what would happen if i mkdir for the above would that just work. just playing no big deal my wife has alz. and trying to make it as easy i can for her to play these games
/tks cheesemaker

---

### Post by handydan918 on 2009-01-03
I'd like to see a current ```
ls -l /usr/share/sgt-puzzles/help/index
```

And I have trouble believing that a good old fashioned ```
sudo chown -R ray /usr/share/sgt-puzzles/
``` would fail....

---

### Post by rburkartjo on 2009-01-03
handy,
as you requested

ray@ray-desktop:~$ sudo -i
root@ray-desktop:~# ls -l /usr/share/sgt-puzzles/help/index
ls: cannot access /usr/share/sgt-puzzles/help/index: No such file or directory
root@ray-desktop:~# 

and
ray@ray-desktop:~$ sudo chown -R ray /usr/share/sgt-puzzles/
ray@ray-desktop:~$ 

still doesnt work yea beats me too
/cheesemaker

---

### Post by lswb on 2009-01-03
> **rburkartjo said:**
> handy,
as you requested

ray@ray-desktop:~$ sudo -i
root@ray-desktop:~# ls -l /usr/share/sgt-puzzles/help/index
ls: cannot access /usr/share/sgt-puzzles/help/index: No such file or directory
root@ray-desktop:~# 

and
ray@ray-desktop:~$ sudo chown -R ray /usr/share/sgt-puzzles/
ray@ray-desktop:~$ 

still doesnt work yea beats me too
/cheesemaker

If it is not too late, DO NOT change any of your file permissions or owner/groups. It is almost certain that this is just a simple misconfiguration of a path entry somewhere. Your ls command shows that THERE IS NO FILE "/usr/share/sgt-puzzles/help/index" 

If I had to guess, I'd say it is at
 /usr/share/*doc*/sgt-puzzles/help/index.*html*"

but why guess? Use the command 
```

find / -name "sgt-puzzles" -type d

```
to find the sgt-puzzles directory. (It might take several minutes to complete) Then cd to that directory and 
```

find . -name index* 

```
to find out exactly where this index file is.

Then put the correct path to this file in the configuration of whatever application needs it.

---

### Post by rburkartjo on 2009-01-04
iswb,
the correct path was /usr/share/doc/sgt-puzzles the when  clicked on the html file in this location it took me to /usr/share/doc/sgt-puzzles/html
and that location lists all the htmls for the games. but i am lost how to get them to the help section of games themselves. okay check this out go to 
applications /add/remove  then add the game flip there are a host of others that have this problem. once you have installed open the program and click on the help and select either of the first two options and you will see what i mean./tks cheesemaker

---

### Post by lswb on 2009-01-04
I don't see any game named "flip" and honestly I'd rather not install any games on my system even temporarily. I did try a few of the games that are default installed and the help worked in all of them, though the gnome help browser was used rather than a web browser. 

Are you sure that these games are even capable of opening an html file on their own? It is not unusual for a program to have html help or documentation files meant to be viewed with a regular web browser.

---

### Post by rburkartjo on 2009-01-04
okay y'all tks for all the help i will just have to use the work around this has been a good tread for learning chown/tks cheesemaker

---

### Post by rburkartjo on 2009-01-04
just a final follow up. after doing some more search i found that all of these game programs that failed to open the help menu when clicked were written by one person. these were all old exe programs that he tried to make compatible for linux and mac to. and he acknowledge that the help programs could only be opened in html format/cheesemaker

---


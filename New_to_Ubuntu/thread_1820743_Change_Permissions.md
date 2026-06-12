---
title: "Change Permissions"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by gigenieks on 2011-08-08
Hi all,


yesterday I installed Xubuntu 11.04. Before actual installation I moved all files to various other hard drives. 
Then I installed Xubuntu on 120GB IDE HDD. :)

After that I shut down computer removed hard drive and placed it in other PC (where files were copied in first place) so I could copy all files in my newly created Xubuntu home directories.


99% of files have X sign attached if I look at files in Thunar. (see attachment)
If I right click > properties > Permissions then I see permission set to [COLOR="Navy"]**root**[/COLOR].. (also can check attachment)


So, I did some googling and found:
[LIST]
[*][File Permissions]("https://help.ubuntu.com/community/FilePermissions")
[*][Root Sudo]("https://help.ubuntu.com/community/RootSudo")
[/LIST]

Some citation:
> 
To change or edit files that are owned by root, [COLOR="DarkRed"]**sudo**[/COLOR] must be used.

> 
You should [COLOR="DarkRed"]**never**[/COLOR] use normal sudo to start *graphical applications* as root.
You should use gksudo (kdesudo on Kubuntu) to run such programs.

What is ment with "graphical applications"? Is, for example, Xubuntu file manager Thunar graphical application? 
Please explaim someone this.

O.K next I found:
> 
The command to use when modifying permissions is chmod.

and
```

chmod with sudo

```
is for:
> 
Changing permissions on **files that you do not have ownership of**: 

(Note that changing permissions the wrong way on the wrong files can quickly mess up your system a great deal! Please be careful when using sudo!)


OK so I have to use sudo chmod, but I won't do that on each file...
So --->
> 
To change all the permissions of each file and folder under a specified directory at once, use **sudo chmod with -R**

fine, but a bit further down is said following:
> 
To assign reasonably secure permissions to files and folders/directories, it's common to give files a permission of 644, and directories a 755 permission, since chmod -R assigns to both.


And:
> 
WARNING: Although it's been said, it's worth mentioning in context of a gotcha typo. Please note, Recursively deleting or chown-ing files are [COLOR="Navy"]**extremely dangerous**[/COLOR]. 

You will not be the first, nor the last, person to add one too many spaces into the command.




So how exactly should I continue? :confused:

For example for my Documents directory (see attachment) 
I would really appreciate some concrete examples, because I don't want to make those file unreadable or mess something up (it is said to be not just dangerous, but extremely dangerous) :frown:

I have very limited experience using terminal. I can install some programs, flash that kinda thing.
So please show some step-by-step guidance! 

Waiting for replies.:rolleyes:

---

### Post by gigenieks on 2011-08-08
bump :confused:

---

### Post by SalHelder on 2011-08-08
First of all "You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs." means that you have to use the command gksudo before running an application as root. For instance:

gksudo synaptic

That will open the synpatic package manager. You can also use the command su -, which will make your terminal a root terminal with the ability to launch aplications until you close it or you end the session. Example:

su -
synaptic

To end the session:
exit

Try this that will probably be easier than using chmod:

1. Go the console and type:
su -

2. Open thunar as root, type now:
thunar

3. Go to the folder where you have the file/files.

4. Select, right click and go to properties.

5. In the permission tab set all to all users (or others it's something like that).

You should be able to use the files now.

---

### Post by Wim Sturkenboom on 2011-08-08
```

sudo chown -R username path/to/directory/with/files/to/copy

```
will change the ownership of the directory containing the files and the files and directories in there; replace username by the name of the user that you're logged in as (gigenieks?)

```

sudo chmod -R 755 path/to/directory/with/files/to/copy

```
will change the permissions of the directory containing the files and the files and directories in there so any user can copy them

If you tells us which directory has your files, we can give the exact command.

---

### Post by gigenieks on 2011-08-14
OK how I fixed everything the way I wanted:
Change file & folder user and group ownership to **gigenieks**
```

sudo chown -R gigenieks:gigenieks /home/gigenieks/folder/folder

```
For example change user to gigenieks and group to gigenieks (default if you check permissions tab in newly created folder) to Info folder:
```

sudo chown -R gigenieks:gigenieks /home/gigenieks/Documents/Info

```
Result: every folder inside 'Info' and every file got User: gigenieks, Group: gigenieks (before User: root, group: root)

I also had to change file permissions in group and others to "read only" (default) --->
```

chown -R go+r /home/gigenieks/Documents/Info

``` 

Hope it helps someone. :rolleyes:

---


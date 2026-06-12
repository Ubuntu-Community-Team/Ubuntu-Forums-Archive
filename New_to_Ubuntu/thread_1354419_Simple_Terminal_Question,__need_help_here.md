---
title: "Simple Terminal Question,  need help here"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by stevenhoe on 2009-12-13
Hi all
I want to ask, when u close your terminal while its still downloading in the middle like 18 % or more, where the downloaded file will be located in our ubuntu drive ? file system or other else ? 

I canceled to download and install the application because I think its useless, so right now I want to delete that half downloaded file (which is from terminal), where should I find it ?

---

### Post by Ichtyandr on 2009-12-13
usually the home folder ?

---

### Post by stevenhoe on 2009-12-13
thanks, but can u be more specific ?

---

### Post by kk0sse54 on 2009-12-13
How exactly were you downloading this program? Via a script or wget or something else? Most likely it's still sitting in your home folder, open up a terminal and type 
```
cd ~/
ls
```

"cd" is the command to change directory, in this case we're changing directory to your home folder just to be sure even though it should already be there when you first open up the terminal.

"ls" is the command to list all files in the current directory and if the file is in your home directory it should show up among the list. Once you find the file, type the command

```
rm -i <filename>
```

"rm" deletes files and folders but make sure that's exactly the file you want since this action is irreversible. 

If you don't see the folder in your home directory  "cd" to another directory such as ~/Desktop or /tmp and issue the same command "ls" to find the file. Of course the problem with this is that you need to know what the file is called in which case it would be a lot easier to know how you downloaded this file. Type "man <command>" to find out more information about any of the terminal commands

*Note, you could also use nautilus to search for the file and delete it

---

### Post by talsemgeest on 2009-12-13
It depends what you were downloading. If you were downloading a file with something like wget, it will be in your home folder (/home/<username>/). If you were downloading an application with something like "sudo apt-get install application", then the temporary file will be in /var/cache/apt/archives/partial. To delete the partial files, type ```
sudo rm /var/cache/apt/archives/partial/*
```
Note that this will delete all the files in that directory.

---

### Post by Greenbean209 on 2009-12-13
Here is a simple Answer. If it was one file and it was incomplete chances are yhat it was automatically deleted. But if the download involved several files, some may still be left over. This can be solved easily. 
You can use this command:

```
sudo apt-get autoremove
```

what this does is it makes the computer search for files that have no purpous such as files you may have downloaded while installing a new program. It will remove the meaningless files. 

Note this will NOT delete person files like music pictures ect....

---

### Post by stevenhoe on 2009-12-14
Okay thanks folks for great and detail answers :)

---

### Post by talsemgeest on 2009-12-14
> **stevenhoe said:**
> Okay thanks folks for great and detail answers :)
I hope it worked for you :)

---

### Post by The_Pirate_King on 2009-12-14
I would recommend doing a complete reinstall of Ubuntu; it would be easier than trying to fix this manually.

Kidding, kidding.  xD

But I think if you were installing something, the installation files will be in your temporary files and thus they should be deleted automatically after a certain amount of time.

---

### Post by ankspo71 on 2009-12-14
Hi,
If you can remember part of the name of the file, the locate command might help you find it. I have only used this for installed files though.... I haven't tried personal files or downloaded files yet (because I keep everything on a separate hard drive)... but it might help.

for example: 
```
sudo updatedb      
locate thefilename
```ubdatedb updates the file database.

if you get a lot of results, you should use the ' | more ' option like:
```
sudo updatedb      
locate thefilename | more 
```You can also use ls command to list the contents of your home directory. It might be sitting right there like the others have said. 

```
ls /home/yourname 
```James

---


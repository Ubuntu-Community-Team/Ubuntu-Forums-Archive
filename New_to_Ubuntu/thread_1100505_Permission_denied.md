---
title: "Permission denied"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Swatfoot on 2009-03-19
Hello I just downloaded some icons and extracted the folder to my desktop when I tried moving folder to icons folder but 
I get error permisson denied.Is they a way to login sudo to move folders around, or is the command line the only way.

---

### Post by scribbles on 2009-03-19
```
gksudo nautilus
```

Run that in Terminal. It will open Nautilus with root privileges and allow that instance to do what you need it to.

---

### Post by paultag on 2009-03-19
It is not very good to use elevated superuser privs in a GUI, out of common practice.

You should learn how to use the command line to preform system wide tasks, in the GUI one missed click and you have the ablility to destroy the /home folder.

for future ref:

to copy:
sudo cp <file_orig> <file_dest>

for more information, type:
man cp

cheers,
Tag

---

### Post by strife242 on 2009-03-19
Depending on if you are using gnome or kde use from terminal:

gksudo nautilus (for gnome)
kdesu konqueror (for kde)

The command will open your filebrowser but with root permissions rather than user permissions. Needless to say, you need to take extra care on what you do as usual when operating as root.

---

### Post by Swatfoot on 2009-03-19
Thank you for replies Im running gnome,and I can see where moving folders around without using command line is probally a windows habit so im gonna try to do it with command line if that fails i do it gui way.

---

### Post by sisco311 on 2009-03-19
Just copy your icon themes in /home/username/.icons . Create the directory if doesn't exist. You can also create a /home/username/.themes directory for your gtk themes.

---

### Post by Swatfoot on 2009-03-19
Thank you sisco311 I will try that but trying to learn the right commands to move this file this is what I ve tried so far can im not sure but think im getting closer.    


brandon@brandon-desktop:~$ cp /home/brandon/Desktop/Polar_icons_2 /user/share/icons
cp: cannot stat `/home/brandon/Desktop/Polar_icons_2': No such file or directory
brandon@brandon-desktop:~$ cd Desktop/
brandon@brandon-desktop:~/Desktop$ cp <Polar_icons_2> </usr/share/icon>
bash: syntax error near unexpected token `<'
brandon@brandon-desktop:~/Desktop$

---

### Post by sisco311 on 2009-03-19
You can use the *ls* command to list the content of the directory:
```
cd ~/Desktop
ls

```
TAB completion is very useful. Type the first characters then press TAB to auto complete:
```
sudo cp -r Pol  #hit TAB
```
After pressing TAB it will be completed to the whole filename:
```
sudo cp -r Polar_icons_whatever_bla_bla
```

[uhelp]community/UsingTheTerminal[/uhelp]
[uhelp]community/RootSudo[/uhelp]

---

### Post by Swatfoot on 2009-03-19
This worked like a charm but why the strange syntax on Polar icons 2.


brandon@brandon-desktop:~/Desktop$ sudo cp -r Polar\ Icons\ 2/ /usr/share/icons

---

### Post by oldos2er on 2009-03-19
> **Swatfoot said:**
> This worked like a charm but why the strange syntax on Polar icons 2.


brandon@brandon-desktop:~/Desktop$ sudo cp -r Polar\ Icons\ 2/ /usr/share/icons

 Because there are spaces in the directory name, the file system has to have a way to recognize them. The "\" tell it to retain but ignore the next character i.e., a space.

---

### Post by sisco311 on 2009-03-19
space is a special character(delimiter) in bash. commands and arguments are separated from each other with a space.

the backslash ("\") is an escape character. [escape characters]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html") are used to remove the special meaning from a single character.  

e.g.:

you can create an empty file with the *touch* command
```
touch my file
```
will create two empty files: *my* and *file*

to create a file named "my file":
[list][*]you can quote the whole name
[*]type a backslash before the space[/list] 
```
touch "my file" 
touch my\ file  
```

---

### Post by Swatfoot on 2009-03-19
> **oldos2er said:**
> Because there are spaces in the directory name, the file system has to have a way to recognize them. The "\" tell it to retain but ignore the next character i.e., a space.


Thanks for explaining that makes sense to me .

---


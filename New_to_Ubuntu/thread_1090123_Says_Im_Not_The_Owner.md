---
title: "Says Im Not The Owner"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by rhconcepts on 2009-03-07
Im very new to this, but I want to set up ubuntu to run apache. I have 3 sites I want to move over from my windows pc. I had a hard time trying to figure out apache on that to. I got apache installed with no problem but when I try to edit the config file it tells me I cant save them. So I looked at the permissions for that file and it says that im not the owner so I cant do anything. How do you become the owner? I only have the main user name and never made a second one so why wouldn't I be the owner.

I hope I posted this in the right place.. Thanks 

Also where would be the best place to find and ask for help about setting up apache.

---

### Post by mrbiggbrain on 2009-03-07
Even though you made 1 user name there are two users,

<username you made>
root

now root is your super user, he owns everything, all your files be his! the only files you own are for your home folder, and files or folders you create.

Now on a ubuntu system, root is this mysterious thing in the background, you cant become root, you cant log in as root (as you can on other systems) but you can impercinate root, put on a root costume as you will, to do this use sudo before a command.

```
sudo chown -R user-name /directory-name/
```

that command will change a folders owner, recursivly, all folders, all files within that folder, as well as all files and folders in folders, in folders, ect, ect.

now this isnt something you should do often, and you may want to make a new user of some kind apache-user or something so he can have read/write access.

you can also do this with groups so anyone in that group can own it. theres also R-W-X permissions...

if you have ?? ask away


EDIT!:::

to exsplaine a little better, the reason you should create a new user is seperation. linux is secure becuse things do what theya re allowed to do, and nothing more. if you lock a man in a room, chances are he is only going to be able to destroy that room, no matter what he does... let him out, and your in deep toruble if he does do something wrong. 

this isnt saying somones going to hack you, it protects you from yourself too, by say a command like

```
rm -r /
```
instead of 
```
rm -r /new-folder
```

the first one eraces your whole OS,
the second one a folder...

---

### Post by mikewhatever on 2009-03-07
If you want to edit a config file, use <sudo nano /path-to/file.fonfig>. Enter your password when asked, and voila.

---

### Post by rhconcepts on 2009-03-07
lol I lost my hair trying to get that. Thanks so much Im going to and that to my notes. 

Now after im done can I send the permissions back to root so I don't mess it up some how?

would I just say [COLOR="DarkGreen"]sudo chown -R root /etc/apache2
[/COLOR]

---

### Post by mikewhatever on 2009-03-08
It is rather silly and absolutely unnecessary to chown the whole directory just to edit a config file. I don't know why the other poster even mentioned it.

---

### Post by Sidewinder1 on 2009-03-08
Can't really help with Apache as I've never used it. There are two quick ways to edit a root config or text file:
```
gksudo gedit
```
Then type your user password

or in nautilus find the file that you wish to edit, right click on it, then "Open as Administrator".
HTH
Side

---

### Post by rhconcepts on 2009-03-08
Ok you guys got me lost now. I did get rights to it by doing what mrbiggbrain said "thanks" Im ok with doing the folder and everything inside of it. But I would like to lock it back up so someone or even I dont mess it up. 

Now mikewhatever if I do this <sudo nano /path-to/file.fonfig> does that do the same as <sudo chown -R username /etc/apache2> but just for the one config file? And would I do <sudo nano /ect/apache2/config.httpd.fonfig> that is if im saying config.httpd is the file name and /ect/apache2/ is where it is at.

---

### Post by oldos2er on 2009-03-08
> **rhconcepts said:**
> Ok you guys got me lost now. I did get rights to it by doing what mrbiggbrain said "thanks" Im ok with doing the folder and everything inside of it. But I would like to lock it back up so someone or even I dont mess it up. 

Now mikewhatever if I do this <sudo nano /path-to/file.fonfig> does that do the same as <sudo chown -R username /etc/apache2> but just for the one config file? And would I do <sudo nano /ect/apache2/config.httpd.fonfig> that is if im saying config.httpd is the file name and /ect/apache2/ is where it is at.

 As was said, changing ownership of an entire directory to edit one file is not the way to go.

 Using 'sudo nano...' opens the nano editor and gives you admin privileges to edit and save the file as needed. It's doesn't touch file permissions.

 I suggest you read [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) and [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by rhconcepts on 2009-03-11
I tried it your way and found it to be much harder to do. I could edit the file but I could not do copy and past into it. I would like to past a few lines into the file then save it. Or did I miss something?

---


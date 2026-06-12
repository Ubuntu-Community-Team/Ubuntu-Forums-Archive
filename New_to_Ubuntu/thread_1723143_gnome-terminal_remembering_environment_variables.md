---
title: "gnome-terminal: remembering environment variables"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by gidra on 2011-04-06
I'm trying to set some environment variables using export MYENV_VAR=/path/to/var which works perfectly fine. However when I end my session in terminal it doesn't remember the path, I have to retype it once again. Any ideas how to make terminal remember environment variables. Thanks

---

### Post by TeoBigusGeekus on 2011-04-06
Add your exports to your .bashrc file (located in your home folder).

---

### Post by gidra on 2011-04-06
Thanks for your reply. Adding "export MYENV_VAR=/path/to/var" to the end of .bashrc did the trick :)

---

### Post by TeoBigusGeekus on 2011-04-06
Glad to hear that! Don't forget to mark the thread as solved.

---

### Post by gidra on 2011-04-06
Was going to mark it as solved, but another problem cropped up. Now I'm trying to sudo a command, such command depends on the variables I defined and guess what; it ain't finding the env variables anymore. Any workaround please?

---

### Post by TeoBigusGeekus on 2011-04-06
Try this
```
sudo cp ~/.bashrc /root/
```

---

### Post by gidra on 2011-04-06
Copied it into root, still no go :(

---

### Post by TeoBigusGeekus on 2011-04-06
Sorry, my mistake...
The universal bash configuration is of course /etc/bash.bashrc
First make a backup
```
sudo mv /etc/bash.bashrc /etc/bash.bashrc_old
```
Then copy your personal bashrc to the etc folder and rename it
```
sudo cp ~/.bashrc /etc/bash.bashrc
```
Delete the redundant bashrc from root's folder
```
sudo rm /root/.bashrc
```
and I think you're done.

EDIT: Alternatively, you could just add your exports to /etc/bash.bashrc

---

### Post by gidra on 2011-04-06
Sorry to say Teo, still no go. I also manually checked that the /etc/bash.bashrc has the relevant entries appended. When I run sudo it still asking for env variables

---

### Post by TeoBigusGeekus on 2011-04-06
Ok. Try this: create a file in your home folder called .bash_profile with this line into it:
```
source ~/.bashrc
```
If it already exists don't create it, just append the line.

Now call sudo with the -i option. Report back.

---

### Post by gidra on 2011-04-07
Sincere apologies for the belated reply (we had a power cut in the middle of the night yesterday). So finally it works(with some extra tweaking)

So here's what I did: I added this entry in /etc/environment : MYENV_PATH="/path/to/env_var". I then sudo -i command and voila. 
Another option which I than discovered was to add nothing besides the entries to my .bashrc and sudo -E command, this will retain my personal .bashrc and carry forward the environment variables. 

So I guess I can mark this thread as solved. Thanks a lot for your generous help

---

### Post by TeoBigusGeekus on 2011-04-07
Glad you've made it mate.

---


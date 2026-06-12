---
title: "Cairo Dock install troubles"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by superninja on 2010-08-07
So I tried to install Cairo Dock using these instructions,[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock"). I used the very first method, From the Repository. And I have no idea what went wrong, it did not download or install. All I did was type in the commands and nothing happened. Now when ever I try to run a command or open up Synaptic Package Manager, I get this error 'E:Type 'wgat' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

It also says "Please report this bug against the 'update-manager' package". Should I report the bug? Thank you

---

### Post by superninja on 2010-08-08
I am running Ubuntu 10.04 on a Sony VAIO laptop

---

### Post by Zorgoth on 2010-08-08
I am sure that "wgat" is a type and was supposed to be "wget."

Also, I do not believe you were supposed to add any lines including wget to that file, but rather to execute them from the terminal...

---

### Post by superninja on 2010-08-08
Oh! Ok, so was I supposed to put that into, for example gedit text editor, then compile it?

---

### Post by superninja on 2010-08-08
No, thats not right at all... Sorry, I don't understand (obviously)...

---

### Post by 0004tom on 2010-08-08
```
echo "deb http://repository.glx-dock.org/ubuntu $(lsb_release -sc) cairo-dock ## Cairo-Dock-Stable" | sudo tee -a /etc/apt/sources.list 
```
 
```
wget -q http://repository.glx-dock.org/cairo-dock.gpg -O- | sudo apt-key add - 
```

```
sudo apt-get update 
```

```
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

No each one is a separate command, that you should run in a terminal

---

### Post by superninja on 2010-08-08
I got it figured out. The error I was getting was that I had an error in my code, so I fixed the errors and installed it and it is working now :) thanks for all your help

---


---
title: "Weird path for default"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by linuxnovice on 2009-01-06
Hi,

For last few days I have been having this problem. My default path is set to /usr/bin instead of /home/$USER/. What I mean by that is whenever I open terminal the pwd is /usr/bin. If I wanted to open some file from program, for e.g. if I have gedit open and I press the file open button to open a text file, it points /usr/bin and I have to traverse my way to my home directory. This is not just with gedit..its with all the programs that I use..like mplayer, evince etc. 

I suspect I need to set the default path somewhere but I am not sure where. Any help is appreciated.

Thanks.

---

### Post by amauk on 2009-01-06
try, System > Admin > Users & groups
under properties > advanced, you can set your home folder

---

### Post by linuxnovice on 2009-01-06
> **amauk said:**
> try, System > Admin > Users & groups
under properties > advanced, you can set your home folder

The home directory is pointing to /home/$USER.

---

### Post by decoherence on 2009-01-06
which terminal program are you using?

if it's gnome-terminal, check your profile preferences and make sure you aren't running a custom command.

---

### Post by linuxnovice on 2009-01-06
> **decoherence said:**
> which terminal program are you using?

if it's gnome-terminal, check your profile preferences and make sure you aren't running a custom command.

I checked my profie but there is no option to set my default path. Secondly, this is not a problem just with the terminal like I mentioned.

---

### Post by linuxnovice on 2009-01-06
Bump

---

### Post by handydan918 on 2009-01-06
Well, since no one else is taking a swing at this...
Post the output of the following:

```
echo $HOME
```
```
echo $PATH
```
```
echo $USER
```

---

### Post by linuxnovice on 2009-01-06
> **handydan918 said:**
> Well, since no one else is taking a swing at this...
Post the output of the following:


```
echo $HOME
/home/sudarshan
```
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/home/sudarshan/myscripts:/opt/matlab/bin
```
```
echo $USER
sudarshan
```

---

### Post by decoherence on 2009-01-07
ah... i re-read your post.

that's a strange one. do you know of any programs that DON'T send you to /usr/bin?

The only thing I can suggest is to check if it's hardcoded somewhere in your gnome configuration

```
find . | grep -H "/usr/bin"
```

if there is a string /usr/bin in a config file in your home directory, this command will find it and tell you what file contains it, which is a start.

---

### Post by linuxnovice on 2009-01-07
> **decoherence said:**
> ah... i re-read your post.

that's a strange one. do you know of any programs that DON'T send you to /usr/bin?

The only thing I can suggest is to check if it's hardcoded somewhere in your gnome configuration

```
find . | grep -H "/usr/bin"
```

if there is a string /usr/bin in a config file in your home directory, this command will find it and tell you what file contains it, which is a start.

Well that came out with nothing. As far as I can say..Amarok doesnt send me there. Could it be a gnome thing (i am assuming that amarok doesnt use a lot gnome libraries).

Thanks.

---

### Post by ibuclaw on 2009-01-07
> find . | grep -H "/usr/bin"
well of course this find command won't produce anything, as grep is only processing the filenames, not the contents of the file.

The proper way to do it would be:
```
sudo find ~ -type f -exec grep -H "/usr/bin" "{}" \;
```
But don't run it, as the output will be too much to analyse/find something of use inside it.

Maybe a better way to find it would be grepping your 'set' environment.
```
set | grep "/usr/bin"
```

Also, can you explain 'default path' better?
Do you mean when you run just
```
cd
```
You jump to the /usr/bin directory, instead of the $HOME one?

Regards
Iain

---

### Post by linuxnovice on 2009-01-07
> **tinivole said:**
> well of course this find command won't produce anything, as grep is only processing the filenames, not the contents of the file.

The proper way to do it would be:
```
sudo find ~ -type f -exec grep -H "/usr/bin" "{}" \;
```
But don't run it, as the output will be too much to analyse/find something of use inside it.

Maybe a better way to find it would be grepping your 'set' environment.
```
set | grep "/usr/bin"
```

Also, can you explain 'default path' better?
Do you mean when you run just
```
cd
```
You jump to the /usr/bin directory, instead of the $HOME one?

Regards
Iain

Hey,

Ok I ran the command you suggested and here is the output:
```
CVSEDITOR=/usr/bin/vim
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/home/sudarshan/myscripts:/opt/matlab/bin
        /usr/bin/python /usr/lib/command-not-found -- $1;

```

So what I mean by default path is not what you indicated. So suppose I open gedit (just gedit not a text file but gedit directly). Then I go to file->open. Now, here instead of pointing to /home/$USER, it is pointing to /usr/bin. Obivously the text files I want to open are not there..they are in my home folder and I have to traverse back to my home folder. Furthermore, since it contains a WHOLE lot of binaries it takes too long to lond. 

Similarly, I go click on terminal. The terminal window comes up but the pwd is /usr/bin. I need to cd to my home directory.

An update from my original post is that I just found out that this is happening only in gedit and terminal. For the other apps, its not happening anymore (i dont know why though).

Thanks.

---

### Post by decoherence on 2009-01-08
>  find . | grep -H "/usr/bin"
well of course this find command won't produce anything, as grep is only processing the filenames, not the contents of the file.

Oops! Nice catch.

Sooo... this a gconf thing? I was looking for a likely suspect in there but couldn't find anything.

---

### Post by decoherence on 2009-01-08
double post

---

### Post by decoherence on 2009-01-08
triple post

---

### Post by decoherence on 2009-01-08
quadruple post... darn i fail at this thread!:oops:

sorry!

---


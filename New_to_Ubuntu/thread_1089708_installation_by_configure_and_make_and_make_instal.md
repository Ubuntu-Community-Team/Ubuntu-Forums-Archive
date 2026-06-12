---
title: "installation by configure and make and make install"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-07
Hi,
I was wondering if I install some software by configure, make and make install, would the generated executable still work with its full path specified if I move it elsewhere? In what cases it wouldn't? Is there something like Windows registry that caused the relocated executable not work?
Thanks!

---

### Post by taurus on 2009-03-07
It still works if you move it somewhere else later providing that you still have the necessary libraries on your machine.

You can tell by running, assuming you are in the directory where filename is

```
ldd filename
```

---

### Post by rhcm123 on 2009-03-07
> **flylehe said:**
> Hi,
I was wondering if I install some software by configure, make and make install, would the generated executable still work with its full path specified if I move it elsewhere?
Thanks!

I had this problem a while ago, and I fixed it actually rather simply.
I had a script called ubucleaner that I got from the ubuntu mailing list. I extracted it to /root/(really long file name I don't feel like typing). 
now instead of typing that path everytime I wanted to run the script, I simply made a symbolic link to it in /bin. so now, every time I open up the command prompt and type sudo ubucleaner, it autofollows the path to the script.


I think you could adapt this to your situation. Just extract the program and make it in an out of the way directory, then symbolic link it in /bin

---

### Post by flylehe on 2009-03-07
As to the dynamically-linking libraries, as long as I don't move the libraries either, I think the relocated executable would still find the libraries it depends on?

As to the path,I think there are two ways:
1. add the new path to PATH
2. create symlink to the new path at the old one
How does software installation play with Windows registry anyway? Is it just adding the path to some environmental variable like PATH and stored in registry?

---

### Post by taurus on 2009-03-07
Basically, you can create a bin directory in your $HOME, ~/bin, and install your personal binaries in there.  Then, edit ~/.bashrc and add 

```
PATH=$PATH:~/bin
export PATH
```
to the end of it.  Now, all you have to do is to call the programs by names from anywhere and they should run.  You can also create launchers in the top panel for those progs to run them by clicking the icons.

However, do whichever way you feel right for you.

---

### Post by MaindotC on 2009-03-07
Hey taurus I hadn't seen that ldd command before and it's very helpful.  Thanks!

---

### Post by flylehe on 2009-03-07
Thanks!

As to the dynamically-linking libraries, as long as I don't move the libraries either, I think the relocated executable would still find the libraries it depends on?

As to the new path, why add "export PATH"? I remember it also works without it in .bashrc, .bash_profile and .profile. Correct?

---

### Post by taurus on 2009-03-07
If you move your libraries to somewhere non-standard, then you need to add the whole path to your /etc/ld.so.conf.d/libc.conf and rerun **sudo ldconfig** again.

---

### Post by rhcm123 on 2009-03-07
> **flylehe said:**
> As to the dynamically-linking libraries, as long as I don't move the libraries either, I think the relocated executable would still find the libraries it depends on?

As to the path,I think there are two ways:
1. add the new path to PATH
2. create symlink to the new path at the old one
How does software installation play with Windows registry anyway? Is it just adding the path to some environmental variable like PATH and stored in registry?

Ok, i think i've consued you. Don't move the libraries, and the executable *should* be able to find them. But the much simpler to do this

```
sudo ln -s /where/the/file/is/now /where/you/would/like/it 
```
This dosent move it, just creates a symbolic link to it, so you don't have to worry about libary dependancies

---

### Post by flylehe on 2009-03-07
Thanks Taurus and rhcm123!
Still, does it need to have "export PATH" in .bashrc, .bash_profile and .profile ?

---

### Post by rhcm123 on 2009-03-07
> **flylehe said:**
> Thanks Taurus and rhcm123!
Still, does it need to have "export PATH" in .bashrc, .bash_profile and .profile ?

you'd have to ask taurus, i don't usually... actually ever... compile my own binaries :) :lolflag:

---

### Post by taurus on 2009-03-07
> **flylehe said:**
> Thanks Taurus and rhcm123!
Still, does it need to have "export PATH" in .bashrc, .bash_profile and .profile ?

If you want to add a new path to your current PATH, then you can do it (in ~/.bashrc)

```
PATH=$PATH:/new_path
export PATH
```
or
```
export PATH=$PATH:/new_path
```
But if you move a binary that is already on your PATH, then you don't have to add or export anything.

This command will show you your PATH and among other things.

```
set
```

---


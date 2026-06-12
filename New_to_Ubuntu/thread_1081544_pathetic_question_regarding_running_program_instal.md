---
title: "pathetic question regarding running program installer"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-26
terribly sorry for the beyond noob question...

im trying to install sun virtualBox (not OSE).  went to virtualbox.org and got the installer.  ive installed the package installer, but am unable to figure out how to run the installer itself!

wow, this is sad.


i have tried
apt-get install virtualbox-2.1
and that seems to just reinstall the installer

ive also tried (though since the virtualbox isnt installed yet if wont work)
$ virtualbox-2.1
bash: virtualbox-2.1: command not found

what is the terminal command for running this installer?

is there another way besides the terminal of running the package installer virtualbox-2.1?

thanks,

---

### Post by taurus on 2009-02-26
Perhaps run the program with the name only, not including the version.

```
virtualbox
```

---

### Post by thtrgremlin on 2009-02-26
no need to beat yourself up. The command is simply ```
virtualbox
``` The versions need identical names, but typically commands link to links of programs. That way other programs trying to access the same utility, it just needs to know the name of the command and not the program. So on any ubuntu or likely any Gnu/linux OS with any version of virtualbox, the command will just be 'virtualbox'.

Hope that helps.

Note: oh, just to add, tab completion is your friend. If you had typed the first few letters, and then hit tab, it would either complete the unique name match, or beep. if it beeps, that means there was more than one match, and hitting tab again would show possible matches. GREAT tool. For example, just typing 'vir[tab]' on my terminal only has the result of 'virtualbox'. It is my choice of VM also.

---

### Post by kanikilu on 2009-02-26
> **nachos99 said:**
> terribly sorry for the beyond noob question...

im trying to install sun virtualBox (not OSE).  went to virtualbox.org and got the installer.  ive installed the package installer, but am unable to figure out how to run the installer itself!

wow, this is sad.


i have tried
apt-get install virtualbox-2.1
and that seems to just reinstall the installer

ive also tried (though since the virtualbox isnt installed yet if wont work)
$ virtualbox-2.1
bash: virtualbox-2.1: command not found

what is the terminal command for running this installer?

is there another way besides the terminal of running the package installer virtualbox-2.1?

thanks,

If you got the .deb file, you can just double-click on it to start the install, or if in the command line, you can use dpkg -i. 

Although, VirtualBox has a repository you can add to your sources.list so that you can just use apt-get to install it and keep it up to date. Check out this page for detailed instructions:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

//EDIT - wait...your post is kind of confusing and I can't tell if you've actually installed it or not. If you have installed it already, you can run it with:

```
VirtualBox
``` note: it's case sensitive

---

### Post by nachos99 on 2009-02-26
VirtualBox!! (case sensitive)

haha, so simple.

i did try virtualbox before and it didnt seem to work.  case sensitive like you said.

thanks everyone!

---

### Post by kanikilu on 2009-02-26
I haven't used it, but I think "virtualbox" (lowercase) is for the OSE version...

---


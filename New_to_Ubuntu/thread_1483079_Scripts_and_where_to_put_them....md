---
title: "Scripts and where to put them..."
date: 2010-05-14
forum: New to Ubuntu
---

### Post by ve1drg on 2010-05-14
I am new at using Ubuntu and know nothing about writing scripts..
 
I want to write a script to bring up a telnet function.  And if I can ever find out how to write such a script I have no idea where to put it.  I think it goes in /etc/init.d subdirectory and once there you run 'update-rc.d'.
 
If any of that is correct does this update-rc.d process create the rc5.d files?  Or whereever they go?
 
When I run update-rc.d  I think I have to include the name of the script and its defaults?  What are the defaults?
 
So - what do I have to put in a telnet or ftp etc.. script. I need an example.
And do I put this script in etc/init.d s/dir?
And what are the defaults that I add to the 'update-rc.d' line?
 
Geeeez... I hope this is clear.

---

### Post by slackthumbz on 2010-05-14
Could you be more precise about exactly what you want these scripts to do? Please explain your goal in pedantic detail. It's much easier to help that way :)

---

### Post by ve1drg on 2010-05-14
> **slackthumbz said:**
> Could you be more precise about exactly what you want these scripts to do? Please explain your goal in pedantic detail. It's much easier to help that way :)
 
Well I am not sure what pedantic detail is.  But simply I want to write a script so I will have a certain function.  Like something for ftp, or telnet etc. etc..
What does one of these scripts look like?  Can I see an example somewhere.  Perhaps I just have to look at those files in /etc/init.d s/dir??
And when I do create such a script - do I just put them in that /etc/init.d s/dir and run 'update-rc.d'  using a name and some default figures..(whatever that is..)
 
I can repeat all this but I have no other way how to say what I need.  
Simply put - I want to write a script to get a particular function to work and I need to know where  to put it, and what are the defaults I need to add to the update-rc.d line.?

---

### Post by HermanAB on 2010-05-14
You could put a user script anywhere in your home directory.

If it is a system management script then the standard place is /usr/local/bin

---

### Post by slackthumbz on 2010-05-14
> **ve1drg said:**
> Well I am not sure what pedantic detail is.  But simply I want to write a script so I will have a certain function.  Like something for ftp, or telnet etc. etc..
What does one of these scripts look like?  Can I see an example somewhere.  Perhaps I just have to look at those files in /etc/init.d s/dir??
And when I do create such a script - do I just put them in that /etc/init.d s/dir and run 'update-rc.d'  using a name and some default figures..(whatever that is..)
 
I can repeat all this but I have no other way how to say what I need.  
Simply put - I want to write a script to get a particular function to work and I need to know where  to put it, and what are the defaults I need to add to the update-rc.d line.?

Well for example, if you wanted to automate a procedure straight out of your user account then you should do as HermanAB suggested. Write the script, make it executable and stick it in /home/<your username>/bin. 

The rc is really for system wide services and server daemons. As a user you shouldn't need to play around with those.

If you want to make your script run at certain times then it's also worth learning about cron. Have a look at [this article]("http://www.codewalkers.com/c/a/Server-Administration/Introduction-to-crontab/").

Lastly if you're new to script writing then you may also want to look into the various languages you can use for creating scripts. At the simplest level there's [bash]("http://www.linuxconfig.org/Bash_scripting_Tutorial") but if you want something a bit more featurefull that is installed onto pretty much all *nix type systems by default then you should have a look at [perl]("http://www.perl.com/pub/a/2008/04/23/a-beginners-introduction-to-perl-510.html").

---

### Post by nothingspecial on 2010-05-14
Put it in your path.

Or put it in a directory you make then add it to your path.

For example I have a directory ~/scripts

```
mkdir ~/scripts

PATH=$PATH:/home/username/scripts/ ;export PATH

```

Now all the scripts in your scripts directory can be called from whereever you are in the file system.

---

### Post by slackthumbz on 2010-05-14
> **nothingspecial said:**
> Put it in your path.

Or put it in a directory you make then add it to your path.

For example I have a directory ~/scripts

```
mkdir ~/scripts

PATH=$PATH:/home/username/scripts/ ;export PATH

```

Now all the scripts in your scripts directory can be called from whereever you are in the file system.

But that will only remain the case for your current session, if you log out and log back in again you will have to re-export the path whereas $HOME/bin is already in the default path.

If he wants to permanently add a path he can add PATH=$PATH:$HOME/scripts; export PATH to his .bashrc

---

### Post by nothingspecial on 2010-05-14
Log out!?

Who ever logs out?

Strange notion

You're right though.

---

### Post by slackthumbz on 2010-05-14
> **nothingspecial said:**
> Log out!?

Who ever logs out?

Strange notion

You're right though.

Lol, good point! But he will still have to reboot the system after kernel updates ;)

---


---
title: "Can not log in. Saying home directory is listed as:"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by bitesize1304 on 2011-01-28
I am new to Ubuntu.  I bought a Dell Mini of off a friend and it runs in Ubuntu 8.04.  She gave me her password so I can change stuff.  I had the bright idea of changing the username in useradmin to my own name.  Now that I have done that when I turn it on it brings me to a log in screen. Say her name is Ash and mine is Jodi. I log in with Ash and her password then it says :
 
Your home directory is listd as: 'home/Jodi' but des notappear to exist. Do you want to log in with the/ (root) directory as your home directory? It is unlikely anythign will work unless you use a failsafe session. If I it no it takes me back to the log in screen if I hit yes it gives me another error sayingUser's $HOME/.dmrc file is being ignored.  This prevents the default session and language fro beign saved. File should be owned by suer and have 644 permissions. User's $HOME directory must be owned by user andnot writable by other users.
 
I can not get into my computer now and have no idea what to do.  I know how to get to the GRUB menu I think is what it's called to enter commands but I have no Idea what to enter.  Please help! :(

---

### Post by fabricator4 on 2011-01-28
> **bitesize1304 said:**
> I can not get into my computer now and have no idea what to do.  I know how to get to the GRUB menu I think is what it's called to enter commands but I have no Idea what to enter.  Please help! :(

I don't think that's grub (I hope not!) but a bash shell.  Hopefully all you need to do is make the correct home directory and you should be good.  Get to the terminal and type:

mkdir /home/jodi

and then reboot the machine by typing:

sudo reboot

It should now boot OK, but may be missing a few things since it no longer knows where the application config files are.  You might want to change the username back to ash then log out and back in again using the ash username.

The correct way of doing this was to make a new user with your name and log in using that.  If you make the new user a "desktop" user you won't be able to make any system changes however.

Once you've got it running again you might also consider starting from scratch, as while 8.04 was an LTS release (Long Term Support) it's only supported for three years, which is just about up.  Consider downloading the ISO for 10.04 Lucid Lynx, which is the new LTS release.

You should probably back up any data you want to keep, then start from scratch with your own installation and configuration.  It's not too difficult.

Chris.

---

### Post by [Snc] on 2011-01-28
> **fabricator4 said:**
> mkdir /home/jodi

Remember, that EXT is CaseSensitive!, so '/home/jodi' can coexist with '/home/Jodi'

---

### Post by bitesize1304 on 2011-01-28
Fabricator, I did this comand mkdir /home/jodi and it says cannot create directory /home/jodi

I did go back and when I get the error message it has a capital J for jodi instead of lower case.. so I tried mkdir /home/Jodi and it still says cannot create directory /home/Jodi.

Remember, I am completely blonde to computers so I don't know what everything means. When I get to the terminal it asks me to login as ash... this is what the screen looks like

ash login: ash
password: 

(then it logs me in as ash) and gives me 

ash@ash:/$  

I can not get passed the log in screen.  I log in as ash with her password and it gives me the error about the /home/Jodi directory... and if i try and log in as Jodi... it says wrong log in and makes me try again... like there is no such person! I am so confused about what to do... I should of just left it alone.

---

### Post by fabricator4 on 2011-01-28
> **bitesize1304 said:**
> Fabricator, I did this comand mkdir /home/jodi and it says cannot create directory /home/jodi

Yes, my fault. I should have realised the ash login does not have root privileges.  The way around this is to use super user privileges on a temporary basis.  This is done by prefixing the command you want to use with "sudo". (Super-User DO).  So the commands should be:

```

cd /home
sudo mkdir Jodi

```

Note the capitalization of Jodi.  The normal convention is the username is lower case, and the home directory is the username, however you must have entered Jodi instead of jodi.  

> 
ash login: ash
password: 

(then it logs me in as ash) and gives me 

ash@ash:/$  


The problem is that your login is still ash, but it's now trying to use a home directory of Jodi.

A second problem is that we used sudo to make the /home/Jodi directory, so it doesn't in fact belong to user ash but instead belongs to root (a special user you should learn about by reading)

To give the directory to the ash user do the following:

```

cd /home
sudo chown -R ash Jodi

```

This will give ownership of the Jodi directory to ash.  Now reboot as before and see if gets you over the hump.  Once it's working change the user directory back to ash.

Log out and back in , and everything should work as before.

Chris

---

### Post by bitesize1304 on 2011-01-28
You are a genius!! Thanks a ton.  However.  I have no idea where to go now to change user directory back to ash.  It is a completely different setup.... I'll look around until you reply! Thank you thank you!!

---

### Post by bitesize1304 on 2011-01-28
okay so now i changed everything back to ash.  I rebooted and it took me to the log in screen and it says this now.. User's $HOME/.dmc file is being ignored.  This prevents thedefault session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by suer and not writable by other users. I hit ok and it takes me to this  "Your session only lasted less than 10 seconds  If you have not logged out yourself, this coul mean that there is some instalation problem or that you may be out of diskpsace.  Try ogging in with one of the failsafe sessions to see if you can fix this problem."  so I hit ok and it takes me back to the log in. ahhh.. I don't know what I've done to this poor thing.

---

### Post by fabricator4 on 2011-01-28
> **bitesize1304 said:**
> You are a genius!! Thanks a ton.  However.  I have no idea where to go now to change user directory back to ash.  It is a completely different setup.... I'll look around until you reply! Thank you thank you!!

Things probably look strange because you've lost all the config files.  They still exist, but they are in the ash directory while you are currently using the Jodi directory.

To change the home directory back go to the users settings:

```

System
    ->Admin
        -Users and groups

```

Change the home directory for ash back to ash (NOT Ash), log out and back in again.

Now you can work on setting up your own login.  You will probably want to set up a 'jodi' user with special privileges, NOT administrator privileges. Special privileges can be set that allow the user to use sudo and install new programs, that sort of thing.

There's plenty of documentation in the form of Ubuntu wikis and manuals you should start reading before attempting any system changes.  Try googling for how to set up users under Ubuntu and Linux and see how you go.  When you get really stuck come back and ask us specific questions.

Chris.

---

### Post by Jetso on 2011-01-28
Just a suggestion here. You said that it is running Ubuntu 8.04. That version is no longer supported, so I _***STRONGLY***_ suggest you upgrade. The process is pretty straight forward, but if you need any help, you can post on this thread or make a new one.

---

### Post by fabricator4 on 2011-01-28
> **bitesize1304 said:**
>  this problem."  so I hit ok and it takes me back to the log in. ahhh.. I don't know what I've done to this poor thing.

I don't know either, but we'll find out.  :-)

It seems that either the correct directory was not ash, or that the file permissions have got screwed up along the way, or something else has changed.  Lets have a look at what directories are in /home.

Get to a bash terminal by hitting ctrl-alt-F2

Login in as ash.  Type:

```

cd /home
ls

```

This will list all the directories in the home directory.  Tell us exactly what you see, being careful to note captilisation.

Chris.

---


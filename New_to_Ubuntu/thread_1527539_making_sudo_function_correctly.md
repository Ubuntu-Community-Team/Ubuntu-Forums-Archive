---
title: "making sudo function correctly?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by mancocapa on 2010-07-09
I am new to ubuntu and computers in general
 
I have found myself unable to use the sudo command although I have made myself a root user....when placing a sudo command it then asks for the password and when I try entering this nothing happens the cursor does not even move
 
I need to use sudo to free up disk space....when trying to update I am given the message not enough free disk space on disk '/'
 
Any help with this is appreciated 
 
Gracias

---

### Post by Rubi1200 on 2010-07-09
If you are trying to run sudo in the terminal you will not "see" anything. Just type your password and then Enter.

Unlike other graphical interfaces, the terminal does not show things like asterisk etc.

---

### Post by LowSky on 2010-07-09
the passowrd will not show up when you type it in a terminal.
Just type your password and hit enter.

---

### Post by Devi1903 on 2010-07-09
Why do you need to use sudo to free up disk space. I would not reccommend deleting any files that you do not have the right to delete as a normal user, especially as someone who is new to ubuntu. If you wish to remove installed applications then use the synaptic package manager or ubuntu software centre.

---

### Post by Rubi1200 on 2010-07-09
> **Devi1903 said:**
> Why do you need to use sudo to free up disk space. I would not reccommend deleting any files that you do not have the right to delete as a normal user, especially as someone who is new to ubuntu. If you wish to remove installed applications then use the synaptic package manager or ubuntu software centre.

+1 to this very sensible advice

Here is a link which has some tips for freeing up space:

[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

Read the warning carefully!

---

### Post by mancocapa on 2010-07-09
What would be the average wait time to let the terminal run after using sudo apt-get clean?

---

### Post by Paqman on 2010-07-09
> **mancocapa said:**
>  
I need to use sudo to free up disk space....when trying to update I am given the message not enough free disk space on disk '/'


How much disk space do you have Ubuntu installed on?

You might want to [do a bit of housekeeping]("http://ubuntuforums.org/showthread.php?t=140920") and see if you can free up some space. Your package cache in particular can get quite big, and uninstalling old kernels will free up 100s of MB.

---

### Post by mcduck on 2010-07-09
> **mancocapa said:**
> What would be the average wait time to let the terminal run after using sudo apt-get clean?

I've never seen it take more than a second or two. But you'll know that it's finished when you return back to command prompt.

edit:

"I have found myself unable to use the sudo command although I have made myself a root user"

So have you actually enabled the root account and logged in as root? If you are root, then you don't use sudo. You already have the permission to do anything. (Not that I'd recommend enabling the root account, you don't really need it for anything, in most cases it just makes things more complicated as you need to switch between two users. Not to mention that enabling root login does have some effects when it comes to system security, and also all the support you'll get on these forums will be based on the assumption that you are following the Ubuntu's security model, as in using "sudo" for admin tasks instead of logging in as root)

---


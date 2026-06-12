---
title: "Accidently stuck as root"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by jhargis1012 on 2011-01-22
Hello.

I believe I have accidentally given my primary user account root privileges. At the terminal, my username is listed with a $ after it all the time. Doesn't that usually mean root privileges? It is my understanding that it should be a # out in front.

A few days ago I was messing with user accounts in the GUI and I just checked all the privileges boxes for my regular username. Could this be the problem? If so, I can't remember which boxes I checked. Are there a few that are supposed to be for root only that are making my user name be treated like root? If that's the case, I'd like to restore my account to a normal one.

Thanks for the help.

---

### Post by ubudog on 2011-01-22
Nope, it's opposite.  :)

Nothing to worry about.  As long as typing:

```
sudo -s
```

asks for a password.

---

### Post by uRock on 2011-01-22
No. Here is the difference between root and normal user.

Normal= rabbit@ronnie-desktop:~$ 

Root= [COLOR=Red]root[/COLOR]@ronnie-desktop:~[COLOR=Red]#[/COLOR]

---

### Post by jhargis1012 on 2011-01-22
Ahh, I see. Thanks, guys.

---

### Post by jhargis1012 on 2011-01-22
So, just to confirm, I couldn't have given any of the really powerful root privileges to my normal account in the GUI, right?

---

### Post by ubudog on 2011-01-22
> **jhargis1012 said:**
> So, just to confirm, I couldn't have given any of the really powerful root privileges to my normal account in the GUI, right?

No.  To obtain root, you must type...

```
sudo -s
```
<enter your password>

Anyway, glad it's clarified.  :p

---

### Post by yetiman64 on 2011-01-22
From this link, [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4), I'd suggest the use of "sudo -i" if you use a root shell at any time. It will use root's home and not yours, thus not risking your .ICEauthority files permissions etc. (quite a problem around here at times). It's the only command for a root shell that is not affected by the user's environment variables.

> Here is a summary:
    
 ```
                                         corrupted by user's 
        HOME=/root    uses root's PATH     env vars
sudo -i        Y        Y[2]                 N
sudo -s        N        Y[2]                 Y
sudo bash      N        Y[2]                 Y
sudo su        Y        N[1]                 Y

```[1] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    probably set by /etc/environment
[2] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin 
As is already noted the $ sign as a prompt is for your user, and a # sign is a root shell and will show root@<hostname>.

---

### Post by ubudog on 2011-01-22
Cool, did not know that.  Thanks!

---


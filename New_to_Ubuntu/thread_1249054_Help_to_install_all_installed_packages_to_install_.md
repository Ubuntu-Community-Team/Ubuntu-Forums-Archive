---
title: "Help to install all installed packages to install in my new ubuntu"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by navaneethan on 2009-08-24
Fatal server error:
Server is already active for display 0
If this is server is no longer running,remove /tmp/.xo-lock and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:Resource temporarily unavailable (error no11):unable to connect to x server

xinit:no such process (error no3):server error

I had this error

please give solution

If i need to reinstall my ubuntu means, ihave installed lot of packages in my current one

How do i back-up all? How can i install all packages to my new one?

Please help

---

### Post by pedro3005 on 2009-08-24
You should provide more exact details, but it looks like you're on a tty trying to get to X by 'startx'. Press CTRL ALT F7. If that does not work, I'd recommend rebooting. If that is not possible, 'sudo killall Xorg' then 'startx' I guess.
If that is not your problem, please be more specific about where you get the error, how, and the such.
Oh and you probably won't need to re-install ubuntu (only if you get too lazy to fix the issue :p), but if you're curious, search about APTonCD.

---

### Post by navaneethan on 2009-08-25
> **pedro3005 said:**
> You should provide more exact details, but it looks like you're on a tty trying to get to X by 'startx'. Press CTRL ALT F7. If that does not work, I'd recommend rebooting. If that is not possible, 'sudo killall Xorg' then 'startx' I guess.
If that is not your problem, please be more specific about where you get the error, how, and the such.
Oh and you probably won't need to re-install ubuntu (only if you get too lazy to fix the issue :p), but if you're curious, search about APTonCD.

This is my detail post

  i am using ubuntu hardy,i have installed some packages which is required to me then i have upgraded my hardy using
apt-get upgrade  this command

             some modules have been done and it shows some error for particular module but i can't able identify which one it is,
after restarting my system i can't enter into root login but before i have done it,then i need to enter into userlogin it can't able to start gdm

            i pressing alt+f2 then i logged in terminal mode .then i gave start gdm it doesn't work,i entered startx command it also doesn't work,  it shows the error

[B]Fatal server error:
Server is already active for display 0
If this is server is no longer running,remove /tmp/.xo-lock and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:Resource temporarily unavailable (error no11):unable to connect to x server

xinit:no such process (error no3):server error[/B]

what it means?

how it will be solved?

If i need to reinstall my ubuntu how can i able to install all the packages once again?? **Is any easy way available to install all packages in my fresh ubuntu? or else how to fix this??**

---

### Post by alexlafreniere on 2009-08-25
Are you running the desktop version of ubuntu or the server edition? Have you changed anything recently related to the X server, like your xorg.conf?

EDIT: Strike that last question, you said you upgraded. Did you have any special graphics drivers installed that might have been ruined with the upgrade?

---

### Post by tarps87 on 2009-08-25
Try
Alt + f7
If nothing happens
```
ps -A | grep Xorg
ps -A | grep gdm
```
If these two do not list any thing, then this means the Xorg (graphical) server is not running so

> **navaneethan said:**
> 
Fatal server error:
Server is already active for display 0
If this is server is no longer running,**remove /tmp/.xo-lock** and start again.
[/B]

```
sudo rm -f /tmp/.XO-lock
```

Now

```
startx
```

---


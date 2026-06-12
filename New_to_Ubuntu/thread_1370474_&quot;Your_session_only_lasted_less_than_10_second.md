---
title: "&quot;Your session only lasted less than 10 seconds&quot;"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by GeoffAk on 2010-01-02
I'm really confused.  I turned on my computer and was greeted with a different login screen than I'm used to.  It says "Enter the name of the host and Port you want to log in to."  I enter localhost and press enter.  

```
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details (~/.xsession-errors file)

gdm[3356]: DEBUG: Attempting to parse key string: daemon/Greeter=/usr/lib/gdm/gdmlogin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/etc/gdm/PreSession/
gdm[3356]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[3357]: DEBUG: Attempting to parse key string: xdcm/Enable=false
gdm[3357]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm
gdm[3357]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/local/bin:/opt/X11R6/bin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin:/usr/bin/X11:/usr/X11R6/bin:/usr/local/bin:/opt/X11R6/bin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/Xsession
gdm[3356]: DEBUG: Running /etc/gdm/Xsession /usr/lib/gdm/gdm-ssh-session for geoff on :0
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for localse=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
ssh: connect to host localhost port 22: Connection refused

```I click OK.  It then asks me for the username I want to log in with, so I enter "geoff" and then my password.  It says "Incorrect username or password" :confused: - my password was correct??  It says it will automatically log in after 10 seconds. After 10 seconds it asks me for the host and port again.  Ugh.

I tried to choose "Failsafe Terminal" under "Select Session" back at the login screen.  But it never actually switches to the terminal, maybe because it says my user/pass is incorrect?  I just keep going back and forth between the "Username/Password" screen and the "Enter the name of the host and port..." screen.  I'm never able to actually log in.  Any ideas for this bewildered newbie? :(

---

### Post by Captain_tux on 2010-01-02
What OS are you using?

---

### Post by tom.swartz07 on 2010-01-02
> **GeoffAk said:**
> I'm really confused.  I turned on my computer and was greeted with a different login screen than I'm used to.  It says "Enter the name of the host and Port you want to log in to."  I enter localhost and press enter.  

```
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details (~/.xsession-errors file)

gdm[3356]: DEBUG: Attempting to parse key string: daemon/Greeter=/usr/lib/gdm/gdmlogin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/etc/gdm/PreSession/
gdm[3356]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[3357]: DEBUG: Attempting to parse key string: xdcm/Enable=false
gdm[3357]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm
gdm[3357]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/local/bin:/opt/X11R6/bin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin:/usr/bin/X11:/usr/X11R6/bin:/usr/local/bin:/opt/X11R6/bin
gdm[3356]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/Xsession
gdm[3356]: DEBUG: Running /etc/gdm/Xsession /usr/lib/gdm/gdm-ssh-session for geoff on :0
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for localse=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
ssh: connect to host localhost port 22: Connection refused

```I click OK.  It then asks me for the username I want to log in with, so I enter "geoff" and then my password.  It says "Incorrect username or password" :confused: - my password was correct??  It says it will automatically log in after 10 seconds. After 10 seconds it asks me for the host and port again.  Ugh.

I tried to choose "Failsafe Terminal" under "Select Session" back at the login screen.  But it never actually switches to the terminal, maybe because it says my user/pass is incorrect?  I just keep going back and forth between the "Username/Password" screen and the "Enter the name of the host and port..." screen.  I'm never able to actually log in.  Any ideas for this bewildered newbie? :(

it looks like you computer is trying to log on using SSH, a remote connection protocol.… shouldn't be doing that. 

What were you doing the last time you were on?

---

### Post by GeoffAk on 2010-01-02
Hello :)  I am using Ubuntu Desktop, I think version 9.04.  I wasn't doing anything as far as I remember, maybe doing some recommended upgrades through synaptic.

---


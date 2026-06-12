---
title: "[SOLVED] shutdown without password"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by televisi on 2009-06-07
Resolution located at [HERE]("http://ubuntuforums.org/showpost.php?p=7419223&postcount=15")

Hi All,
I've search through google, and even through this ubuntu forum, but seems all suggestions still not giving me any solution

I'm using Ubuntu server version.

I want to be able to [COLOR="Blue"]**shutdown without asking for password**[/COLOR], this is what I do:
**sudo visudo** and add the following:
```
user ALL=NOPASSWD: /sbin/shutdown
```

Now, I try to logout and log back in, and type
```
shutdown -r now
```
or
```
/sbin/shutdown -r now
```

The above command giving an error message: [COLOR="Red"]**shutdown: need to be root**[/COLOR]

*I think that error message comes up because the shutdown file is owned by root, right? or wrong?*

I try:
```
sudo shutdown -r now
```
or 
```
sudo /sbin/shutdown -r now
```
The above command [COLOR="Red"]**asking me for [sudo] password**[/COLOR]

Anything that I miss here?

---

### Post by mgt_90 on 2009-06-07
You could run "sudo -s" to get a root shell.  You'd need to enter a password to get the root shell, but after that, it shouldn't prompt you.

---

### Post by mrbiggbrain on 2009-06-07
why would you like to do this, maybe if we knew what you where doing we could say how

---

### Post by televisi on 2009-06-07
hi mgt_90,
Er.. the purpose is **shutdown without asking for password**, and by using 'sudo -s' or even 'sudo -i' are not really what I want, if you know what I mean....

---

### Post by _Purple_ on 2009-06-07
Try
```
televisi ALL=(ALL)NOPASSWD:/sbin/shutdown
```

televisi = user
ALL = any host /ip
(ALL) = can run as any user

---

### Post by mgt_90 on 2009-06-07
> **televisi said:**
> hi mgt_90,
Er.. the purpose is **shutdown without asking for password**, and by using 'sudo -s' or even 'sudo -i' are not really what I want, if you know what I mean....

 Any particular reason why you don't want it to prompt for a password? If it's something like a cron job, then can't you get root to run that?

---

### Post by terdon on 2009-06-07
Try ```

username ALL=NOPASSWD:/sbin/shutdown
username ALL=NOPASSWD:/etc/init.d

```

Then run ```
sudo shutdown -h now
```

Seems that shutdown calls processes from init.d so you must have access to that also. See [https://answers.launchpad.net/ubuntu/+question/7998]("https://answers.launchpad.net/ubuntu/+question/7998")

---

### Post by televisi on 2009-06-07
Hi Purple,
I put exactly the same as you suggested then I:
- restart manually the system 
- login back as user
- run **sudo shutdown -r now**
- System still asking me for the SUDO password, strange things?

is it really a big matter to put <SPACE> or <TAB> in combination in between characters?

```
user*<SPACE>*ALL*<SPACE>*=*<SPACE>*(ALL)*<SPACE>*NOPASSWD:*<SPACE>*/sbin/shutdown
```
or 
```
user*<TAB>*ALL*<SPACE>*=*<SPACE>*(ALL)*<SPACE>*NOPASSWD:*<SPACE>*/sbin/shutdown
```


> **_Purple_ said:**
> Try
```
televisi ALL=(ALL)NOPASSWD:/sbin/shutdown
```

televisi = user
ALL = any host /ip
(ALL) = can run as any user

---

### Post by televisi on 2009-06-07
hi terdon, 
Your suggestion still not working :cry: right after I restart the system manually.

This is what I add in /etc/sudoers:
```
user ALL=(ALL) NOPASSWD:/sbin/shutdown, /etc/init.d
```


> **terdon said:**
> Try ```

username ALL=NOPASSWD:/sbin/shutdown
username ALL=NOPASSWD:/etc/init.d

```

Then run ```
sudo shutdown -h now
```

Seems that shutdown calls processes from init.d so you must have access to that also. See [https://answers.launchpad.net/ubuntu/+question/7998]("https://answers.launchpad.net/ubuntu/+question/7998")

---

### Post by aysiu on 2009-06-07
Please don't ever run *sudo -s*. If you want a persistent root prompt, use ```
sudo -i
```

That said, I don't think either will really help you in this case.

If you've done as you said, then you've done everything right, assuming *user* is just a placeholder for your actual username.

In other words, if your username is *televisi*, then it should be ```
televisi ALL=NOPASSWD: /sbin/shutdown
``` and not ```
user ALL=NOPASSWD: /sbin/shutdown
```

---

### Post by terdon on 2009-06-07
Sorry, forgot a change I had made to make it work. Make shutdown executable by your user. Something like:
```

sudo chmod 777 /sbin/shutdown

```

And there is no reason to restart, worked for me just after I made the changes. I also recomend you use ```
 sudo shutdown -h 10
``` or something so it doesn't shutdown on you just as you are trying it out :)

---

### Post by _Purple_ on 2009-06-08
> **televisi said:**
> Hi Purple,
I put exactly the same as you suggested then I:
- restart manually the system 
- login back as user
- run **sudo shutdown -r now**
- System still asking me for the SUDO password, strange things?

is it really a big matter to put <SPACE> or <TAB> in combination in between characters?

```
user*<SPACE>*ALL*<SPACE>*=*<SPACE>*(ALL)*<SPACE>*NOPASSWD:*<SPACE>*/sbin/shutdown
```
or 
```
user*<TAB>*ALL*<SPACE>*=*<SPACE>*(ALL)*<SPACE>*NOPASSWD:*<SPACE>*/sbin/shutdown
```

Hi televisi,
As aysiu has already mentioned, please use your own username instead of user and save the sudoers file. Putting space in between is not necessary. It works fine for me and /etc/init.d is not needed. Did you place the line at the end of sudoers file? Because if you place it above, it will get overwritten. You do not need to change permission of any file either.

---

### Post by terdon on 2009-06-08
_Purple_ : It works for you without the /etc/init.d line? Really? That's weird, I had to add it or it still asked for the password. Strange...

---

### Post by _Purple_ on 2009-06-08
> **terdon said:**
> _Purple_ : It works for you without the /etc/init.d line? Really? That's weird, I had to add it or it still asked for the password. Strange...

terdon, 
Yes, it works. I have checked in both Intrepid and Jaunty.

---

### Post by televisi on 2009-06-08
Yay!!! THANKS!!!
This is the end result:
- Assumed user = televisi
- sudo visudo
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
#%televisi ALL=(ALL) NOPASSWD:/usr/bin/rsync, /sbin/shutdown

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
televisi ALL=(ALL) NOPASSWD:/usr/bin/rsync, /sbin/shutdown

```

Originally I put the **televisi ALL=(ALL) NOPASSWD:/usr/bin/rsync, /sbin/shutdown** line above **%admin ALL=(ALL) ALL**

Apparently this shouldn't be done (as per _Purple_ suggestion).

As this is working for me now, I'll continue my work to use rsync backup using sudo to preserve the file permission as per [http://notepad.bobkmertz.com/2008/04/using-sudo-on-remote-rsync-session-via.html]("http://notepad.bobkmertz.com/2008/04/using-sudo-on-remote-rsync-session-via.html")

THANKS!!!

---


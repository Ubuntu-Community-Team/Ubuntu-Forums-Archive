---
title: "user's $home/.drmc file is being ignored"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by matchstich on 2009-09-14
ok,  i got this error at start up after log in.

User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users. 

tried to follow the directions on here>>>>

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

but,  when i do 

sudo chown username /home/username/.dmrc

i get ----can not access  home/username/.drmc  no such file or directory

did something on here the other day and can not remember what and i started to get these errors this morning.

thanks.

been searching and doing what some folks on here suggested , no joy as yet.

---

### Post by Ms_Angel_D on 2009-09-14
username should be your username as in the one you use to login with, not actually username

Hit ctrl+alt f1

login to the console with your usual name and password then run these commands
```
sudo chmod 644 /home/REPLACE_WITH_YOUR_USER_NAME/.dmrc
sudo chown REPLACE_WITH_YOUR_USER_NAME /home/REPLACE_WITH_YOUR_USER_NAME/.dmrc
sudo chmod -R 700 /home/REPLACE_WITH_YOUR_USER_NAME
sudo chown -R REPLACE_WITH_YOUR_USER_NAME /home/REPLACE_WITH_YOUR_USER_NAME
```

after that 
run this command to reboot your computer

```
shutdown -r now
```

everything should be fine then.

---

### Post by egalvan on 2009-09-14
> **Ms_Angel_D said:**
> username should be your username as in the one you use to login with, not actually username

Or to put it another way...
the parts in [COLOR="Red"]RED[/COLOR] should be changed to **the name you use to log on**...


```
sudo chown [COLOR="Red"]username[/COLOR] /home/[COLOR="Red"]username[/COLOR]/.dmrc

```



As **Ms_Angel_D** wrote... (and mind the spaces)
```
sudo chmod 644 /home/[COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME[/COLOR]/.dmrc
sudo chown [COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME[/COLOR] /home/[COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME[/COLOR]/.dmrc
sudo chmod -R 700 /home/[COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME[/COLOR]
sudo chown -R [COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME [/COLOR]/home/[COLOR="Red"]REPLACE_WITH_YOUR_USER_NAME[/COLOR]
```

---

### Post by matchstich on 2009-09-14
ok,  did not mention it in first post but i did replace 'user name' with my log in name.  

 following instructions from ms agel and egalvan , i did the the ctrl-alt-f1, never saw that screen before , and i put in all commands as shown. what is it?

for the 1st, i got -----no such file or directory

for the 2nd-----missing operand after "usernme/home/username/.drmc

for the 3rd-----cannot access /home/username/.gvf's : permission denied

for the 4th-----missing operand after "username/home/username"

shutdown -R now did nothing so i did ctrl>alt>delete  to get back to log in.

cept after log in that error message did not show up

i logged out again just to check and that error message did not show up.

does that mean all is ok?  also, apologize about taking so long to answer,

my meds knocked me out.  


thanks

---

### Post by drs305 on 2009-09-14
If you no longer see the .dmrc error message on boot, you have fixed that problem.

This guide explains what the commands did to solve .dmrc problems:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=7813405")

---

### Post by matchstich on 2009-09-14
thanks, that is a good thing.  will now mark this as solved.

appreciate y'alls help with this.

---


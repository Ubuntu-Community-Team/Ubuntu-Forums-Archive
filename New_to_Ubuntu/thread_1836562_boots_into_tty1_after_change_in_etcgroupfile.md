---
title: "boots into tty1 after change in etc/group/file"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by gastoj on 2011-08-31
hey after i followed advice to do: sudo nano /etc/group/  and change something there (to fix a no sound problem) my ubuntu boots into ubuntu tty1.. and asks for login and password.. and after i type them it shows kasper@ubuntu:~$

so basically i am stuck now :D .. Could someone please help ?

---

### Post by nothingspecial on 2011-08-31
What did you change?

---

### Post by gastoj on 2011-08-31
[SIZE=2]i added: [/SIZE][SIZE=2]audio:x:29:root:kasper


[/SIZE]

---

### Post by gastoj on 2011-08-31
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i added that line.. (there was nothing else there).. and then saved and rebooted

---

### Post by nothingspecial on 2011-08-31
> **gastoj said:**
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i added that line.. (there was nothing else there).. and then saved and rebooted

There was nothing there ???

Can you copy and paste your /etc/group?

If not and you have a wired connection for that machine pastebin your /etc/group

```
sudo apt-get install pastebinit
pastebinit /etc/group
```

Type the url in a new post back here.

---

### Post by gastoj on 2011-08-31
when i type 
sudo apt-get install pastebinit
pastebinit /etc/group

i get:

[sudo] password for kasper:
and when i type the correct password I get:
kasper is not in the sudoers files. This incident will be reported.

---

### Post by nothingspecial on 2011-08-31
> **gastoj said:**
> when i type 
sudo apt-get install pastebinit
pastebinit /etc/group

i get:

[sudo] password for kasper:
and when i type the correct password I get:
kasper is not in the sudoers files. This incident will be reported.

You may have major problems. Reboot and hold down the shift key. Choose recovery mode and boot a root shell with networking, then try pastebinit again.

---

### Post by gastoj on 2011-08-31
it says <br><br>W:failed to fetch http: blablablablbalba<br>Could not resolve 'us.archive.ubuntu.com'&nbsp; <br><br><br><br><br>

---

### Post by gastoj on 2011-08-31
without the <br>

---

### Post by nothingspecial on 2011-08-31
Do you have a wired connection?

Also try typing, in the root recovery shell

```
usermod -G -a admin kasper
```

Which will hopefully give you admin rights.

---

### Post by gastoj on 2011-08-31
I am connected on that pc trough ethernet cable to a modem (simcard internet).. and the internet works relatively good.. im also using that modem for this laptop.. 

after typing ur code i get:

usermod: group '-a' does not exist
root@ubuntu:~#

---

### Post by saltmarshlamb on 2011-08-31
not that this will help with the issue at hand, but it'll help in future. Use nano with the -B option - it'll create a backup

sudo nano -B /etc/group

Always backup system files you are editing, then you can mv them backup from a recovery session if necessary

---

### Post by gastoj on 2011-08-31
ok thx

---

### Post by gastoj on 2011-08-31
maybe there is a way to fix the etc.group/file ?

---

### Post by nothingspecial on 2011-08-31
Sorry typo, the flags are the wrong way round

```
sudo usermod -a -G admin kasper
```

---

### Post by gastoj on 2011-08-31
after typing that i get group 'admin' does not exist

---

### Post by nothingspecial on 2011-08-31
What does ```
less /etc/group
``` say?

---

### Post by gastoj on 2011-08-31
after googling some, i have created a group called admin and then made kasper part of it using your code.. also now i can login as root using sudo bash.. after going into recovery mode.. and typing your code my screen looks like this:

groups: cannot find name for group ID 0
root@ubuntu:~# less /etc/group
audio:x:29:root:kasper













kasper2:x:1000:
admin:x:106:kasper
/etc/group (END)


//ofcourse the smiley represents  : x  without the space

---

### Post by nothingspecial on 2011-08-31
Well you've managed to overwrite your /etc/group file.

I would say that your installation is toast.

You can wait for a second opinion.

Do you have a backup?

---

### Post by gastoj on 2011-08-31
nope i am total noobie.. :p im stuck in the tty. 
Was there a lot in that file? WHen i first opened it there was nothing exept that.. so.. im thinking of deleting the first line which i have added.. and saving the file.. how can i save it?

---

### Post by sisco311 on 2011-08-31
The backup of the file is called /ect/group-

You might have other backups in /var/backups

---

### Post by nothingspecial on 2011-08-31
There you go, from your root console

cp /etc/group- /etc/group

---

### Post by gastoj on 2011-08-31
yes i found backup files there.. and thye contain alot of these blabla:x:blabla:  so i guess i am saved? [http://ubuntuforums.org/archive/index.php/t-1083487.html](http://ubuntuforums.org/archive/index.php/t-1083487.html)  should i do as he?

---

### Post by gastoj on 2011-08-31
thanks for bearing with me :)  ..  this worked.. hehe working with linux feels good , feel like a hacker

---

### Post by nothingspecial on 2011-08-31
Good to here, breaking your system is fun.

---


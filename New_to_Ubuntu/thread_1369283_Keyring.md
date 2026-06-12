---
title: "Keyring"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Dirkgiggler90504 on 2009-12-31
i have a little problem, how do i turn off the keyring password. I'm getting tired of having to enter my password all of the time. 

Thanks in advance

---

### Post by cartisdm on 2009-12-31
Right click on the icon in your system tray that shows your wireless connection strength.  Then go to Connections, then click the wireless tab.  Then choose the network, click Edit, then click make available to all users.

I'm going from memory, as I am not in Ubuntu right now, so some of those terms might be off but you should get the general idea

---

### Post by melrokz on 2009-12-31
u mean the password box that pops up when u perform an administrative task?

---

### Post by cartisdm on 2009-12-31
> **cartisdm said:**
> Right click on the icon in your system tray that shows your wireless connection strength.  Then go to Connections, then click the wireless tab.  Then choose the network, click Edit, then click make available to all users.

I'm going from memory, as I am not in Ubuntu right now, so some of those terms might be off but you should get the general idea

My apologizes, I thought you were referring to whenever you log in to the desktop you have to type a password to unlock the keyring for your network

---

### Post by Buuntu on 2009-12-31
Type 
```
sudo visudo
```
at the terminal

Change the line that looks like
```
%admin ALL=(ALL) ALL
```
to 
```
%admin ALL=NOPASSWORD : ALL
```

Press <Ctrl> + 'O' to save and <Ctrl> + 'X' to exit, then press 'Y' to overwrite it. (If it edits in nano, which I think it should by default)

After that you probably need to restart for the changes to take effect.  You should realize that this change could be dangerous if you share a machine or if it's not your home PC.

---

### Post by Dirkgiggler90504 on 2009-12-31
Thanks for all of the help but i can not get it to take any of the commands

---

### Post by tenach on 2009-12-31
> **Buuntu said:**
> Type 
```
sudo visudo
```
at the terminal

Change the line that looks like
```
%admin ALL=(ALL) ALL
```
to 
```
%admin ALL=NOPASSWORD : ALL
```

Press <Ctrl> + 'O' to save and <Ctrl> + 'X' to exit, then press 'Y' to overwrite it. (If it edits in nano, which I think it should by default)

After that you probably need to restart for the changes to take effect.  You should realize that this change could be dangerous if you share a machine or if it's not your home PC.

You can also type 
```
sudo gedit
```
and edit the file in a graphical editor, changing the line as Buuntu said.

---

### Post by lisati on 2009-12-31
> **melrokz said:**
> u mean the password box that pops up when u perform an administrative task?

I'd advise against turning **that one** off - try what the others have suggested and let us know how you get on.

---

### Post by Dirkgiggler90504 on 2010-01-01
The window opens up and i can change all to nopassword but it doesn't save or exit

---

### Post by Buuntu on 2010-01-01
If you don't know how to use nano or vi you can use
```
gksudo gedit /etc/sudoers
```
to edit it from a more friendly editor though that is not the recommended way of editing that file.

---

### Post by Dirkgiggler90504 on 2010-01-01
i tried to do it that way but it will not let me change it. here is what it says

Could not save the file /etc/sudoers.

You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.

---

### Post by Buuntu on 2010-01-02
Oh that's right, you have to use visudo...
In that case try using this to edit it: (in a Terminal)
```
export EDITOR=gedit && sudo -E visudo
```
Now you'll be editing the same file just with gedit, a more friendly editor :D.

From: [http://ubuntuforums.org/showthread.php?t=790286](http://ubuntuforums.org/showthread.php?t=790286)

---

### Post by Dirkgiggler90504 on 2010-01-02
i got it. 

Thank you very much

---

### Post by Dirkgiggler90504 on 2010-01-02
now that i have solved that one i am trying to install Mac4Lin_Install_v1.0 and i got all of it installed except for the advent thing on the bottom on the desktop

---


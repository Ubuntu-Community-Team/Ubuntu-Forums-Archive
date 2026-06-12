---
title: "error message on loading ubuntu."
date: 2009-04-02
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-04-02
hi there,

i've ubuntu 8.10. it was working perfectly until yesterday. When i switched on my pc, and just after entering my username and password, i got an error message which read:
**User's $HOME/.dmrc file is being ignored. This prevent the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other user's.**

after pressing 'ok', the message box disappears, and then i can see my desktop.

can anyone please tell why is it that everytime when i load ubuntu i got this error message and what should be done?

---

### Post by Cybie257 on 2009-04-02
Just had that problem myself last night.

Change your home directory to 744 permissions. 644 didn't seem to fix it, 744 did. no more issues.

-Cybie

sudo chmod 744 <homedir>

---

### Post by taurus on 2009-04-02
Boot into recovery mode from GRUB menu.  Then, drop into root shell and run

```
chown -R username:username /home/username
chmod 755 /home/username
chmod 600 /home/username/.dmrc
```
Replace username with your login name.

Reboot.

---

### Post by dwasifar on 2009-04-02
That has happened to me a couple of times too.  Easy fix.

In terminal:

```

cd ~/
sudo chmod 644 .dmrc
sudo chown [yourusername]:[yourusername] .dmrc
cd ..
sudo chmod 755 [yourusername]/
sudo chown [yourusername]:[yourusername] [yourusername]/

```

Obviously, you put your actual username in the indicated spots.  :)

Then reboot, and you should be good to go.

---

### Post by Cybie257 on 2009-04-02
Just in case you are extremely new... 

go to a terminal and do this:

cd /home <return>

ls <return> (to see the name of your home directory)

the do this:

chmod 744 <the name of your home directory> <return>

-Cybie

---

### Post by RajaAjmal on 2009-04-02
i've made thing worst.
i've just read the first reply from cybie and i think i've made a big mistake.
instead of writing this in the terminal
**sudo chmod 744 /home/raja **(i believe this is the right command Cybie) 
i've wrote:
**sudo chmod 744 /home**
and now i got lots of error message when loading ubuntu. after entering my username and password i got this error message:
[B]Your home directory is listed as: '/home/raja' but it does appear to exist. do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.
[/B]
i clicked on button 'yes' from the message box, after which my desktop appears with only the background picture. i can hear the sound as when ubuntu is loading. but there's no upper panel that shows the menu. neither is the lower panel present. there's only the background picture.
if i follow the instructions posted by Taurus, will it solved the problem?
or should i try something else?

---


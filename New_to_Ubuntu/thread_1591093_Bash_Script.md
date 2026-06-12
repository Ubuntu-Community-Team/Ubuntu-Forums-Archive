---
title: "Bash Script"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by k33bz on 2010-10-08
Hey all, I am trying to create a bash script, the commands that are in the script require a password. How do I set it up where it will put in the password, or give me a popup that request my password (prefer this method). That is by clicking on it. I can run it from CLI and it will ask for my password, but not when I click on it. It is already set as an executable file.

---

### Post by llamabr on 2010-10-08
so the script calls for sudo?  change it to gksudo

---

### Post by k33bz on 2010-10-08
ok that will solve some of my scripts. Which is good to know, thank you. But I have two scripts that are similiar to this that also need to be done.

```
#! /bin/bash



#Connect through LOCAL NETWORK:

sshfs 192.168.1.4: /home/keebler/FileServer
```

---

### Post by SuaSwe on 2010-10-08
What is it you want that last script to do?

---

### Post by k33bz on 2010-10-08
> **SuaSwe said:**
> What is it you want that last script to do?

The last script mounts my fileserver as a symbolic link that I can access through my home directory. The command works if I type it all in CLI. or even if I
```
bash local-connect
```
What essentially happens is my computer ask me for my password so it can access the keys to verify that I can connect to my fileserver.

If I type out the command or bash local-connect it will prompt me for the psswd. However if I click on the script and run it, or even run in cli it will not prompt me for the psswd. This is the hurdle I need to cross.

---

### Post by SuaSwe on 2010-10-08
I've never done it but maybe you could adapt Zenity/kdialog to do what you need it to?

e.g. [http://library.gnome.org/users/zenity/stable/zenity-text-entry-options.html.en](http://library.gnome.org/users/zenity/stable/zenity-text-entry-options.html.en)

---

### Post by asmoore82 on 2010-10-09
I think the easiest fix for this is authorizing your public SSH key on the remote server.

```
$ ssh-keygen
$ ssh-copy-id *<user>@<remote-host>*
```

This sets up the remote box to allow your account in without requiring a password.
You can revoke this authorization by truncating or deleting the file "$HOME/.ssh/authorized_keys" *_on the remote server_*.

The only catch to this is that the local private key will be encrypted and
protected by your login keyring. Scripts that need to run unattended or through
any scheduled tasks or cronjobs cannot unlock the keyring on their own.
The workaround for this is to simply not supply a ssh-keygen password and
store your local private key "unprotected" - which isn't really a big deal
unless you are in the habit of loaning out your computer to malicious strangers :D.

---

### Post by k33bz on 2010-10-09
> **asmoore82 said:**
> I think the easiest fix for this is authorizing your public SSH key on the remote server.

```
$ ssh-keygen
$ ssh-copy-id *<user>@<remote-host>*
```

This sets up the remote box to allow your account in without requiring a password.
You can revoke this authorization by truncating or deleting the file "$HOME/.ssh/authorized_keys" *_on the remote server_*.

The only catch to this is that the local private key will be encrypted and
protected by your login keyring. Scripts that need to run unattended or through
any scheduled tasks or cronjobs cannot unlock the keyring on their own.
The workaround for this is to simply not supply a ssh-keygen password and
store your local private key "unprotected" - which isn't really a big deal
unless you are in the habit of loaning out your computer to malicious strangers :D.


My keys are already on the server. To keep things more secure my key is password protected and I really dont feel like keeping my key in an unprotected area.

I have found several scripts like this

```
#!/bin/bash
# sshmount - simple script to mount ssh shares.
echo 'Mounting ssh filesystems...'
sudo -u vserver sshfs -o ro,allow_other vserver@myhome.homeip.net:/share/Music /mnt/slug2/Music/
sudo -u vserver sshfs -o umask=0,allow_other vserver@myhome.homeip.net:/share/vserver /mnt/slug2/vserver/
mount | grep sshfs

bernie@vserver:/usr/local/bin$ sudo cat /etc/sudoers
Password:
--- snipped ---
# This one so that sshfs can be used as user vserver by anyone
ALL     ALL=(vserver) NOPASSWD: /usr/bin/sshfs

```

and several others, some of them are alot longer, including a python script.

---

### Post by asmoore82 on 2010-10-09
> **k33bz said:**
> I can run it from CLI and it will ask for my password, but not when I click on it.

```
password=$( zenity --entry --hide-text --title "Password" --text "password:" )
```
But this can only get the password for you, you'll still have to
supply the password to the program in the script somehow.

---

### Post by k33bz on 2010-10-10
> **asmoore82 said:**
> ```
password=$( zenity --entry --hide-text --title "Password" --text "password:" )
```
But this can only get the password for you, you'll still have to
supply the password to the program in the script somehow.

So if I make the whole script like this:
```
#! /bin/bash

#Connect through LOCAL NETWORK:

sshfs 192.168.1.4: /home/keebler/FileServer

password=$( zenity --entry --hide-text --title "Password" --text "password:" )
```

Will it ask for my password when I click and run the script? Cause really that is what I prefer to happen. Is when I click on it, it runs the command, then prompt me with a pop up asking for my passwd to give permission to verify in my keyring.

---

### Post by piratesmack on 2010-10-10
This will run the command in a new terminal window when clicked so you can type the password

```

#!/bin/bash
# clickable script

#figure out which line the script starts at
LINE=$(awk '/^START OF SCRIPT$/ { print NR + 1 }' $0)
# copy everything starting from $LINE to /tmp/myscript.sh
tail -n+$LINE $0 > /tmp/myscript.sh

# Run /tmp/myscript.sh
exec xterm -e bash /tmp/myscript.sh

START OF SCRIPT
#Connect through LOCAL NETWORK:
sshfs 192.168.1.4: /home/keebler/FileServer

# delete /tmp/myscript.sh:
rm -f $0

read -p "Press ENTER to exit"

```

edit:
Just realized Nautilus gives you the option "Run in Terminal" when you click an executable file.

Sorry, I was using Dolphin

---

### Post by k33bz on 2010-10-10
> **piratesmack said:**
> This will run the command in a new terminal window when clicked so you can type the password

```

#!/bin/bash
# clickable script

#figure out which line the script starts at
LINE=$(awk '/^START OF SCRIPT$/ { print NR + 1 }' $0)
# copy everything starting from $LINE to /tmp/myscript.sh
tail -n+$LINE $0 > /tmp/myscript.sh

# Run /tmp/myscript.sh
exec xterm -e bash /tmp/myscript.sh

START OF SCRIPT
#Connect through LOCAL NETWORK:
sshfs 192.168.1.4: /home/keebler/FileServer

# delete /tmp/myscript.sh:
rm -f $0

read -p "Press ENTER to exit"

```

edit:
Just realized Nautilus gives you the option "Run in Terminal" when you click an executable file.

Sorry, I was using Dolphin

Ok, that script worked flawlessly, except for one thing. It pops up with a white bash shell which does say enter to exit. It also pops up asking for my password. However once I put in my passwd it mounts, like it is suppose to, but when I close the bash shell either by closing it out or by pressing enter, the server gets unmounted. Is there a way to keep it mounted, and close the bash shell?

---

### Post by cavh on 2010-10-10
I think you can do that by appending the ampersand symbol as follows, to run the command in the background:

```
sshfs 192.168.1.4: /home/keebler/FileServer &
```

You could also include the *nohup* command, but I haven't used that myself and so would hesitate to give any further advice - Google should help for the research :P

```
nohup sshfs 192.168.1.4: /home/keebler/FileServer &
```

EDIT: see [http://ubuntuforums.org/showthread.php?t=979929&highlight=ampersand+background]("http://ubuntuforums.org/showthread.php?t=979929&highlight=ampersand+background") for ideas!

---

### Post by k33bz on 2010-10-10
> **cavh said:**
> I think you can do that by appending the ampersand symbol as follows, to run the command in the background:

```
sshfs 192.168.1.4: /home/keebler/FileServer &
```

You could also include the *nohup* command, but I haven't used that myself and so would hesitate to give any further advice - Google should help for the research :P

```
nohup sshfs 192.168.1.4: /home/keebler/FileServer &
```

EDIT: see [http://ubuntuforums.org/showthread.php?t=979929&highlight=ampersand+background]("http://ubuntuforums.org/showthread.php?t=979929&highlight=ampersand+background") for ideas!


Perfect, worked perfect. Thank you again.

---

### Post by piratesmack on 2010-10-11
EDIT: cavh beat me to it

---

### Post by careertargetph on 2011-02-07
I also encountered this kind of problem last week. Because of this I can fix it.

---


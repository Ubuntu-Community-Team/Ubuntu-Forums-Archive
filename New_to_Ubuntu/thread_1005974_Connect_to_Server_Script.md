---
title: "Connect to Server Script?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mjheagle8 on 2008-12-08
I am able to connect to two servers via ssh and samba. Is there any way I could make a script to automate this process instead of having to type in the data each time?  
I thought i could bookmark it, but i cant be constantly connected, and that makes my places menu switch from showing all the bookmarks to having a bookmarks drop down menu.

---

### Post by anim on 2008-12-08
Create a text file called .bash_aliases in your home directory. Open the file (you may have to hit Ctrl+H to see hidden files) and create an alias for the command. For example you could write:

```
alias connect2server = 'command1;command2;command3' 
```

Then all you would have to do is type in connect2server the next time you enter terminal and all those commands would be run in order.

For example, I have a script in mine that changes to the folder for one of my games, then executes that game, then returns the prompt to the home folder. That looks like this in my .bash_aliases file:
```
alias nwn='cd /home/username/games/nwn/;./nwn; cd~'
```

A new command in signified by the semicolons, so it is as if I typed each command into a separate terminal line. You can use whatever commands that you use to connect to your server in much the same fashion, just separate them by ; and you are good to go.

Note: You'll have to enter the command
```
$:source .bash_aliases
```
after you update the .bash_aliases file before your aliases will work.

Let me know if you have questions.

---

### Post by mjheagle8 on 2008-12-08
thanks for your help. what would i use for the commands ('command1, command2, command3') to connect to the servers?
one of the servers is a samba, one is ssh.
when i tried the command:
```
mike@mike-laptop:~$ $:source .bash_aliases
```

i got:
```
bash: $:source: command not found
```

---

### Post by albinootje on 2008-12-08
Sounds like you're using Nautilus to connect normally.

You could try something like this in a terminal as a start :
gvfs-mount ssh://username@fileserver for ssh
gvfs-mount smb://username@fileserver/share-name for samba

Unfortunately documentation for gvfs-mount doesn't seem straight-forward to find.

For transparent use of ssh the package sshfs is interesting.
After installing sshfs, see : man sshfs for the syntax.

---

### Post by anim on 2008-12-08
Just type
```
source .bash_aliases
```

I meant to put in ~$ because that is the prompt signifier. I'm sorry.

For some reason I assumed when I read your original post that you were using the command line to make those connections and already knew the commands. Unfortunately I don't, sorry :oops:. Perhaps someone else will be able to assist you with the commands necessary, or knows a GUI solution.

---

### Post by anim on 2008-12-08
Here a nice (although a bit out of date) guide to shfs. Perhaps it will help.

[http://www.zdnetasia.com/techguide/opensource/0,39044899,39370301,00.htm](http://www.zdnetasia.com/techguide/opensource/0,39044899,39370301,00.htm)

---

### Post by mjheagle8 on 2008-12-08
i got it working! thank you for all of your help!

---


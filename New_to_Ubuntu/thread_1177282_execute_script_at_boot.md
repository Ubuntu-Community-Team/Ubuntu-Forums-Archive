---
title: "execute script at boot"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by benfindlay on 2009-06-03
Hi all, I've done some searching for this, but I have to admit I am a little mistified regarding usage and how to actually accomplish the task. Here's the situation:

I have a bash script currently in my home directory that launches a program which I then connect to via web browser pointed at localhost. The bash script just runs the program, which is sitting in a subdirectory of my home folder, and looks like this:

```
#!/bin/bash
./bootprogdir/bootprog
```

I would like to know if there is a way to configure this program to run automatically when the machine is powered on. I am using ubunu server edition, so can't add it to Sessions within System >> Preferences.

Thanks

Ben

---

### Post by Celauran on 2009-06-03
Add it to /etc/init.d

---

### Post by benfindlay on 2009-06-03
Thanks for the reply.

By that, I take it you mean just copy the file into that directory? If I do that, are there any issues with needing permissions to run the command?

Thanks again

Ben

---

### Post by Bölvaður on 2009-06-03
System &#8594; Preferences &#8594; Sessions
put the command to execute your file in command, and some fitting name for name.

change permissions of the file where the script is contained to be executable for you.


btw this is only if you do not need root. Scripts which do not require root should not be run by root and should be kept as separate from it as possible.

---

### Post by benfindlay on 2009-06-03
Hi, I can't put it in System>Preferences>Sessions because I am running ubuntu server, so I don't have a GUI installed. Also wouldn't that only make it work following log in? What I am trying to achieve is for it to automatically execute during bootup, requiring no intervention (such as logging in) from me whatsoever

Thanks

Ben

---

### Post by =CelticRaven= on 2009-06-03
add it to /etc/init.d is probably easiest as stated above.

I think you just need to do the following:

cd ~
sudo cp YOURSCRIPTNAME /etc/init.d
sudo chmod +x  /etc/init.d/YOURSCRIPTNAME
sudo update-rc.d YOURSCRIPTNAME defaults

btw you may need to change the contents of your script file to have the full path, i.e. instead of 
  ./bootprogdir/bootprog

you might need
  ./home/YOURUSERNAME/bootprogdir/bootprog

---

### Post by The Cog on 2009-06-03
I think the normal thing to do is to put your script into /etc/rc.local. 

For instance, assuming:
* your username is benfindlay
* your launcher script is /home/benfindlay/myscript/begin
then add a line like this to /etc/rc.local:
```
su -c '/home/benfindlay/myscript/begin' benfindlay &
```
which runs your script in the background under your id.

---


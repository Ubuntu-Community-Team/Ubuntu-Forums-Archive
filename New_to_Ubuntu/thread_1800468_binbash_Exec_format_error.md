---
title: "/bin/bash: Exec format error"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by Ballzac on 2011-07-09
Hi,

I have a computer running Ubuntu server 10.04. So I tried writing a bash script for the first time. It looked simple enough to do. It only had a couple of lines, and they were simply commands that I normally use in the terminal. I just wanted to save myself from writing the same lines over and over while I was testing something out. Anyway, I was doing this via ssh on another computer, and when I logged out and logged back in again, I got

```
/bin/bash: Exec format error
```

I tried logging in on the machine itself, and get the same error. It is the only login other than root on the machine, and I don't know what the password is for root. On another machine my normal password works for root as well, so I don't know why I can't log in as root to at least try to set up another account. I don't even know if this would work, but I have a suspicion that it's trying to load bash from the path that I had the script in. I didn't really want to mess around with changing the path in .profile, so I was running the script simply by putting it in a directory and then running it from that directory by typing

```
./script
```

I thought maybe the problem had something to do with the .profile file, so I tried to rename the .profile file so that the system would ignore it (I did this via nautilus on my other machine because all the shares are mounted okay), but doing so deleted the file for some reason. I had previously looked at it, so I got a .profile off another machine and it looked the same, so I copied it over and tried logging in again. Still no dice. I have no idea if this could even be the problem. I don't know much at all about bash (clearly). If I even suspected that writing a script could cause problems then I wouldn't have even bothered at this point in time.

I have searched regarding the error message, but it seems it can be the result of a variety of problems, and as I have no idea why it occurred, I don't know what advice to take. I can log in via rescue mode on the cd, but don't know how to fix it. And I'm sure you all know it's a bit of a pain running rescue mode because you have to set everything up on it each time you run it, so if I try this or that and then reboot and try to login booting from hard disk, it's a PITA if it doesn't work and I have to setup the rescue CD again.

I could easily reinstall from scratch, as I have my home directory on a different partition, but there's a fair amount of setting up for me to do, and I'd rather fix this and learn from it. Also, if the .profile file (or one of the other configuration files in my home directory) DOES have some part to play in why this isn't working, it might still be an issue after reinstalling and mounting my /home partition, unless I setup a new login on the new install.

Hopefully someone out there can spot what the problem is. Thanks for your help. :)

---

### Post by linuxman94 on 2011-07-09
Can you please post the script itself in code tags?

---

### Post by Ballzac on 2011-07-09
I can't post the exact script because I renamed it the same as I did with the ./profile file and it also vanished. But it was basically this (probably verbatim).

```
 #!/bin/bash
echo password | sudo -S chmod -R 777 /home/ballzac/path1
echo password | sudo -S mv /home/ballzac/path1/* /home/ballzac/path2
```
where "password" is my password and "path1" and "path2" are two paths on my system. I had previously run
```
which bash
```
to know what path to put as the first line. I know putting the password in the script is a bad way of doing it, but I was only planning on using it while I was troubleshooting something, so wasn't too worried about security. I was using it by typing

```
./script
```

mostly, but also using

```
nohup ./script &
```

at times.

---

### Post by linuxman94 on 2011-07-09
I would just remove the echo password lines and the sudo and then just run the script with sudo.

So the script would look like this:
```
#!/bin/bash
chmod -R 777 /home/ballzac/path1
mv /home/ballzac/path1/* /home/ballzac/path2
```

And you would run it like this:

```
sudo sh ./script
```

---

### Post by Ballzac on 2011-07-09
Is that going to fix my problem? Or are you just saying that's how I should have run the script when I was using it? I don't care about the script anymore. I just want to be able to boot into my system.

Thanks for the help.

EDIT: That should have read "login to my system", it boots fine. I just can't do much because all I have access to is the samba shares and I can use transmission via remote-gui, but that's it.

---

### Post by linuxman94 on 2011-07-09
Yes that should fix your problem. Oh and can you boot into your system?  You made it sound like you couldn't.

---

### Post by Ballzac on 2011-07-09
Ah, cool. I'll try that then. Yeah, I edited my last post before I realised you'd replied again, that explains a bit about logging in etc. I'll have to use the live cd to run the script.

---

### Post by linuxman94 on 2011-07-09
Ahh i see.  Well don't hesitate to post back if you encounter problems!  And mark your thread as solved so others can benefit.

---

### Post by Ballzac on 2011-07-09
Sorry for my ignorance, but can I just delete the two lines in it and run it with only the #!/bin/bash line? I'm assuming it's just running this particular line that will fix the problem? Like I said, I really have no understanding of bash. Thanks again.

---

### Post by linuxman94 on 2011-07-09
You could do that, but the script would do nothing! :lolflag:

#!/bin/bash tells the system to use the bash interpreter when you execute the script.  It doesn't actually execute a command.

Edit: What exactly is the problem you're trying to fix?

---

### Post by Ballzac on 2011-07-09
Yeah, but I'm not acutally interested in chmodding or moving any files anymore, so if I leave those lines in, I'm going to have to put an empty file or something in that directory just so I don't get an error when I run the script. Also, I'll have to change the paths to /target/home... as that's were it's mounted when I use the live cd. I really don't understand how this is going to fix my system, so I assumed that it must be the #!/bin/bash line. How is running chmod and mv going to fix my system? And if they do, can't I just run them from the command line?

---

### Post by Ballzac on 2011-07-09
> Edit: What exactly is the problem you're trying to fix?
When I try to login with my account, I get 
```
/bin/bash: Exec format error
```
and it doesn't let me in. I can't do anything other than access my smb shares and transmission if I can't login. I just want to be able to login.

---

### Post by Ballzac on 2011-07-09
So yeah, I'm pretty skeptical that running a chmod and mv command in a script is magically going to fix my system. I'm thinking maybe I didn't explain what the issue is clearly enough and you misunderstood or something. Unless you can explain to me how this will work, I'm probably just going to try to copy some configuration files (fstab smb.conf, etc.) to my /home partition if I can, and reinstall the operating system.


EDIT: So I got it all up and running pretty quickly with a reinstall, but it's a shame I still don't know why the problem occurred in the first place. I would like to learn how to write bash scripts, but I'll think I'll mess around on a test machine first, lol. I'll leave this thread as unsolved so that other people looking for a solution to this problem don't get the wrong idea and think I got it fixed without reinstalling.

---


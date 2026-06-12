---
title: "SSH Cron"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by justin1812 on 2007-11-24
Hi 

I'm attempting to connect to a remote machine running openvms from ubuntu using an ssh command in cron. When i execute the command from a terminal it works withour error. Altough when I put the command into cron it fails. The command I'm running is as follows

/usr/bin/ssh -i /home/user/sshkey -l username node  dir >/home/user/Desktop/file.txt

I have added the -o batchmode yes option. I have created a bash script with this command in it. Aswell as a perl script with this command in it they both run fine when called from the terminal but fail when called by cron. 

I have also ran whoami and cron and piped it to a file. It's running with the correct user account. 
 
OpenVms uses ssh2 but i have converted the format of the key. It works fine through the terminal but not in cron so I don't think the key format should matter. 

Any Help would be great I need to do this and am at a loss here. 

Thanks

---

### Post by kevdog on 2007-11-24
Sounds like a permissions problem.  Is this a personal or system wide cron job???   If you run a similar cron job but put something like 

ssh localhost 

does it work??

What are the permissions for your sshkey?  Im not sure if the owner of the cron process would have access to your key.  Although cron is using your personal crontab file, I not sure if it is being run under your personal username or using your personal permissions.

---

### Post by justin1812 on 2007-11-24
Thanks for the help 

It will run successfuly when i run it as root aswell. the permissions are 
-rw-r--r--. I did try to change this but once its changed the server won't accept the key once its changed.

---

### Post by kevdog on 2007-11-24
So the script will run, however the login will not work??

---

### Post by justin1812 on 2007-11-25
When I pipe the output from when it runs in cron ssh logs in okay but the command never gets executed on the server.

---

### Post by kevdog on 2007-11-25
So ssh will login, but you are not able to execute any commands.  Just a suggestion, do you have read-only capabilities?  For example in your script if you login to the remote computer and you do a ls -la > server-test.txt, does this give you any output??

---

### Post by justin1812 on 2007-11-25
Thanks for the reply

When I attempt to execute ls -la the command still doesn't get executed on the server. Authentication is successful but the command never gets executed.

---

### Post by kevdog on 2007-11-25
This is super annoying!!  I'm assuming you have this working as a personal cron executable -- or using your personal crontab file to get the script to execute.  Can you try setting up a system-wide crontab file?  Ive done this once, but for the life of me can't figure out where I found the documentation.  It was fairly easy.  My ubuntu machine -- my old dell inspiron 5000e laptop -- the monitor is about to fall off its hinges -- so I dont really have access to the machine to give you the specifics.

---

### Post by justin1812 on 2007-11-25
yah I can try to set that up I don't have access to that machine until tommrow as it's not in my house. I was also thinking about creating the key pair in a script called by cron. On second thought though I don't know if that is possible as input is required for the paraphrase.

---

### Post by kevdog on 2007-11-25
one other suggestion -- well I guess it might not work -- but did you try putting a sleep statement in for 60 seconds or so in between the login statement and the next statement.  Does the connection terminate during the sleep statement or with the execution of the next statement?

---

### Post by justin1812 on 2007-11-25
Thanks for the suggestion I will try that aswell.

---


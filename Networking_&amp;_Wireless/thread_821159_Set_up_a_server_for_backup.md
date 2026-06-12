---
title: "Set up a server for backup?"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by edd07 on 2008-06-06
Hello. I have a somewhat old computer hanging around unused, so I started thinking what I could do with it. I've decided I'll use it for backups and maybe some experiments (muahaha), but when it comes to networking, I'm pretty much a noob.

What would be the best way to set this thing up? I'm planning on installing the Server edition, so it'll have no GUI, and if I could do everything remotely, it would be great. What should I do? FTP server? Samba share?

Thanks

---

### Post by superprash2003 on 2008-06-07
you could set it up like a gateway cum backup server.. and have all your main data like music,snaps,movies and other data onto this server and share it via samba .. so that it can be accessed by any pc on the network.. if you want to access your files from the internet then ftp server.. if your interested in having a webserver you could install apache..

---

### Post by SpaceTeddy on 2008-06-07
i use ssh+rsync+rsnapshot+samba.

In detail, i have a server with big hd capacity that just lurks around and does nothing but holding backup files. 
Every night, the clients connect to it and rsync their files to the server. Then, later, the server runs rsnapshot on the newly synced files and builds a revision hive out of it. This hive is then shared via read-only shares with samba. 

On the server side, setting up openssh, rsnapshot and samba is pretty easy. That should not prove to be any problem at all. On the client side, you can use native rsync and ssh if you have an ubuntu client, or cwrsync and nncron if you use a windows client. 

As a totally different idea - use bacula. But i have no idea of working or installing it. Never did anything with or to it, 

Sorry for not being more helpful. I can probably help you with the first setup, but right now i am too tired to type it out :(

hope it helps (a little) :)

---

### Post by edd07 on 2008-06-07
> **SpaceTeddy said:**
> i use ssh+rsync+rsnapshot+samba.

In detail, i have a server with big hd capacity that just lurks around and does nothing but holding backup files. 
Every night, the clients connect to it and rsync their files to the server. Then, later, the server runs rsnapshot on the newly synced files and builds a revision hive out of it. This hive is then shared via read-only shares with samba. 

On the server side, setting up openssh, rsnapshot and samba is pretty easy. That should not prove to be any problem at all. On the client side, you can use native rsync and ssh if you have an ubuntu client, or cwrsync and nncron if you use a windows client. 

As a totally different idea - use bacula. But i have no idea of working or installing it. Never did anything with or to it, 

Sorry for not being more helpful. I can probably help you with the first setup, but right now i am too tired to type it out :(

hope it helps (a little) :)
Thanks, this sure helps; it sounds exactly like what I had in mind. Bacula looks awfully complicated, though, so I guess I'll stick with the ssh+rsync+rsnapshot+samba combination.

I'll do my research on these things, but if you have some tips, they'll be greatly appreciated.

Thanks again

---

### Post by SpaceTeddy on 2008-06-09
mhm... k

i've never really written this down, so i'll try to remember everything i did :)

[SIZE="5"]1.) install the software[/SIZE]

this command should get you started in installing all you need for the server. we will only worry about the server for now and leave the clients alone.
```
sudo apt-get install rsnapshot rsync openssh-server samba
```


[SIZE="5"]2.) Getting to know the directories[/SIZE]
You need to have a directory per user that does the backups. Where you store that is your decision. I usually have a backup point per user in /var/backups/user where the big drives are mounted. but you could also use the homedrives or somewhere entirely different. for simplicity reasons, i will assume now that you are going to use the homedrives of the user, and that /home is where you mounted the big storage capacity.
Another imporant directory is the ~/.ssh dir. This is a folder in each home direcory that will contain the private and public key to access the backup storage so that the computers that do the backup can write to the server. But we will get to that aswell. 
Lastly, i'd like to point out the /etc/openssh/ folder where the config of the openssh-server lives, the /etc/samba folder where the config of samba is placed and /etc/rsnapshot.conf which is the configuration file of rsnapshot.

please check that all dirs and files exist (except ~/.ssh which we are going to create in the next step) and check that you can at least login via ssh to the server. The standard configuration should let you do that. Samba still need some configuration, but can probably be access by now too.

[SIZE="5"]3.) passwordless login for machines[/SIZE]
first and foremost - NEVER use the root account. create a new user account which a user/machine should use. This can be either done via the gui or the "adduser" command (if you use adduser, don't forget the -m for creation of the home dir). Once the user is created, log in as that user. In their home dir (usually /home/%username%) and create a direcroty called .ssh. Then go into that dir and generate a pair public/private keypair for that user with this command:
```
ssh-keygen -t rsa -b 2048
```
for the filenames just press enter. Once that is done, rename the file rd_rsa.pub into authorized_keys. Now, any client that holds the id_rsa file will be able to log in as that user without being asked a password ! So make sure, NOBODY ever gets that file unless you want them to.

[SIZE="5"]4.) setting up the ubuntu client[/SIZE]
so - we have a server running that we can shove backups to. On an ubuntu machine, all we need is one command per directory and we are done. But first, make sure that the ubuntu hast rsync as well as the openssh-client installed.
```
sudo apt-get install openssh-client rsync
```
once that is done, this is the generic command to run if you want to mirror something onto the server:
```
rsync -ruv --delete -e "ssh" /path/on/local/machine/ username@example.server.net:/path/on/server/for/backups
```
run that command first from the commandline to see if it works. If it does, then remove the v from it (v is for verbose - if you want to keep the output, then leave it in) and add the command to your crontab via this command
```
crontab -e
```
i ususually run my backup at 22:00 every day (a time where i rarely work, but mostly do something else with the comp... like answering posts on ubuntuforums.org). As an example, the full line to be added looks like this:
```
0 22    * * *            rsync -ruv --delete -e "ssh" /path/on/local/machine/ username@example.server.net:/path/on/server/for/backups
```

viola - you have a mirror of your machine. If you need to backup two dirs, just add two lines. just make sure that the destination folders also don't match.

this is all i can write for now, as i am already low on time again. Next time (if there is such a thing) i will talk about setting up the windows client and doing the shared in samba.

hope it helps :)

---


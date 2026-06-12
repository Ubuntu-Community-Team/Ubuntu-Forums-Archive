---
title: "rsync syncing issues. Unable to send large directories of files."
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by Michael_A_Garner on 2014-02-05
Hello fellow Ubuntuers,

I apologize if this is isn't quite the right section for this type of issue, but I am new to the forums and wasn't quite sure which category this belonged in.
-BEGIN-
I am trying to sync a the files contained in a samba share located on a Ubuntu 12.04LTS machine to a remote repository contained on an Ubuntu Server (11 or 12? Latest LTS)edition server. I have installed rsync and updated it on both machines. I am running the following command to try to accomplish this task:
```
rsync -azvr /home/REPOSITORY -e "ssh -p [PORT #] -i [KEYNAME&LOCATION]" [usernamel]@[SERVERADDRESS]:[REMOTE DIRECTORY]
```
This command then begins to work (so it seems) with the following:

sending incremental file list
FILES/
FILES/file19238749879asdfjh

It then hangs here for hours and does nothing else.
The directory it is syncing is about 60GB so not outrageous, but quite large and there are some files which are in the 50-60MB size range with one in particular that is 1GB. 

I have run this command several times overnight hoping to see better results in the morning and wondering if it is just taking a long time to transfer the whole directory because it is decently large and the internet connection on the transferring side is about 1.5mbps upload, but everytime I check on it the connection eventually times out and when I check the remote directory's size with the du command it isn't any bigger, or at least insignificantly bigger.

It seems to have created the directory tree just fine, but most of the directories are empty.

Any ideas on what the problem could be?

Requirements are that it must use an alternative port for SSH and also a key file for connection to the remote repository. Password configurations are not accepted. The ports could change if that is really the issue.

---

### Post by TheFu on 2014-02-05
Please post the EXACT command, because the one above won't work.
ssh is the default mode for rsync. No need to specify it.
Does ssh into the other machine work?
Are you using a ~/.ssh/config file to handle the alternative port and userid for ssh?

I use rsync to mirror videos all-the-time. Here is the ENTIRE script:
```
#!/bin/bash
SRC=/export/dvds/
TARGET=hadar:/misc/dvds
rsync -avz --stats --progress --delete  $SRC/* $TARGET
```

---

### Post by Michael_A_Garner on 2014-02-06
```
[COLOR=#000000][FONT=Ubuntu Mono]rsync -azvr /home/videos -e "ssh -p 29458 -i /publickey" user@server.com:/remote/directory[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

SSH works just fine on alternative ports. I mostly use Putty to connect to machines and so I just specify ports there. Yes I modified the ssh config file to use an alternative port. SSH to both machines works flawlessly and I can also ssh between the machines. This is not for a LAN rsync, but rather a WAN rsync. I have filled the above command with bogus information, but the idea should be pretty straight forward. I am using the ssh command with rsync because I am specifying the port to use as well as a key file to use when connecting to the remote machine. Hence the -p and -i flags respectively with the ssh command. Ideally I would have something as simple as your example, but I must use an alternative port and public key authentication with the remote.

EDIT:
Sorry, I misread that. I don't believe I have setup a config file on the remote. I am using the router to handle the ports. I send it to port XXXXX and the router puts the traffic through port 22. The remote shouldn't notice a difference right?[/FONT][/COLOR]

---

### Post by papibe on 2014-02-06
Hi Michael_A_Garner.

You're missing a ":
```
rsync -azvr /home/videos -e **"**ssh -p 29458**"** -i /publickey user@server.com:/remote/directory
```
Also, I recommend using the option -P ( which implies both --partial and --progress) so you can see if something is being transmitted and also at what speed.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Michael_A_Garner on 2014-02-06
I realized I missed that in my code sections above and have edited it accordingly. In my actual command that I was running I did have the ending quote. What command does the -P flag pertain to? rsync or ssh?

---

### Post by TheFu on 2014-02-06
No need for the -i option and if you setup the ~/.ssh/config file on the source machine (where you run the rsync on), then all the -e stuff goes away. Trust me, learn it, use it, love it. [http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication)

---

### Post by Michael_A_Garner on 2014-02-06
Oops. Should that ending quote be right after the port or should it wrap all the way around the public key section too?

---

### Post by Michael_A_Garner on 2014-02-06
Ok. So the transfer is working, but it is transferring at a rate of about 78KBps. The file it is getting stuck on everytime is 1GB. Is there a timeout for rsync? And what happens if the transfer is interrupted in the middle of a file transfer. Will it continue where it left off on that file the next time you run the command or will it delete the partial file and start over? If it deletes the partial file then I think it may just be a situation where it is timing out and thus I keep trying to transfer the same huge file over and over and it times out and that is why I'm not seeing progress. Could that be it? Thoughts?

---

### Post by Michael_A_Garner on 2014-02-06
Found really nice documentation for rsync. Posting this here for others who may have similar issues. Big thank you to @papibe for the -P flag hint. It shows file transfer progress in real time and also allows for the saving of partial files in the event of a disconnect. If you are transferring large files this flag is a must. The reason mine kept failing to transfer everything is because it was repeatedly transferring a portion of a 1GB file, timing out, and then starting over whenever I ran the command. With the -P flag my problems should now be solved. Thank you for the tip.

---


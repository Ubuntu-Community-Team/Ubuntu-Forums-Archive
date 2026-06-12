---
title: "Cannot write files to another Linux computer"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by MacDuff on 2007-07-25
I have a network consisting of a Ubuntu machine, a Windows XP machine and a dual boot laptop.

I can connect the XP machine to the Ubuntu with no problem and I can read files on the Ubuntu computer from the Laptop booted in Ubuntu but I cannot write to the files on the Ubuntu box.

I have set up the user of the laptop as a user in the Ubuntu Box.  The files on the Ubuntu box are shared.

What am I missing to be able to write to the Ubuntu computer?

---

### Post by punx45 on 2007-07-25
if you are using NFS between the two machines it is most likely because the user ID and group ID (UID and GID) numbers mismatch, despite the user names being the same.

you should be able to find out the UID and GID of the user on each machine with ```
id -u username
id -g username
```

it looks to me like changing the UID is a little complicated[COLOR="Red"]*[/COLOR], so instead we can edit the /etc/exports so that all connections are assumed to be the same person.
[B][I](NOTE: this is safe, assuming the networked computers bleong to and are used by yourself, and possibly friends/family that you trust, and that there are either no remote users (outside the house) or any remote access is sufficiently protected.)
[/I][/B]
on the machine hosting the files in question:
make a backup of /etc/exports, then open it in an editor.

add the paramaters 'all_squash,anonuid=xx,anongid=xx' inside the parenthesis with whatever else is there.
where xx= the UID/GID of the user on that machine.

restart NFS:
```
sudo /etc/init.d/nfs-kernel-server restart
```

now you should have the same read/write privileges of the account you created on that local machine with whatever other machine you connect from with NFS.

hope that wasnt too confusing!

this is from memory, i dont have access to my machines or a terminal right now, so if I am off somewhere I apologise.   corrections are welcomed.

see man exports for more information, and examples.

and finally, see here [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) for lots more information on installing and configuring the NFS service on ubuntu.
___________________
[COLOR="Red"]* apparently i was looking in the wrong place.  see man usermod for details![/COLOR]

---

### Post by MacDuff on 2007-07-25
Thank you punx45.  That seems clear to me.  Your reply is well written  with enough background to make it easy for a newbie like me to grasp.

I will try it out tomorrow and see how it goes.

Cheers

Mac

---

### Post by MacDuff on 2007-07-25
Could not wait.  Had to try your instructions out so booted up the Ubuntu Box

The instructions:
  " you should be able to find out the UID and GID of the user on each machine with
Code:
id -u username
id -g username"

did not work.  I just received a reply "No such user" to both of them, so what little thing am I missing.  Please remember that I know virtually NOTHING about Linux and steps that you and other experienced users might take for granted are completely unknown to me.

Is there an "accepted" way to back up a file before editing or should I just make a copy of the file somewhere? Because the first step did not work, I did not have the nerve to proceed to the second step.

Sorry for my extreme ignorance.

Mac

---

### Post by punx45 on 2007-07-25
in id -u username, substitute 'username' with the actual username on your system.
such as for myself:
```
id -u punx45
```



the easiest way to make a backup when using the command line is to copy the file.
copy works like this:
```
cp <original_file> <new file>
```

or in real terms
```
cp /etc/exports /etc/exports.backup
```

for a file like /etc/exports and the directory /etc you would need administrator privileges to modify/create files, so add 'sudo' at the beginning of the line.
```
sudo cp /etc/exports /etc/exports.backup
```

---

### Post by punx45 on 2007-07-25
are you having trouble writing files while in XP, or Ubuntu, or both?

---

### Post by MacDuff on 2007-07-26
Thanks for the clarification punx45.  I should have reaiised that I should substitute my own username for the word "username" but I thought that it would report a username which I would then set up on the other machine.    See what I mean about a different point of view for a Windows user?

 As to your question regarding having trouble writing from just the dual boot machine or both it and the XP machine, the answer earlier today would have been:  No trouble writing from the XP machine, just trouble writing from the Ubuntu dual boot machine, but after messing about following your ealier post, I could not even see the files on the Ubuntu box from the XP machine, let along write to them.  I am not sure how long it takes to establish a network connection after boot-up though so it may be that I quit too soon. 

 I find this struggle to get everything working to be very tiring because I have to keep up with my regular work as I mess about with Linux.  It is becoming clear why others have told me that they just gave up on Linux because of the obscurity of getting everything to mesh.

I may have some time tomorrow to play around again with Ubuntu, but I am trying to get caught up on my my work so I can take a couple of weeks off.  Maybe after I have cleared my head I will make better progress.

Thank you for your help.  If it were not for the assistance of people like you, I would have given up weeks ago.

Mac

---

### Post by punx45 on 2007-07-26
I hear ya on the busy part! i cant tell you how many hours have been absorbed by reading, tweaking, more reading, and so on.
happy to help! glad you havent given up!

---

### Post by MacDuff on 2007-07-27
I still cannot write to an ubuntu box.  I guess I have not mastered the terminal language but who has time to commit all that to memory when trying to keep up with work and get a new machine running?

Is it perhaps that I have also have a windows XP box on the same network.  Does Ubuntu set up two networks, one for windows using samba and another between linux boxes?

Is there a way to use the Gnome interface to give permissions to other ubuntu computers to write to files?  I would love to be able to use the terminal but I must be missing something in the sequence of commands.

---


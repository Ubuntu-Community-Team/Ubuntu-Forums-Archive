---
title: "Trouble with SSH and SCP"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by rgb96 on 2009-03-06
I can't seem to get SCP to work. I'm trying to SSH to another computer and pull a txt file from it. My SSH connection works fine, so I was going to use SCP to get the file. I've never used SCP before, but from what I read it seems like you just enter the command like this:

```
scp wbonnerhp:cygdrive/c/AATv2/environments /home/SSC
```

with the first argument being where the file is located, and the second being where I want to put it on my computer. When I do this, I get a "/home/SSC No such file or directory error" which is weird because I know that directory exists. I tried writing the second argument a few different ways, but no luck. any ideas?

---

### Post by pytheas22 on 2009-03-06
Are you sure /home/SSC is writable by the user account that you're using to run this command?  /home/SSC looks like a weird location, because normally usernames in Linux shouldn't have any capital letters in them.  Is 'SSC' the name of a user on your machine, or did you just create that directory?  If you just created it, check the permissions on it--I'm guessing it's not writable by (and possible not visible to) anyone but root.

---

### Post by kanikilu on 2009-03-06
The syntax looks fine as far as I can tell. Is "environments" the name of the text file? Also, do you have permission to write to /home/SSC?

---

### Post by rgb96 on 2009-03-06
well, the permissions were  all create and delete files.

I'm really not sure why, but I was just using SSC as a shortcut. What I actually put in the command was /home/aaran/Circuit_Switch_Controller

---

### Post by geirha on 2009-03-06
The path is relative to the homedir on the server, You probably want to use the absolute path.

```
scp wbonnerhp:/cygdrive/c/AATv2/environments /home/SSC/
```

---

### Post by rgb96 on 2009-03-06
Yeah. environments.txt

I used that in my scp command, I just mistyped it... I really should have copy/pasted.lol

---

### Post by kanikilu on 2009-03-06
> **rgb96 said:**
> I used that in my scp command, I just mistyped it... I really should have copy/pasted.lol I think your syntax is fine, but can you copy and paste the entire command you used?

> **rgb96 said:**
> I'm really not sure why, but I was just using SSC as a shortcut. What I actually put in the command was /home/aaran/Circuit_Switch_Controller Just out of curiosity, does the directory, "Circuit_Switch_Controller", exist prior to trying to copy?

If all else fails, you might want to just try a GUI SFTP client like filezilla (in the repos).

---

### Post by rgb96 on 2009-03-06
$ scp wbonnerhp:/cygdrive/c/AATv2/environments.txt /home/aaran/Circuit_Switch_Controller

Yes that folder existed before I tried this command. I am writing a program and all of my source code is in there.

---

### Post by kanikilu on 2009-03-06
Ok. I would think it would give you a "permission denied" if it was a permissions problem, but...

Is your username the same on both the local and remote hosts? If not, try changing the syntax to "username@wbonnerhp:...".

Does it ask you for your password (and accept it), and then give you the error?

I'm not really sure what else it could be. Is there anything significant about your setup? I noticed the path on the remote machine has "cygdrive", what's up with that? Is this a linux host or windows with cygwin?

---

### Post by Kareeser on 2009-03-06
You may need a trailing slash.

```
scp wbonnerhp:/cygdrive/c/AATv2/environments.txt /home/aaran/Circuit_Switch_Controller/
```

---

### Post by rgb96 on 2009-03-06
Yeah, it gives me a chance to enter my password and it accepts it. I am trying to get a file from a windows machine with cygwin to my computer which is ubuntu 8.10.

I have tried the trailing slash. Same error.

---

### Post by geirha on 2009-03-06
Sure you got the cases correct? afaik it should be case sensitive in both ends

scp wbonnerhp:/cygdrive/c/AATv2/environments.txt /home/aaran/Circuit_Switch_Controller

```
ssh wbonnerhp ls /cygdrive/c/AATv2/environments.txt
ls -d /home/aaran/Circuit_Switch_Controller/

```

---

### Post by rgb96 on 2009-03-06
> **geirha said:**
> Sure you got the cases correct? afaik it should be case sensitive in both ends

scp wbonnerhp:/cygdrive/c/AATv2/environments.txt /home/aaran/Circuit_Switch_Controller

```
ssh wbonnerhp ls /cygdrive/c/AATv2/environments.txt
ls -d /home/aaran/Circuit_Switch_Controller/

```

```
gbonner@wbonnerhp /cygdrive/c/AATv2
$ ls /cygdrive/c/AATv2/environments.txt
/cygdrive/c/AATv2/environments.txt

```

```
aaran@Aserisk:~$ ls -d /home/aaran/Circuit_Switch_Controller/
/home/aaran/Circuit_Switch_Controller/

```

---

### Post by geirha on 2009-03-06
Well I'm out of ideas. Your scp command should've worked (assuming you also have an aaron user on your cygwin), and getting an error that says /home/aaran/Circuit_Switch_Controller/ does not exist just makes no sense :/

---

### Post by pytheas22 on 2009-03-06
It doesn't make any sense to me either why this won't work.  Maybe you'd have better luck if you installed samba on the Ubuntu machine and used regular Windows file sharing to do the transfer.  Or try a graphical sftp client, as geirha suggested (you can mount sftp shares graphically in Ubuntu by going to Places>Connect to Server, or you can install any of dozens of other clients available in the repositories).

---

### Post by Locke_99GS on 2009-03-06
Are you considering point of view? If you're within an SSH to another computer, and trying to scp from there, you will need to treat it as though you are sitting at the other computer. Provide a local path, then a remote path - the remote going back to the PC you're sitting at.

---

### Post by rgb96 on 2009-03-06
wow... Thanks locke. That makes so much sense

---


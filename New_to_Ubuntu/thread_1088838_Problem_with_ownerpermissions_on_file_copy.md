---
title: "Problem with owner/permissions on file copy"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by GaryInThailand on 2009-03-06
I seem to be confused about something fundamental. I'm moving my laptop to Ubuntu. Installation went fine. Now I'm trying to bring over data from my Windows desktop machine.

When I push files and folders from the Windows machine, they come up as 'owner nobody' and locked for writing. Using the Gui, I can't change the owner or permissions.

As an experiment, I copied files to CD and then into the Ubuntu 'Documents' folder. They still come up locked, but I'm now the owner and can change the permissions. Works but awfully tedious for the amounts of data I need to move.

So how can I copy files over the network with permission such that I can work with them? 

Thanks.

---

### Post by taurus on 2009-03-06
You just need to change the ownership of those files from whatever they are to your login name.  Then, you can edit them whenever you want.

Applications -> Accessories -> Terminal
```
sudo chown username:username filename
```
Assuming you are in the directory where filename is and replace username with your login name.

---

### Post by GaryInThailand on 2009-03-06
Please pardon my ignorance. Here's what I typed into the terminal and what I got back:

gary@gary-laptop:~$ sodo chown gary:gary Accounting
bash: sodo: command not found

What am I missing here? Thanks

---

### Post by taurus on 2009-03-06
1.  Typo--sudo.

2.  Is Accounting on your $HOME (not desktop)?

3.  Is Accounting a file or a directory?

```
ls -la ~
```

---

### Post by GaryInThailand on 2009-03-06
Thank you. Accounting is a folder within the Documents folder.

---

### Post by taurus on 2009-03-06
If you want to change the ownership of all the files/directories in Accounting (under Documents), then you would do something like

```
cd ~/Documents
**sudo** chown -R gary:gary Accounting
ls -la Accounting
```

---

### Post by GaryInThailand on 2009-03-06
Well that seems to be working, and it's a big help. I'll dig into the documentation to familiarize myself with the commands.

But is there not a simple to copy files over with the permissions already set to my own?

Thanks again for the help. And patience

---

### Post by TracyO on 2009-03-15
I have the same problem with folders, so thanks for the help.  However (and I realize this is basic) how do I write the name if it is more than one word?  I've tried various methods with no luck yet.

---

### Post by RetchingRabbit on 2009-03-15
> **GaryInThailand said:**
> Well that seems to be working, and it's a big help. I'll dig into the documentation to familiarize myself with the commands.

But is there not a simple to copy files over with the permissions already set to my own?

Thanks again for the help. And patience
Not really, if the file is coming from a "foreign" system like your Windows partition....it isn't going to have properties that will allow for the same permissions until after it becomes a Unix-type of file. chmod and chown are you friends, here.

> **TracyO said:**
> I have the same problem with folders, so thanks for the help.  However (and I realize this is basic) how do I write the name if it is more than one word?  I've tried various methods with no luck yet.

If you are talikng about idiotic names like My Documents, just put the whole name of the file in quotes, for example:

```
cp -R "My Documents" /home/myusername/Desktop 
``` would recursively copy the folder My Documents from it's current location (in your working directory) to your desktop, if your username was myusername.
Note that Linux is always case sensitive, so My Documents is a different file than My documents.

---

### Post by TracyO on 2009-03-15
Thanks for responding.  I ended up taking care of it through changing the permissions under properties.

---

### Post by rafac24 on 2009-03-15
Yeah, sometimes it just works to right click the folder that's locked and change all the Permissions to 'Create and Delete Files'.

---


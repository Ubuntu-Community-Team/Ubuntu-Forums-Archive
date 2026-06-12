---
title: "Join domain to use SMB filesystem?"
date: 2024-07-22
forum: Networking &amp; Wireless
---

### Post by dstromberg on 2024-07-22
I have an Ubuntu 22.04.4 LTS system that I want to use an SMB filesystem on.  I do not currently know for sure what OS the SMB server runs, or its version.  nmap -sS -O thinks it's probably Windows Server 2016 or 2012.

The SMB filesystem has many directories, but from what I've seen, they all have permissions of 755 or 711.

The directories that have mode 755 all allow me to cd into them.

The directories that are mode 711 do not allow me to cd into them.  Depending on whether I try to cd to these as root or myself, I get "bash: cd: /mymount/somewhere/a: Operation not supported" or "bash: cd: /mymount/somewhere/a: Permission denied", respectively.

This is inconsistent with what I would expect from an ext4 or other Linux-native filesystem, but that's not what this question is about.

One of my autofs entries for the filesystem currently looks like:
corp-Teams -fstype=cifs,rw,credentials=/etc/creds-corp ://example.com/somewhere
I've tried other permutations of the options allowed - so many that it's impractical to list them all here.  The above is the simplest one.

Please note that I've obfuscated the hostname and paths for security.

I'm wondering if I need to get my Linux system into the Windows domain to cd to /mymount/somewhere/a, where "a" is a mode 711 directory, or if there is a nicer (more Linux-native and/or simpler) way.

For completeness, I'll mention that my /etc/creds-corp has two lines and looks like:
username=me
password=pw
There's nothing about the domain in it, and I don't know whether there should be or not.

Thanks!

---

### Post by currentshaft on 2024-07-22
Can you chmod those directories to 0755 to see if they work then? Or do you not have remote access to the SMB system?

---

### Post by dstromberg on 2024-07-24
I do not have login access to the SMB server.

---

### Post by currentshaft on 2024-07-24
What happens if you just try to "ls" or "find" those directories instead of "cd"?

---

### Post by TheFu on 2024-07-25
> **currentshaft said:**
> Can you chmod those directories to 0755 to see if they work then? Or do you not have remote access to the SMB system?

chmod doesn't work on CIFS. 

> The directories that are mode 711 do not allow me to cd into them. Depending on whether I try to cd to these as root or myself, I get "bash: cd: /mymount/somewhere/a: Operation not supported" or "bash: cd: /mymount/somewhere/a: Permission denied", respectively.

This is inconsistent with what I would expect from an ext4 or other Linux-native filesystem, but that's not what this question is about.

711 means that only the owner of the directory can 'chdir' into it.  That's how UNIX file permissions work.  The **cd** command requires both execute AND read permissions, not just execute.  Now, if you know the exact name of a file inside a directory that your user/group only has execute permissions on, you can access that file, assuming it's permissions allow read, or run a compiled program (not a script), if read access to the file isn't not allowed.

In short, it is working as designed. That's how Unix permissions are supposed to work.   Local root usually gets translated to "nobody" on remote systems. It's a security thing.  With NFS, you can enable/disable that mode. Allowing a remote root user root access for storage they don't own is terrible for security.

Whether the CIFS manager requires AD credential or not is something only they can answer.  In most corporate Windows environments, they would expect each system to be a member of their AD setup, which you cannot do. Only a Domain Admin can do that for your computer.  I know this because I would remove my computer from AD while working at home, then have to call the help desk every week to get it re-added. The 2nd time this happened, they told me to stop doing it, which caused issues within my network.  My workaround was pretty ugly.   It was their computer and their job to manage it.  I just preferred working from home (saving 90min in a car daily), so causing too many problems wasn't in my best interest.

---

### Post by Morbius1 on 2024-07-25
> **dstromberg said:**
> I have an Ubuntu 22.04.4 LTS system that I want to use an SMB filesystem on.  I do not currently know for sure what OS the SMB server runs, or its version.  nmap -sS -O thinks it's probably Windows Server 2016 or 2012.

The SMB filesystem has many directories, but from what I've seen, they all have permissions of 755 or 711.

[COLOR="#B22222"]The directories that have mode 755 all allow me to cd into them.[/COLOR]

The directories that are mode 711 do not allow me to cd into them.  Depending on whether I try to cd to these as root or myself, I get "bash: cd: /mymount/somewhere/a: Operation not supported" or "bash: cd: /mymount/somewhere/a: Permission denied", respectively.

It's been a while since I've used autofs directly but cifs should sill operate operate normally and that is a curious set of symptoms.

mount.cifs creates a virtual filesystem on the client machine and can have any permissions you want it to have - on the client.
> I've tried other permutations of the options allowed - so many that it's impractical to list them all here. The above is the simplest one.

Have you tied this combination:

```
corp-Teams -fstype=cifs,uid=1000,dir_mode=0755,file_mode=0644,nounix,nodfs,rw,credentials=/etc/creds-corp ://example.com/somewhere
```

The domain access question depends of the server setup and is a bit above my pay grade but if you can access the shares that have 755 permissions this may not be the impediment.

---

### Post by currentshaft on 2024-07-25
> **TheFu said:**
> 711 means that only the owner of the directory can 'chdir' into it.  That's how UNIX file permissions work.

I don't think so. You should check your work before committing to something so confidently incorrect. Being a self-proclaimed Unix expert of many decades, I expect more out of you.

A chmod of 711 means the owner can do anything, while group and other can execute. Here, I will demonstrate:

mkdir foo
chmod 0711 foo
sudo chown root:root foo
stat foo | grep Access
Access: (0711/drwx--x--x)  Uid: (    0/    root)   Gid: (    0/    root)

And guess what? You can cd into the directory.

What you can't do is list it, because that would require the read permission.

---

### Post by TheFu on 2024-07-25
> **currentshaft said:**
> I don't think so. You should check your work before committing to something so confidently incorrect. Being a self-proclaimed Unix expert of many decades, I expect more out of you.

A chmod of 711 means the owner can do anything, while group and other can execute. Here, I will demonstrate:

mkdir foo
chmod 0711 foo
sudo chown root:root foo
stat foo | grep Access
Access: (0711/drwx--x--x)  Uid: (    0/    root)   Gid: (    0/    root)

And guess what? You can cd into the directory.

What you can't do is list it, because that would require the read permission.

You are technically correct. Thanks for pointing that out.  Sometimes we simplify answers for the audience.  I must admit, I was assuming a GUI user using a browser to point-n-click into a directory.  Yes, the OP said he was using cd - I saw that, but my brain ignored it completely.   However, if you don't test using CIFS only, network-only access, not being local to the file system, then root doesn't matter, unless the network share team allows it. God I hope they don't.

What's the use in a chdir if you can't see anything inside the directory?  

Now, Morbius1 probably knows more about CIFS (MSFT version) than anyone else here.  I use autofs, constantly.  autofs supports all the options that a normal 'mount' would support.  file_mode=0664,dir_mode=0775 are definitely supported. In home setups, the mapping of Windows to Unix usernames/groupnames is controlled by the uid=,gid= and  credentials= options.  The uid/gid options support either Unix uid/gid or usernames/groupnames, which is convenient.

In one of my autofs config files, I have this:
```
winult  -fstype=cifs,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/winlap-D.credentials  ://172.22.22.8/Data

```
That mounts the "Data" share from a Windows computer into "/D/winult".  But my home Windows system doesn't use or have AD.  The "/D/winult" is determined from 2 different autofs files.  The "winult" is from the beginning of the line above.  The "/D/" part is in the auto.master that refers to the auto.Data file containing the line above.  This method is one of the confusing things in Unix that isn't expected, but has been that way for 20+ yrs.

Anyway, hope a concrete example helps. There are others in these forums.

BTW, I used to use the DNS name for the CIFS server, but MSFT broke that at some point and I got tired of fighting it, hence the IP address is used.  Also, vers 2.1 is the highest level supported by my box. We all know what that means, but if the OP's share is from 2012, he will likely need to use a specific version as well.   Let me look up the nmap command to probe for the exact CIFS version supported.
```
$ sudo nmap --script smb-protocols 172.22.22.8
```
Very handy.  You'll see after running it.

---

### Post by dstromberg on 2024-07-25
I've tried ls, find and tree.

ls reports:
This one depends on the day, but a reboot may have helped it.  Anyway today, I get:
For a 711 directory:
ls: cannot open directory 'MDT_Backup': Permission denied
For a 755 directory:
A proper ls

find reports:
$ find directory -maxdepth 1 -ls
below cmd output started 2024 Thu Jul 25 03:20:49 PM PDT
     5383      0 drwx--x--x   2 root     root            0 Jul 25 15:20 directory
find: 'directory': Permission denied
above cmd output done    2024 Thu Jul 25 03:20:50 PM PDT

tree reports:
either a directory, or "error opening dir"

All report errors with the 711 directories, and not the 755 directories.

Based on that, it is sounding to me like I'm being mapped to some user other than me.

---

### Post by dstromberg on 2024-07-25
> What's the use in a chdir if you can't see anything inside the directory?

Some people will create a 755 directory inside a 711 directory, to avoid people being able to discover the presence of the 755 one.

One relatively common such use is on an anonymous ftp server.

---

### Post by dstromberg on 2024-07-25
ATM, I'm getting apparmored away from mounting these shares, possibly because I nmap'd the SMB server - they're pretty careful about security here.

Also, it turns out the SMB share isn't big enough for my purposes anyway, so this thread has become less than directly-beneficial to me.

---

### Post by TheFu on 2024-07-25
> **dstromberg said:**
> > What's the use in a chdir if you can't see anything inside the directory?

Some people will create a 755 directory inside a 711 directory, to avoid people being able to discover the presence of the 755 one.

One relatively common such use is on an anonymous ftp server.

Very true, 711 **is** handy for admins, but not typically for end users.

Almost nobody should be setting up an anonymous plain FTP server since around 2002.  We've known better since at least then.

Just use HTTPS instead to share with the world, or sftp to share with authenticated users. While I do use NFS (read-only) to store files to be shared with some of my web servers and document servers, I can't see using RW CIFS storage for that purpose.  Perhaps I'm not seeing the use-case.

Regardless, I'd be surprised if running 1 **nmap** command, specialized as it is, to get the protocol version support list would trigger anything.  If that's the situation, someone from Data Security should have already shown up at your desk, taken you into your Boss's office to have a discussion.  BTW, I had something like that happen to me at my first real job.  My boss told me to "become familiar with the OS", so I started following commands and quickly found some datasets where lots of other things all pointed too. So I tried to take a look and got some RACF errors.  Didn't think anything of it. Access was blocked. An error was shown. Fine.  The next day, after lunch, some federal security guys were waiting for me inside my office (how did they get into the building AND into my locked office?) and asked me to come with them to my boss's, boss's office.  Then they asked me questions for 30 minutes, until they were satisfied.  I was told to write a report about what I'd done and why. To be turned in ASAP  .... and in the meantime, stop doing that.

BTW, that wasn't the last time 2 Feds were sitting in my office at that job.  Fun times!

---


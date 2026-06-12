---
title: "Sharing Between PC -&gt; Ubuntu"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Zigosity on 2007-05-14
Hey,

I'm a complete Linux newbie, but I've decided to give it a shot. It's absolutely critical to get this working for be to continue experimenting with Ubuntu, because most of my family's music and some other work files are hosted on this PC, and they would like access to them while I play around. 

So here's what I want to do: Allow other PCs on the network running windows to access some folders on one of the HDDs on my Ubuntu box. I know I can access all of their shared files normally from Ubuntu, but it doesn't seem to work the other way around. I've been playing around with 'samba server', and I have no idea how it works even after reading several tutorials on sharing files with it. Right now, all I've got is that my PC shows up in network neighborhood, but when I try to access it from a windows box I get a password request. I don't remember setting any passwords...

So, if anyone could just tell me, simply, how to get this working, I'd be VERY grateful. After this is done I can continue to learn how to use the OS, but right now I just need this working. And I'd need a complete idiot proof guide too, I have almost no idea what I'm doing >_>.

Thanks.

---

### Post by reacocard on 2007-05-14
I've found that System -> Administration -> Shared Folders works very well, no extra config needed. You may need to reset your samba config if you've messed with it too much.

---

### Post by Zigosity on 2007-05-14
Thanks,

I've done that now, and I see that's how it works, thanks, but whenever I try and access the shared stuff from the windows PC it prompts me for a password. I've put in my Ubuntu user account password, a whole bunch of possible default passwords, and I still can't get it. It's very strange, I've gone back to all default Samba configs too. 

Thanks for the help so far!

---

### Post by gavinj44 on 2007-05-15
I am also having the same problem, what credentials is it asking for here ?

Regards,
Gavin Jones

---

### Post by DJiNN on 2007-05-15
I don't use gnome, i use Xubuntu but the idea is essentially the same. Take a look [here]("http://doc.gwos.org/index.php/Share_files_using_Samba") & see if that helps. Also, one mistake that i've made more than a few times is the following.....

> [B][U]
Note[/U]: The name of the workgroup (in quotes) must be the same on your windows and Ubuntu box. If you do not know the name or your workgroup, look under "My Network Places" on your windows box, select "Microsoft Windows Network" and you will see a list of your workgroups.[/B] Default workgroup on windows XP, home edition is MSHOME (not WORKGROUP).



Also, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=386610&highlight=samba+user") and see if there's anything there that helps.


Chances are, once you have a username & password both in Samba & your system, then all should work OK. 
 
DJiNN

---

### Post by gavinj44 on 2007-05-15
That seems to describe the process from getting from the Windows desktop to a share on the Ubuntu box.

What I am having is trouble the other way round, from the Places menu I select Network then Windows Network I can then see the Workgroup and then the machine that the share is on, I can see the share but when I try to open the share It asks for credentials, but none of the ones configured on the XP box seem to work, this is a brand new Ubuntu install.

Any ideas ?

---

### Post by DJiNN on 2007-05-16
> **gavinj44 said:**
> That seems to describe the process from getting from the Windows desktop to a share on the Ubuntu box.

What I am having is trouble the other way round, from the Places menu I select Network then Windows Network I can then see the Workgroup and then the machine that the share is on, I can see the share but when I try to open the share It asks for credentials, but none of the ones configured on the XP box seem to work, this is a brand new Ubuntu install.

Any ideas ?

Sorry about that. :)  So you can see the Win Shares from the Ubuntu box, but you just can't access them, is that right? 

If that's the case then it sounds like a Win problem rather than an Ubuntu/Linux problem.  I take it that "Simple File Sharing" is enabled on the drives that you're sharing? (On the WinBox) and that you also have "Allow users to change my files" enabled? 

Also, when you setup Samba (Shared folders etc) did you select "smb" or "nfs"? ..... smb is the one that you want if you haven't already selected it.

You've probably already done the above several times, but i just wanted to make sure. :)  It sounds like it's some kind of Password/Access problem, but where & what to change is the tricky bit. 

If i think of anything else then i'll be right back...... I've had this problem a few times but it was ages ago & i can't remember the reasons or what i did to resolve it. :)  Keep on going though.... i'm sure it won't take long to get sorted out. 

DJiNN

---

### Post by Zigosity on 2007-05-16
Well, to fix the password prompt thing, I went to smb.conf and set this:

security = share

This totally eliminated the password prompt and allowed me to see the shared folders from my windows PC, but now I get this:


"\\family\temp is not accessible. The share name was not found. Be sure you typed it correctly." 

When I double click on the folders from windows... Annoying as hell, I still can't access my stuff :\

---

### Post by tact on 2007-05-16
you need to check the permissions of the folders you have shared.  

sharing folders is one thing.  congrats you have persevered and gotten this far.

(apologies in advance is this is too basic and u already know it)
In linux of any flavour every file, and every folder has an "owner".  Apart from the owner there are 2 other entities:  "group(s)" and "other(s)".   

There are basically 3 types of permission...  read, write, and execute.   read and write are obvious.  you need execute permissions to access a directory (for example, amongst other things).

Any file or folder can have different permissions set for "owner", "group" and "other(s)"

So...  the folders you want to share.  Ignore "group" for a moment.  Who is the "owner"?  (Presumably you?)  This is important because if you do not "own" the folder or files you cannot change the permissions.

You can find out who owns a file or folder, and what the permissions are set to - either at the command prompt (type "ls -l /your/path") or using the GUI file browser (right click>properties>permissions)

If you are owner then fine.  If someone else (or "root") owns the files then you would have to use "sudo" to change permissions.

Now decide whether you want to give read only access to family members?   Set appropriate permissions (for "other(s)" and then they should be able to list directories and access files as well as find the shares in network neighborhood.

---

### Post by tact on 2007-05-16
...referring back to that time prior to you changing 
security = user
to 
security = share

the credentials your windows users were being asked for are specific samba username and passwords that you create and assign on your linux box.

with "user" level security the process for sharing files/folders on your linux box is like this...
1. share the folder or file  (using the ubuntu GUI is ok)
2. make sure the files/folders have appropriate permissions for "other(s)"
3. create a samba  username/password for each person wanting to access the file/folder (using the commandline and samba utilities like smbpasswd)

note: the username/password is created and maintained by samba and its utilities.  Its not the same as a user account you might create using the GUI "System>Administration>Users and Groups". 

No need to follow all those hundreds of guides that tell you to make major edits to your smb.conf file and nsswitch.comf and PAM etc.   Forget all that.  Thats for a full on samber server type install.

To just share files on a peer to peer level with linux or windows boxes - your basic, standard, installed at ubuntu installation time without you even knowing or caring, samba configuration is all you need.

If you don't want your windows users to have to enter a password then one simple edit to smb.conf (changing security = user to security = share) is enough.  But you still have to do the first 2 steps above.  Share the folder, set permissions appropriately.

---

### Post by gavinj44 on 2007-05-17
Turns out it was an XP problem, The network setup wizard finished saying an error had occured but no information as to what the error was ...

I disabled file and print sharing and then rebooted and then re enabled it and rebooted again ;)

And voila it now does not ask for a password and I can access the shares on the Windows box.

Thanks for all your help on the above, just need to sort out the printer now ;)

---


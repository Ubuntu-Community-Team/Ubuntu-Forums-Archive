---
title: "How to network 2 computers"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by brk3 on 2007-05-15
Hi, Im aware there are other similar posts about this but there seems to be no clear cut answer.
Ive spent hours trying to network 2 ubuntu computers via a network cable to share some files, it works fine on windows its just a case of running the setup wizard, but I just cant believe there is no similar way on ubuntu. All the forum posts seem to involve editing obscure files that Im pretty sure arent meant to be messed with.

Could someone please post a brief guide on what to do to get the files showing up, I have it partially working(the other computer shows up in places->network) but I cant seem to access its files.  Should I be using samba or nfs or what..? Any help greatly appreciated Ive wasted nearly a whole day on what should be a trivial task!

---

### Post by dotweb on 2007-05-15
I will join in on this question. I have only been using linux for four weeks, and the only thing missing is my home network. Hope that there is an easy way out this problem.

Thanks

//dotweb

---

### Post by hartz on 2007-05-15
Hi there, and congrats on getting this far.

If both computers are running Linux, then NFS can be used.  If you have any Windows computers on the network, SAMBA is your best bet.

I will assume you have two linux computers, and I'll call them firsthost and otherhost. Firstly, confirm that the two computers can see one another.  On each computer open a terminal (Applications -> Accessories -> Terminal)  

My procedure below involved about 17 commands.

Then on each computer, using the IP for the OTHER computer each time, run this command:

```
ping 192.168.10.20
```

Substitute the address I used above with whatever applies in your situation.  You should get a new line every second or so containing statistics.  Press Ctrl-C to end the test, and it should print some summary statistics just before it quits and returns your prompt.

You should expect a low packet loss, which indicates that the connection is working well.  A 0% packet loss is typical of today's network hardware.  It will be useful if the two computers can see one another by means of a name in stead of an IP address.  To this effect, you need to add an entry to each computer's hosts table.

on each computer, do the following:```

sudo cp /etc/hosts /etc/hosts.bak
sudo echo "192.168.10.20   otherhost" >> /etc/hosts
```

Note:  I just entered a few spaces in there.  TABS would be nicer.  Press Ctrl-V, followed by a TAB, to obtain a real TAB... if you want.  This is quite optional.

The address and hostname parts must correspond to the OTHER computer's details.  This makes a backup copy of the /etc/hosts file and adds the other computer to the end of the file.  Once done, enter this command to display the file in the terminal:

```
cat /etc/hosts
```

You should see in each computer's hosts file an entry at the bottom for the "other" computer.

You can now re-do the ping test using names in-stead.  Eg

```
ping otherhost
```

To share some location on your hard drive via NFS, you need to install an NFS server.  enter this command:

```
sudo apt-get install nfs-kernel-server
```

When prompted to confirm the actions that will be taken, Enter Y.

You should see a line indicating that the new daemon has been started.

To check that it is running, you can also issue this command:
```
ps -ef|grep nfs
```

You should see a number of nfsd processes.  These are nfs "daemons", daemons are the "services" in Unix-land.

To export a file system, you use the exportfs command.  This command gives "otherhost" access to a file directory and all directories below:

```
sudo exportfs otherhost:/path/to/directory/
```

You can run this multipe times to export more than one directory.

The default is to export file systems as "read-only".  You can change this by running this command instead:

```
sudo exportfs -o rw otherhost:/path/to/directory/
```

To see information about exported file-systems, run this command:

```
exportfs -v
```

And if you want to change options, you sometimes want to first un-export a file system and then re-export it, so the command may be something like this:

```
sudo exportfs -u otherhost:/path/to/directory/
```

Finally, to mount the file system from firsthost on otherhost.  First decide what directory you will use to mount the file system on.  I suggest that you create a new directory, like this:
```
sudo mkdir -p /firsthost/somedir
```

Then mount the directory.
```
sudo mount -t nfs firsthost:/path/to/directory /firsthost/somedir
```

Check that it is seen:```

df
mount
cd /firsthost/somedir
ls -l
```

Voila - NFS is fast, easy and works very well in Unix/Linux environments.

---

### Post by dotweb on 2007-05-15
Sorry, I seems to get something wrong .... I get:
"Permission denied" 
How do I get around that?

//Thanks for your help

---

### Post by Neuralgia on 2007-05-16
For some reason, after getting Feisty, I just right cliked on a folder, "share folder"... it told me it needed to install some stuff... restart VOILA.

I can even share my printer :)

---

### Post by hartz on 2007-05-16
> **dotweb said:**
> Sorry, I seems to get something wrong .... I get:
"Permission denied" 
How do I get around that?

//Thanks for your help

At which step do you get this problem?


I use GUIs more and more these days - yesterday I read a guide on how to remove red-eye from a photo using Gimp.  It worked quite nicely, and I would not have been able to do it without a GUI.  GUIs are nice I guess, as long as they don't get in your way.  But I digress ... there is a reason why I used the command line in my little "guide" above.

After completing those steps, you can add more exports without having to go through the whole process again - You just run the exportfs command on one computer, and the mount command on the other computer.

Through this process you have learned many things.
- The ps command, piped through grep, shows running processes
- Use of the echo command to add a line to the hosts file
- The hosts file resolve names to IP addresses
- The ping command tests connectivity between computers
- the cp command makes a copy of a file
- the cat command shows the content of a file
- preceding a command with "sudo" will execute the command with elevated privileges.

Another reason I had in mind is that when we talk about sharing file systems we often talk about "servers".  And with "servers" we often think about working across the network and sometimes these don't even have a GUI installed.  The above procedure will work on an Ubuntu /server/ installation on any old computer, maybe one not powerful enough to run a GUI.  You can log in from a terminal window into a server by using a telnet or ssh command, and remotely execute all of those commands, even across a 9600 baud dial-up link.  Try using a GUI for that.  

Most importantly I have used a single window - the terminal - to perform many different tasks.  On the one hand, this makes the terminal scary.  It is powerful, but it may seem cryptic, unfriendly, magical.  It is beautiful.  There are thousands of commands you can use, and each one has got many different ways in which you can use it, so there is no surprise that it seems "difficult" to learn.  But it is not - just take it one day at a time and in a month you will love it.

Soon you write a little script to automate the process.  (A script is just a text file containing the steps you would enter at the command line, one after another).  This allows you to repeat the same procedure many times, because you can copy the script to many computers and let it execute the steps.

There is another topic I can go into in some more depth here, ie the Mounting of file systems on directories, which seemed a bit weird to me the first time I encountered it, and I had the benefit of not having been indoctrinated (much) by the awkward drive-letter based method used by some other operating systems.

So let me know if you're interested.

Also it is worth noting that the above procedure will not make the changes survive a reboot.  For now, just get it to work first.  Once it is working just right, you can make the settings "permanent".  I'll provide some guidance on how to do that too once you get it to work.

---

### Post by Rob2Kx on 2007-05-16
Hartz:  That quick NFS sharing guide was money.  I was having a lot of problems, but I followed that and it worked to a T.

As for the guy above getting the permission denied error, I bet it happens here:

sudo echo "192.168.10.20   otherhost" >> /etc/hosts

That's where it happened for me, so I just opened /etc/hosts with gedit, and wrote in the line at the bottom of the file then saved it.

Now about making those changes survive the reboot.... is it just a matter of making the IP's static and writing a script to mount the shared folders on startup?  a little help there would be nice :D

---

### Post by Panzor on 2007-05-16
> **dotweb said:**
> Sorry, I seems to get something wrong .... I get:
"Permission denied" 
How do I get around that?

//Thanks for your help

That usually means that you have to be root to do that operation.
Just add "sudo" before the line that gives you this error.

---

### Post by dotweb on 2007-05-16
Yepti - now it works here too. I cant say it was easy to or easy to understand. It was great help, but I wonder why there has been made a more user-friendly application for setting up a network.  The console is - as you explain so well a powerful tool - but it is also something that effectively stops more people from using Linux. 
But your help was great - thanks, and I cant waint for next chapter on how to make the settings stay. 
//KR dotweb

---

### Post by Cheese Sandwich on 2007-05-16
Awesome - thanks! 8)

---

### Post by hartz on 2007-05-17
Right.

There are two things that needs to be made permanent.
[LIST]
[*]The system "sharing" the NFS resource needs to have an entry placed into the file /etc/exports for every exported directory
[*]The client(s) connecting to this resource needs to have an entry added to their /etc/fstab file to make them mount each share at startup.
[/LIST]

[COLOR="Red"]On the server (system sharing the resource) you need a line like this in the /etc/exports file:
```
/path/to/directory/   client1(ro) client2(rw) otherhost(ro)
```

Basically the lines specify what directories are to be shared, and for each directory, a list of the names of "client" computers that can connect to it.  For each client, there is a set of options specified in brackets, with NO leading space.  

I just used "ro" or "rw", there are some other options you can specify but these should be sufficient for a start.  In the example above, client1 and otherhost gets Read-only access, but client2 gets full read-write access to the file system.

Basically if a client tries to mount a file system as "read-write", but you have specified that it only gets read-only (ro) access, then the mount operation will fail with an error.
On the other hand if you allow read-write for a specific client, and it makes an attempt to mount the file system as "ro", then the mount will succeed, but it will be read-only by that client as long as the mount point stays mounted like that.
[/COLOR]

[COLOR="Blue"]On the client side you need to add "file system mount" entries to the /etc/fstab file.

These entries look like this:

```
#Resource	Target	Dir	Type	Options	Dump	Seq
firsthost:/path/to/directory	/firsthost/somedir	nfs	rw	0	0
```

[LIST]
[*]The line starting with # is just a comment I added as a caption/guide.
[*]The entries in the file are normally tab-separated, though any white space is acceptable.
[*]First Entry: The shared resource to mount (connect to), including the host and the shared directory
[*]Second Entry: Where to mount it (the local path you want to use to access the shared directory)
[*]Third entry: The type of resource.  The keyword "nfs" must be here to indicate that it is an NFS share.
[*]The fourth entry:  This is a "list" of options.  I only specified a single option, so it is a list of one option, being "rw" to requires read-write access
[*]The next two options should just be 0 for NFS shares.  These pertain to dumping and doing consistency checks for this file system which doesn't apply.
[/LIST][/COLOR]

To make edits to system files, you can use a text-editor program.  a program like "gedit" will open a new window, and executed with "sudo" will elevate its permissions to allow it to save modifications to the file.

There are also command-line (CLI or terminal-mode) editors.  "joe" is quite a popular editor with Linux users, you can install it using this command:

```
sudo apt-get install joe
```

Use one of these commands to edit the file:
```
sudo joe /etc/fstab
sudo gedit /etc/fstab
```

When using Joe, try
Ctrl-K, H (press Control-K, then tap H) to get some help.
Ctrl-K, X (Save and Exit)
Ctrl-K, Q (Quit, you will be prompted to save changes)

If you do not want the client to mount the NFS share constantly, you can create a little script which you can run to mount it (connect to the server), and another to unmount it (disconnect from the server).

**You should test the entries you placed into the files.**
First unmount the share on the client
```
umount /firsthost/somedir
```

Check that it is indeed not mounted any more (on the client)
```
df
```
The entry should be missing.

Then un-share the directory on the server side with this command
```
sudo exportfs -u otherhost:/path/to/directory
```

Check that it is indeed not shared any more
```
exportfs -v
```
There will probably be nothing shared now.

Now run the command to automatically share everything as specified in the /etc/exports file
```
sudo exportfs -av
```
This command uses the /etc/exports file, exactly as it will be done when the system boots up.

And then check and list the exported file systems:
```
exportfs -v
```

Now back to the client - run the "mount all file systems of type nfs" command:
```
sudo mount -a -t nfs
```
This command uses the /etc/fstab file, exactly as it will be done when the system boots up.

Finally, make sure the mount was really successful :
```
df
cd /otherhost/somedir
ls -l
```

The df command should show the remotely mounted file system, and after the "cd" command, the ls command should list the files across the network.

Note: the sudo echo xxxx > file
will not work as I suggested earlier.  This is because sudo elevates the permission of the command "echo", but not the permission of the redirection (the "> file" part).  So sorry, I wasn't thinking when I wrote that.

A workaround would be to use this trick:
```
echo "Some line to add to a file" | sudo tee -a filename
```

Also note your systems should have static (fixed) IP addresses as hinted as by another poster.  That however is off-topic for this little tutorial (because I am tired now and my brain is fried)

Simply place the mount commands in a text file and save it as, for example, "mount-shares".  Similarly create a file with a meaningful name like "unmount-shares", containing unmount commands one-per-line.  These files can be made "executable" so that you can run them by entering the file name.

---

### Post by hartz on 2007-05-18
After writing the above and including a step to install joe, it continued to bothered me that "joe" was not installed by default in ubuntu.  So reasoning that there had to be SOME user friendly CLI-mode text editor included with ubuntu, I started to scratch around and soon discovered that a text editor called "nano" is provided with ubuntu.

I've heard of it, probably even ran it some time ... many years ago, but never needed it (I use vi, but I don't recommend it to new users).

Give "nano" a try, it is a bit more polished than joe and comes pre-installed.

I also noticed that "pico" is linked to nano (meaning if you enter the command pico, Linux will run nano).

---

### Post by Luis_vxd on 2007-05-19
Hi

I am new to Ubuntu and Linux so I am playing around with it now.

My home network have a Ubunto (feisty) and 2 XP Professional computers. From the Ubunto I can see and manage the shared folders on the 2 XP but from the XP I can see the Ubuntu computer but cant access it.
The idea is to use the network as a P2P without a 'server'. Searching the internet I found the concept of "network users" but cant find it on Ubuntu.

What am I doing wrong?

Thanks

---

### Post by kvonb on 2007-05-19
> **Luis_vxd said:**
> Hi

I am new to Ubuntu and Linux so I am playing around with it now.

My home network have a Ubunto (feisty) and 2 XP Professional computers. From the Ubunto I can see and manage the shared folders on the 2 XP but from the XP I can see the Ubuntu computer but cant access it.
The idea is to use the network as a P2P without a 'server'. Searching the internet I found the concept of "network users" but cant find it on Ubuntu.

What am I doing wrong?

Thanks

The easiest way is to get rid of the annoying and unnecessary logon password thing.

Press ALT-F2 and type this into the run box:

```
gksu gedit /etc/samba/smb.conf
```

Find this line:

```
security = user
```

and change it to:

```
security = share
```

Save and exit

Press ALT-F2 again and click on the box "run in terminal", then type this in and select RUN:

```
sudo /etc/init.d/samba restart
```

Give it a few seconds then try to access the network again, that should fix you up :)

---

### Post by tact on 2007-05-19
> **Neuralgia said:**
> For some reason, after getting Feisty, I just right cliked on a folder, "share folder"... it told me it needed to install some stuff... restart VOILA.

I can even share my printer :)

THAT is exactly how it should work - and also did work for me.  

No need to go thru the 23 commands or edit esoteric config files.

Just right click on a folder or file>sharing> and if this is the first time you will be prompted via a msg box telling you that you need to install Samba or NFS to share files...  leave BOTH selected and let it install.

I note that one of the original question askers mentioned that both machines can be seen in Places>Network.  Excellent you already have NFS or Samba installed as much as is needed.   

Now all you need to do is:
1- make sure that you have the right permissions assigned to the shared folders/files.  Right click on the folder and any files in a share and then click Properties>Permissions.   Even if a folder/file is shared - if permissions are set so that users "other" than the owner have no access then guess what - no one will see them.

Linux is THAT much more configurably secure by default than Windows peer sharing.  ;)

2- you also need to ensure that each user who is allowed to access the share has a username and password on the host PC (unless using samba and you decide to edit an esoteric config file (/etc/samba/smb.conf) to change security from "user" to "share").  

3- (again if using samba with the default "security=user") you ALSO must use the command and "smbpasswd" commands to add the permitted users to samba's list of permitted sharers.


So thats the overview of the process.  Of course you COULD edit configs and allow pretty much "guest" access with no password required.   But where is the fun in that!

---

### Post by hsweet on 2007-05-19
Thanks everyone.  One more question.. One of the posts mentioned printer sharing.  How 2?

---

### Post by The Pinny Parlour on 2007-05-19
> **brk3 said:**
> Hi, Im aware there are other similar posts about this but there seems to be no clear cut answer.
Ive spent hours trying to network 2 ubuntu computers via a network cable to share some files, it works fine on windows its just a case of running the setup wizard, but I just cant believe there is no similar way on ubuntu. All the forum posts seem to involve editing obscure files that Im pretty sure arent meant to be messed with.

Could someone please post a brief guide on what to do to get the files showing up, I have it partially working(the other computer shows up in places->network) but I cant seem to access its files.  Should I be using samba or nfs or what..? Any help greatly appreciated Ive wasted nearly a whole day on what should be a trivial task!

It doesn't work.  I'm yet to see or setup a successful network to or from a ubuntu-windows pc.

---

### Post by Luis_vxd on 2007-05-19
Thanks kvonb.

Just perfect. What I wanted.

---

### Post by mrgnash on 2007-05-20
I have found trying to share files between two Ubuntu machines to be one of the most frustrating and ###-backwards aspects of the OS. For the time and hassle, you'd probably be better off emailing whatever documents you need to transfer to yourself and picking them up on the other end.

---

### Post by The Pinny Parlour on 2007-05-20
> **mrgnash said:**
> I have found trying to share files between two Ubuntu machines to be one of the most frustrating and ###-backwards aspects of the OS. For the time and hassle, you'd probably be better off emailing whatever documents you need to transfer to yourself and picking them up on the other end.

Couldn't agree with you more.

---

### Post by xpod on 2007-05-20
> Couldn't agree with you more.

I could`nt disagree more i`m afraid
I myself have 2 ubuntu machines connected with just a spare network card & crossover cable and setting up nfs was a piece of cake...even for a pc novice like myself;)

I just followed the simple instructions  here and it all works great
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

I also had to allow the second pc access using firestarter.

---

### Post by The Pinny Parlour on 2007-05-20
> **xpod said:**
> I could`nt disagree more i`m afraid
I myself have 2 ubuntu machines connected with just a spare network card & crossover cable and setting up nfs was a piece of cake...even for a pc novice like myself;)

I just followed the simple instructions  here and it all works great
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

I also had to allow the second pc access using firestarter.

I was referring to linux>windows and vice versa. ;)

---

### Post by ADT on 2007-05-21
Thanks hartz, great tutorial. :D

---

### Post by hartz on 2007-05-21
My pleasure, I am glad it was useful.

---

### Post by gigaferz on 2007-06-27
hello, Im not posting anything useful ,but i am at a public computer right now and I need to "flag " this post to try it later

---

### Post by tico on 2007-08-03
Well,

I've done the following:

in /etc/exports (server: Acer)

/home/share		Toshiba(rw,sync)

in /etc/fstab (client: Toshiba)

Acer:/home/andre	/mnt/Acer/Home nfs	rw,andre 0 0

Here are my questions/problems:

1. The directory is not mounted after boot. I should mount it manually. How could I automount it?

2. When I try to manually mount it, I get the following error message:

Could not mount device.
The reported error was:
mount: only root can mount Acer:/home/andre on /mnt/Acer/Home

I'd like to be able to mount it without being logged in as root. How could I do this?

3I my server computer I've got a ntfs partition mounted in /mnt/sda1. When I try to mount it a get a "permission denied" message, even if I have given the permission in the server computer using "exportfs -o rw Toshiba:/mnt/sda1". Is there a way to fix this?

Thanks.

---

### Post by blueflyt on 2007-08-04
Somebody help me please.  I have a small business and needed to add some PC's to our peer-to-peer network.  I was convinced by someone that I should install Linux on them to save money.  So I've got Kubuntu installed on two PCs.  Everything works fine; I can surf the Net, do everything I normally do on a Windows machine...except for sharing files!  Why is this so difficult with Linux?  

When I try to share my home folder (or a sub-folder) by right-clicking on the folder (and entering the appropriate root password), I get a message that says "SMB and NFS servers are not installed on this marchine, to enable this module the servers must be installed."  

Okay, fine.  How do I do that?  Why do I have to spend hours (literally) reading through these forums trying to figure out something as simple as file sharing when it should come pre-packaged out of the box?  This is really aggravating.  Can someone please provide me with SIMPLE, BASIC, NON-GEEK instructions on what I need to do to share folders between two machines running Kubuntu 7.04?  The funny thing is, I can see my Windows Vista box's on the network as well as my XP box's and browse the shared folders on those machines (although only the XP machines will let me copy files).  

Any simple, straightforward help will be appreciated.  Please keep it simple: I don't appreciate people trying to impress me with techno-talk.  Leave your ego behind.  Keep it simple and you may just help a small service company with 11 employees switch over entirely to Linux/kubuntu, which would be a small, but nevertheless great step in putting a chink in Microsoft's armor.  

Thank you in advance!

---

### Post by clblanchard on 2007-08-13
> **blueflyt said:**
> Somebody help me please.  I have a small business and needed to add some PC's to our peer-to-peer network.  I was convinced by someone that I should install Linux on them to save money.  So I've got Kubuntu installed on two PCs.  Everything works fine; I can surf the Net, do everything I normally do on a Windows machine...except for sharing files!  Why is this so difficult with Linux?  

When I try to share my home folder (or a sub-folder) by right-clicking on the folder (and entering the appropriate root password), I get a message that says "SMB and NFS servers are not installed on this marchine, to enable this module the servers must be installed."  

Okay, fine.  How do I do that?  Why do I have to spend hours (literally) reading through these forums trying to figure out something as simple as file sharing when it should come pre-packaged out of the box?  This is really aggravating.  Can someone please provide me with SIMPLE, BASIC, NON-GEEK instructions on what I need to do to share folders between two machines running Kubuntu 7.04?  The funny thing is, I can see my Windows Vista box's on the network as well as my XP box's and browse the shared folders on those machines (although only the XP machines will let me copy files).  

Any simple, straightforward help will be appreciated.  Please keep it simple: I don't appreciate people trying to impress me with techno-talk.  Leave your ego behind.  Keep it simple and you may just help a small service company with 11 employees switch over entirely to Linux/kubuntu, which would be a small, but nevertheless great step in putting a chink in Microsoft's armor.  

Thank you in advance!


To install samba

sudo apt-get install samba

---

### Post by grrrlshapedthing on 2007-12-12
I did number 1 and it seemed to work fine i allowed access... but i still don't see any files... I'm trying to connect an Ubuntu comp with a linux mint comp(which is basically like  networking two ubuntu comps)

I'm really new to linux and not much of a technology knowledged person when it comes to this!

> **tact said:**
> THAT is exactly how it should work - and also did work for me.  

No need to go thru the 23 commands or edit esoteric config files.

Just right click on a folder or file>sharing> and if this is the first time you will be prompted via a msg box telling you that you need to install Samba or NFS to share files...  leave BOTH selected and let it install.

I note that one of the original question askers mentioned that both machines can be seen in Places>Network.  Excellent you already have NFS or Samba installed as much as is needed.   

Now all you need to do is:
1- make sure that you have the right permissions assigned to the shared folders/files.  Right click on the folder and any files in a share and then click Properties>Permissions.   Even if a folder/file is shared - if permissions are set so that users "other" than the owner have no access then guess what - no one will see them.

Linux is THAT much more configurably secure by default than Windows peer sharing.  ;)

2- you also need to ensure that each user who is allowed to access the share has a username and password on the host PC (unless using samba and you decide to edit an esoteric config file (/etc/samba/smb.conf) to change security from "user" to "share").  

3- (again if using samba with the default "security=user") you ALSO must use the command and "smbpasswd" commands to add the permitted users to samba's list of permitted sharers.


So thats the overview of the process.  Of course you COULD edit configs and allow pretty much "guest" access with no password required.   But where is the fun in that!

---

### Post by buccaneere on 2007-12-13
I'm still in the process of converting 5 machines to EEft, same version on 4 so far - WITH SAME NAME, SAME USERNAME, AND SAME PASSWORD.

Will this make for problems in sharing? Make for *easier* sharing?

*Internal* security, and wireless security aren't concerns, if this makes any difference...

Another consideration: One desktop will eventually be configured to play media files, and stream them to each of the other 4 pc's in the house simultaneously from one media player.

Thanks

---

### Post by buccaneere on 2007-12-14
> **buccaneere said:**
> I'm still in the process of converting 5 machines to EEft, same version on 4 so far - WITH SAME NAME, SAME USERNAME, AND SAME PASSWORD.

Will this make for problems in sharing? Make for *easier* sharing?

*Internal* security, and wireless security aren't concerns, if this makes any difference...

Another consideration: One desktop will eventually be configured to play media files, and stream them to each of the other 4 pc's in the house simultaneously from one media player.

Thanks

bumpintodatop...

---


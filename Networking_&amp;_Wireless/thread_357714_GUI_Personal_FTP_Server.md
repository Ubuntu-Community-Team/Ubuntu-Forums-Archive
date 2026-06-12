---
title: "GUI Personal FTP Server"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by CalcProgrammer1 on 2007-02-10
I'm using an old Pentium 133 MHz machine as a personal FTP server.  Currently, it's running Windows 95, and runs great but that old OS can only recognize 8GB of the HDD, and if that, you have to split it up into like 5 partitions.  I'm thinking of switching to a lightweight version of Linux on it, like I had before.  However, I could not find any good GUI FTP server applications.  I use WarFTP for 95 on it now, is there a good FTP server WITH GUI for Linux?  Or...is there any way to mount a ext2fs or fat32 partition in Win95?

---

### Post by gradedcheese on 2007-02-10
FTP is a standard, defined long long ago.  Any OS can run an FTP server, and any FTP client can connect to it.  So you can continue working as before, the OS will not be noticeable from the client side.

Also, I recommend SFTP instead of FTP as FTP presents a huge security risk (it sends passwords pretty much in plain text).  On ubuntu, you just need to do this:

sudo apt-get install openssh-server

From any client PC, just connect via SFTP (port 22) and you should be all set.

---

### Post by clint1010 on 2007-02-10
If security is not a big issue for you, try proFTPd for a server, uses the standard FTP protocol. For client software I use gFTP. Both of these packages are available using synaptic.

Search the forums, there is a great How To by frodon somewhere.

Have fun

---

### Post by CalcProgrammer1 on 2007-02-10
How do you set up this server?  On WarFTPd, the server I'm currently using, you can setup a user database with usernames, passwords, and restrictions.  You can also assign what folders can be accessed and which ones can't.  Is the Linux server configured through console or from a GUI interface?  The only thing I've used so far for Linux FTP is BetaFTP and I didn't get its interface, it had a GUI but no settings options.  The OS I'm probably going to use would be either DSL or Puppy Linux, unless there's a way to get Ubuntu running with Fluxbox or something on a P133/64MB RAM.  I have a 40GB hard drive.

All of my client PC's are going to most likely be Windows, and I've been able to access FTP from all of the versions of Linux I've used, so that isn't much of an issue.

I will try proFTPd on my DSL boot CD and see how I like it.

---

### Post by gradedcheese on 2007-02-10
Well, I can tell you from a UNIX perspective, but if you're shooting for some Windows-style GUI thing then I don't know much about it.  

Basically, you can create Linux accounts for your users: "sudo adduser user_name_here" or use the GUI tool in System->Administration->Users and Groups  -- these accounts are their SFTP accounts, and each account comes with a home directory where they will be logged in to by default.  So those are your "user" directories, which you get automatically.  

Now if you want certain directories where just particular users can have access, or that sort of thing, it's also very easy.  Create a group (ex: "ftpusers") and add the needed users to it.  You can do that in Users and Groups or you can do it the shell way: "sudo addgroup group_name" to create a group, "sudo adduser user_name group_name" to add a user.  Make sure you add yourself to that group too.  

Now set the permissions for that directory such that the group in question has access but the default group 'users' does not.  The graphical way is to right-click on the directory, go to Permissions, and you will see the group option there.  You may need to run Nautilus with gksudo to be able to do this (I assume you'll create this special share directory somewhere outside of your home, like /opt/groupshare or something).  The command line way is "sudo chown -R your_username.group_name /path/to/the/share"

In closing, Linux is a very powerful UNIX-style operating system and it's usually administered via the shell, often remotely via an ssh login.  You can still do GUI stuff as needed, but it helps to think the UNIX way rather than trying to change things to a more Windows-style model (in my opinion, you'll find the UNIX way more secure and to make more sense in the end)

For example, the file server I administer sits in th garage.  It has never had a monitor or keyboard or mouse hooked up except for the day I installed it, which was about 2 years ago.  When I need to do something, I ssh in and do it with the shell.  It has never been rebooted except for power outages and kernel upgrades.  Nothing on it has ever crashed or needed 'fixing', it's just a matter of occasionally logging in and adding/removing users.

---

### Post by lavinog on 2007-02-10
> **CalcProgrammer1 said:**
> How do you set up this server?  On WarFTPd, the server I'm currently using, you can setup a user database with usernames, passwords, and restrictions.  You can also assign what folders can be accessed and which ones can't.  Is the Linux server configured through console or from a GUI interface?  The only thing I've used so far for Linux FTP is BetaFTP and I didn't get its interface, it had a GUI but no settings options.  The OS I'm probably going to use would be either DSL or Puppy Linux, unless there's a way to get Ubuntu running with Fluxbox or something on a P133/64MB RAM.  I have a 40GB hard drive.

All of my client PC's are going to most likely be Windows, and I've been able to access FTP from all of the versions of Linux I've used, so that isn't much of an issue.

I will try proFTPd on my DSL boot CD and see how I like it.

since you have 32 gigs available on your hd why not just install ubuntu server (without the desktop) using the alternate cd. You can set it up as dual boot this way if all else fails you can boot back to your win95 setup. (you should really consider using linux for your server...win95 can't possibly be secure.)

I'm not sure what you are using ftp for. Are you using ftp to serve files on a local network or across the internet? If you just need local network access consider using samba so you can access your shares just like folders on your client computers.

Also the advantage (as mentioned in earlier post) is that you don't need a screen or keyboard...This would save space and electricity. Also operating without a gui reduces the overhead and processing power thus reducing the power usage (every watt helps when you are considering running a server all year long) (do not run a screensaver if there is no screen...you would just be wasting money)

---

### Post by mrpeenut24 on 2007-02-11
I'm also looking for a GUI ftp server.  I used to use BulletProofFTP, and it was great.  It was simple, but highly configurable.  From what I've seen, all the ftp servers are either non-gui, or not highly configurable.  Are there any that bring both of these together?

---

### Post by CalcProgrammer1 on 2007-02-12
I'm using this server for Internet, but just to share files with friends.  I'll also probably connect to it from school to upload files.  I want a GUI so that I can use it for occasional Web browsing and mp3 playing (xmms works quite well on some distros).  I have Vector 3.2 installed currently but although it runs fine, it's not Debian based and doesn't have Synaptic or apt-get, and the autopkg installer fails because there is no support for it because it is so old.  I'm going to try Xubuntu, using alternate CD.  I've set up 1GB as linux swap (hda1) and the rest as ext2fs (hda2).  I also would like if it would be able to work with a Windows home network (I've only ever gotten this to work on Puppy Linux).

---


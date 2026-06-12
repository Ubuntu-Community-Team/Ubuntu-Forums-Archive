---
title: "How to connect two laptops on one LAN Ubuntu"
date: 2022-01-13
forum: Networking &amp; Wireless
---

### Post by validust on 2022-01-13
Having two Dell Latitude E7470 laptops on the one LAN, with Ubuntu MATE 20.04 on both, I looked for a way to connect them. There are many... And I couldn´t make any of them work.
When ready to give up, my CLI-speaking brother came to the rescue. It was so simple!

1.  Make sure you have SSH (Meta package) installed in both laptops´ OSes
2.  Open the File Manager (Mine is Caja. About Nautilus, see lower down in this post.)
3.  On the top left click on "File".
4.  On the drop-down list click on "Connect to Server".

Server Details
5.  In the field for "Server" write the other laptops internal (local) IP address. (For me the easiest way to find it, was to rest the pointer on the Network Monitor/Netspeed Applet icon of the other OS. It starts 192.168...)
6.  As "Type" choose SSH. The Port then changes from "21" to "22", and "User Details" appears.
7.  In "Folder" I chose "/".

User Details
8.  Write the user name of the other laptops OS.
9.  Write the password of that user.
10. I marked "Remember this password".
8.  I marked "Add bookmark", and named that bookmark sumpin.

In Nautilus the "Connect to Server" is found when you open "Other  Locations" at the bottom. There you write "ssh://username@server". I don´t know if bookmarking it is possible.

When clicking "Connect" the other OS´ File Manager appears beside the one of the OS you are using. Next time you want to open it, just click on the bookmark. If the other laptop is on, it will open. Some day I´ll find a way to have the thumbnails in that file manager showing whatsits.

---

### Post by TheFu on 2022-01-13
"Connect" is ambiguous.  How did you want to connect?  There are a number of different protocols which allow connecting 2 or more systems.
[LIST=1]
[*]remote terminal
[*]remote window/GUI program
[*]remote desktop
[*]file sharing (permanent)
[*]file sharing (temporary)
[/LIST]
Then there are a bunch of client/server "connections like NTP, HTTP, SMTP, SNMP, - literally, there are thousands of "connection" possibilities between systems.

For **remote terminals**, I use ssh.  Install openssh (meta package) on both the client and server, then just open a terminal and run
```
$ ssh remote-user@remoteIP-Address
```
There are lots of ways to make this more secure AND more efficient, but that's the basic method. No downloading any special GUI program needed.  Any terminal that already exists on your system can be used.  Ssh is really the only viable ch

To run a **remote GUI program** on a different system and have that program shown on the system you happen to sit behind, use 
```
$ ssh -X remote-user@remoteIP-Address name-of-program
```
The "name-of-program" needs to be the actual name of the program, not the menu name.  So, "Printers" is probably "system-config-printer". Also, if the program isn't in the PATH for the "remote-user", then the full path to the program is required.  Simple command, but crazy useful.  All the traffic will be tunneled through the ssh connection and some other things are automatically setup for us. If this doesn't work, it is possible the sshd_config file on the remote system doesn't allow X11Forwarding. The default was to allow it, but that might be changing in newer releases.

To run a **remote desktop**, we need to ensure it is over a secured connection.  As we learned above, ssh is the way to have both secure authentication AND tunneling.  That means that rdp or vnc connections all need to be tunneled through ssh to be secure. Neither rdp nor vnc servers should allow any connections except from 'localhost'. This little thing will prevent people from using non-secure connection methods. Or just use one of the NX-based desktop protocols which are 2-3x faster than either vnc or rdp.  x2go is one of those.  NX makes use of ssh tunnels, so we only need to have ssh setup, just like all the methods above this imply or state.  Do you see a pattern?  x2go has a client and a server - install the server on the remote system (over an ssh terminal) and the client on the local system. There are x2go clients for Windows, OSX, and Linux and I know the Windows and Linux clients are very solid. With Windows, you'll want to download the font package from the x2go project website.  The client has a GUI and it is pretty easy.  If you have standard ssh-key setup, those will be used automatically, just like for all the other ssh-based things in this post.  RDP and VNC protocols are commonly hacked, have poor encrypted network connections (if any) and don't use key-based authentication, so if you must use those, please, please, only do it through an ssh tunnel.  There are lots of guides on the internet for setting up an ssh tunnel for VNC. The ones from Windows using PuTTY are what many people need.  PuTTY does some things odd related to ssh-keys, so beware, but the major ideas for what putty does is fine.   X2go has a set of ssh-keygen and ssh-copy-id tools included on Windows. Use those just like on Unix/Linux systems to create keys for x2go. The x2go ssh tools are standard.  PuTTY uses their own ssh tools, which are different.   I seldom use remote desktops, since *ssh -X* has windows that integrate into my workstation regardless of where the program is actually running and uses secure channel.  Remote desktops are great when traveling and we don't want any data on our travel computers or don't trust the local network in our current location.  Most of the time, people using full remote desktops come from MS-Windows background and don't know about X11forwarding.  Remote desktops don't really work for video playback. Some don't work for audio.

To connect for **file sharing in a permanent way**, Unix systems use something called NFS - Network File System.  It is a system-to-system connection, available for all users of the client system, based on normal Linux/Unix permissions. It is fast and solid.  Works best for wired networking connections and if the NFS server doesn't have a wired connection, then I'd seriously rethink making that the server or get some better networking like powerline or MoAC networking to connect a PC/server in a different part of the house back to the main router using at least GigE. This reduces latency and will make multiple NFS clients happy.
There's also samba, but that really should only be used for Windows and perhaps Android clients. Samba/CIFS doesn't provide standard Unix permissions. It can do some funky things to files and break the Unix security model. Since around 2020, the browsing for Windows CIFS shares from Linux hasn't worked and the best way to setup that connection is manually using the /etc/fstab.  Lots of posts in these forums about doing that.
With NFS, remote storage seems like local storage and can be accessed that way by 99.99999% of programs.  Programmers have to really go out of their way for NFS NOT to work like local storage.

For **file sharing in a temporary way**, there is sftp, scp, rsync/grsync, sshfs.  All of these are based on ssh, use the same credentials, and are considered secure enough for use over the internet.  Most Linux file managers support URLs with sftp:// in them - so you can drag-n-drop files to/from the remote system. If you have lots of files to push to another system, perhaps an entire directory, use rsync. There's a GUI version, but it requires typing just as much, so what's the point?  With rsync, we can script the task and it will behave exactly the same each time.  That means updating files on computer A ---> computer B is just running 1 script as needed.  rsync is smart. It only sends blocks of files that have changed between the source and target.
```
$ sftp remote-user@remoteIP-Address 
```
will connect to a remote system. Normal FTP commands work, so ldir, dir, cd, put, mput, get, mget all work as expected. This isn't by accident. sftp was specifically designed to be a drop in replacement for plain FTP which shouldn't be used since 2002.
```
$ scp  source target 
```
where the source or the target can be local or remote.  The default bash prompt in every terminal window provides the exact format needed for a remote location to be used by scp and rsync.  This isn't by accident.  It makes copying files between systems very easy.  scp was designed to be a drop-in replacement for rcp, which was effectively killed off in the 1990s along with rlogin and telnet.  Windows people don't know much about those, but in the Unix world, they were mainstays of connectivity since the 1970s.
For rsync over ssh, use something like this:
```
$ rsync -avz  source target 
```
An exact example is 
```
$ rsync -avz  ~/TODO/*     romulus:~/TODO/  
```
That will copy everything new from the local machine to a remote machine, romulus, and put all the files in a ~/TODO/ directory. rsync has special meaning for the trailing / on source and target locations.  Just be aware of it.  The '/*' doesn't match any .dotfiles, so if I wanted those included too, I'd use 
```
$ rsync -avz  ~/TODO/     romulus:~/TODO/  
```
Pulling with rsync works too. Just swap the source/target around.  Of course, ssh-keys would need to be exchanged in the opposite direction prior to this working.
```
$ rsync -avz     romulus:~/TODO/  ~/TODO/  
```

There are lots of programs that copy files between systems. The ones based on ssh that I've listed are the most secure and quickly become 2nd nature. Plus, since more Linux file managers support ssh:// or sftp:// URLs, the entire drag-n-drop method is available.  It might be tempting to use something like syncthing or enable a 1-line perl/python/ruby web server to quickly share files, but this isn't secure and only allows pulling, not pushing.  Syncthing seems like rsync with a nice GUI, but it isn't.

On Windows, there is WinSCP, which supports sftp.
I understand the Win10 has an ssh client now, finally.  They also have scp and sftp which can be used in a powershell or cmd.exe window. Just use / rather than \ for paths.  Windows has always supported using / instead for directory separators.

BTW, the sftp-server is setup automatically when we installed openssh in the first paragraph.  It is there and working already. Same for sftp and scp too.  rsync and sshfs are addons - but both are in the normal repos.

And all of these ssh-based tools use the ssh port and ssh credentials, so setting up ssh-keys makes using them all crazy fast AND secure.

Getting into all the NTP, HTTP, SNMP, SMTP and thousands of other methods would take too long.

I've assumed that connecting 2 laptops isn't the only part of the network. There is a router, so that they can find each other automatically. Without a router, having just 2 computers talk to each other involves setting a route to/from each computer to the other one, manually.  A used $5 router makes this trivial - just plug them both into different ethernet ports and routing is handled along with DNS, dhcp and perhaps some other things to make life easy, but less secure.

---

### Post by validust on 2022-01-14
Thank you very much for your response, The Fu!
My ambiguousness comes with my ignorance. I wanted to be able to move files between the two laptops. That I can do now, and since I came upon many other non-CLI-speaking searchers while searching for a solution, I wanted to post a way to do it that works. 
Your response is much appreciated. Not to say overwhelming. I have much to learn.

---

### Post by TheFu on 2022-01-14
> **validust said:**
> Thank you very much for your response, The Fu!
My ambiguousness comes with my ignorance. I wanted to be able to move files between the two laptops. That I can do now, and since I came upon many other non-CLI-speaking searchers while searching for a solution, I wanted to post a way to do it that works. 
Your response is much appreciated. Not to say overwhelming. I have much to learn.

Everyone started somewhere. The more I know, the more I know is yet to be learned.

Pretty much all system-to-system connections begin by installing openssh on both sides.  After that, almost anything is possible, securely.  Having a file manager that supports sftp:// URLs - which almost every Linux file manager does - just makes accessing storage everywhere fit into the MS-Windows model.

If you really want to make that access easier, setup static IPs (or DHCP reservations) for all the systems on the LAN and setup ssh-keys on all client devices, pushing the public key to all the servers.  2 steps:

**Step 1:**  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

**Step 2:**  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
 The "username" is optional and not needed if the same between the client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup inside the /etc/hosts or configured in the ~/.ssh/config file.

Do that once per client -to- server connection and you'll not be prompted to enter a password for those connections more than once per login on the client machine. The ssh-key has to be unlocked once per login. After that, it is available and automatic. Crazy secure and crazy convenient.

Those 2 steps work on any Unix-based OS.  Win10 supports Step 1. MSFT didn't think to port the ssh-copy-id tool to Windows. Boooo.  There are manual ways to accomplish the xfer and appending of the client key, but those are all a pain and prone to mistakes and mis-setting file permissions.  ssh cares greatly about permissions of specific files. They cannot be too open or too closed - have to be just right.

---

### Post by Morbius1 on 2022-01-14
> **validust said:**
> I wanted to be able to move files between the two laptops. That I can do now, and since I came upon many other non-CLI-speaking searchers while searching for a solution, I wanted to post a way to do it that works. 

I have a couple of suggestions if that is OK:

[1] I would edit the original subject header to include the word **Tutorial** or maybe **HowTo** so that folks do not think this is a request for help. 

Maybe even specify the protocol like: ***[COLOR="#0000FF"]Tutorial: Connecting two laptops on one LAN using SSH[/COLOR]***

You might even want to place this in the "Tutorials" subsection of the forum/

[2] Your Tutorial is very MATE specific.

There is no "Connect to Server" dropdown in Nautilus. Instead it's under "Other Locations" at the bottom of the file manager where the user is expected to know the syntax. You might want to add something about this and recommend a template like ssh://server or ssh://username@server.

I don't know this as a fact but I suspect there are more Gnome users than MATE users in this forum.

---

### Post by validust on 2022-01-14
So true, Morbius1! Thank you! I have tried to wiggle in the pertinent changes. Hopefully the result isn´ too foggy.

---

### Post by mIk3_08 on 2022-01-14
> **TheFu said:**
> "Connect" is ambiguous.  How did you want to connect?  There are a number of different protocols which allow connecting 2 or more systems.
[LIST=1]
[*]remote terminal 
[*]remote window/GUI program 
[*]remote desktop 
[*]file sharing (permanent) 
[*]file sharing (temporary) 
[/LIST]
Then there are a bunch of client/server "connections like NTP, HTTP, SMTP, SNMP, - literally, there are thousands of "connection" possibilities between systems.

For remote terminals, I use ssh.  Install openssh (meta package) on both the client and server, then just open a terminal and run
```
$ ssh remote-user@remoteIP-Address
```
There are lots of ways to make this more secure AND more efficient, but that's the basic method. No downloading any special GUI program needed.  Any terminal that already exists on your system can be used.

To run a remote GUI program on a different system and have that program shown on the system you happen to sit behind, use 
```
$ ssh -X remote-user@remoteIP-Address name-of-program
```
The "name-of-program" needs to be the actual name of the program, not the menu name.  So, "Printers" is probably "system-config-printer". Also, if the program isn't in the PATH for the "remote-user", then the full path to the program is required.  Simple command, but crazy useful.  All the traffic will be tunneled through the ssh connection and some other things are automatically setup for us. If this doesn't work, it is possible the sshd_config file on the remote system doesn't allow X11Forwarding. The default was to allow it, but that might be changing in newer releases.

To run a remote desktop, we need to ensure it is over a secured connection.  As we learned above, ssh is the way to have both secure authentication AND tunneling.  That means that rdp or vnc connections all need to be tunneled through ssh to be secure. Neither rdp nor vnc servers should allow any connections except from 'localhost'. This little thing will prevent people from using non-secure connection methods. Or just use one of the NX-based desktop protocols which are 2-3x faster than either vnc or rdp.  x2go is one of those.  NX makes use of ssh tunnels, so we only need to have ssh setup, just like all the methods above this imply or state.  Do you see a pattern?  x2go has a client and a server - install the server on the remote system (over an ssh terminal) and the client on the local system. There are x2go clients for Windows, OSX, and Linux and I know the Windows and Linux clients are very solid. With Windows, you'll want to download the font package from the x2go project website.  The client has a GUI and it is pretty easy.  If you have standard ssh-key setup, those will be used automatically, just like for all the other ssh-based things in this post.

To connect for file sharing in a permanent way, Unix systems use something called NFS - Network File System.  It is a system-to-system connection, available for all users of the client system, based on normal Linux/Unix permissions. It is fast and solid.  Works best for wired networking connections and if the NFS server doesn't have a wired connection, then I'd seriously rethink making that the server or get some better networking like powerline or MoAC networking to connect a PC/server in a different part of the house back to the main router using at least GigE. This reduces latency and will make multiple NFS clients happy.
There's also samba, but that really should only be used for Windows and perhaps Android clients. Samba/CIFS doesn't provide standard Unix permissions. It can do some funky things to files and break the Unix security model.
With NFS, remote storage seems like local storage and can be accessed that way by 99.99999% of programs.  Programmers have to really go out of their way for NFS NOT to work like local storage.

For file sharing in a temporary way, there is sftp, scp, rsync, sshfs.  All of these are based on ssh, use the same credentials, and are considered secure enough for use over the internet.  Most Linux file managers support URLs with sftp:// in them - so you can drag-n-drop files to/from the remote system. If you have lots of files to push to another system, perhaps an entire directory, use rsync. There's a GUI version, but it requires typing just as much, so what's the point?  With rsync, we can script the task and it will behave exactly the same each time.  That means updating files on computer A ---> computer B is just running 1 script as needed.  rsync is smart. It only sends blocks of files that have changed between the source and target.
```
$ sftp remote-user@remoteIP-Address 
```
will connect to a remote system. Normal FTP commands work, so ldir, dir, cd, put, mput, get, mget all work as expected. This isn't by accident. sftp was specficially designed to be a drop in replacement for plain FTP which shouldn't be used since 2002.
```
$ scp  source target 
```
where the source or the target can be local or remote.  The default bash prompt in every terminal window provides the exact format needed for a remote location to be used by scp and rsync.  This isn't by accident.  It makes copying files between systems very easy.  scp was designed to be a drop-in replacement for rcp, which was effectively killed off in the 1990s along with rlogin and telnet.  Windows people don't know much about those, but in the Unix world, they were mainstays of connectivity since the 1970s.

On Windows, there is WinSCP, which supports sftp.
I understand the Win10 has an ssh client now, finally.  They also have scp and sftp which can be used in a powershell or cmd.exe window. Just use / rather than \ for paths.  Windows has always supported using / instead for directory separators.

BTW, the sftp-server is setup automatically when we installed openssh in the first paragraph.  It is there and working already. Same for sftp and scp too.  rsync and sshfs are addons - but both are in the normal repos.

And all of these ssh-based tools use the ssh port and ssh credentials, so setting up ssh-keys makes using them all crazy fast AND secure.

Getting into all the NTP, HTTP, SNMP, SMTP and thousands of other methods would take too long.

I've assumed that connecting 2 laptops isn't the only part of the network. There is a router, so that they can find each other automatically. Without a router, having just 2 computers talk to each other involves setting a route to/from each computer to the other one, manually.  A used $5 router makes this trivial - just plug them both into different ethernet ports and routing is handled along with DNS, dhcp and perhaps some other things to make life easy, but less secure. 

You are The Man! TheFu! You're Amazing! Your ideas on how to explain things here in forum always makes the user very simple on how they will do it. You always explain in detailed in every little things you encounter.
You always have the explanation in every situation. I love to support users here in forum like you but my words are limited. My English is not good. :-D  But I'm trying to share my idea in a little way. Maybe someday my words will expand someday, so user can easily understand what I am trying to reach to the concerned user. I hope my english is not bad today. :-D Cheers.

---


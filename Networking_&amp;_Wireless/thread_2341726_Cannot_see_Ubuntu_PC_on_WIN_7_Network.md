---
title: "Cannot see Ubuntu PC on WIN 7 Network"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by kg4muc on 2016-10-31
I have some important files I really need to back up over the network in order to upgrade Ubuntu versions. Currently running 10.04 LTS which does fine for what I need it to do mostly. Problem is that I can't see this machine under the network tab in Win7. It shows up fine on my status page of the router but past that pinging is all I can do. I am running static routes on all my equipment due mainly to some network satellite receivers that need a static address to work properly.

I cn access the internet fine on the Ubuntu machine but not the Windows network.  SAMBA is installed running and configured with the accounts I need shared. This machine worked previously on the same network but was off lined for a few years and the static addresses were implemented since it was last running on the network.

I have tried everything I can think of and research but still no go ! I'm sure it's a simple something, it usually is in these situations.

Any guidance greatly appreciated!


Regards,
Wayne Thomas

---

### Post by TheFu on 2016-10-31
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
EOL for 10.04 desktop was in 2013.

Boot 16.04 using a flash drive, mount the storage and backup the files as needed - probably best the enable file sharing on the Windows machine and drag-in-drop FROM the Linux GUI over to Windows.

Just be certain to update the /etc/hosts file to have entries for any networked machines you want to access. This might not be necessary - just depends on the network architecture.

---

### Post by kg4muc on 2016-10-31
Thanks for taking time to help me !
EOS has certainly been a long while back on my current version :D
Is there a tutorial or any sort of check list I can consult to verify my settings as far as accessing the network are correct since I'm using static routes instead of DHCP? The network setup here is fairly simple consisting of the Comcast gateway, Netgear router and the individual clients.

I will work on what you suggested and try to get the files backed up in order for me to update versions. I just want to make sure that either way I can access the files if by no other means FTP if I have to.

Thanks again for helping

---

### Post by TheFu on 2016-10-31
Don't use FTP.  That protocol should have died in the mid-1990s with telnet.

Use sftp which you get for free by installing openssh-server.  This is part of ssh and provides a swiss-army-knife of network connectivity on Unix systems. There are clients for every networked OS that I know ... even Windows. ;)

I don't know of any check list. The networking is standard, so if the network is setup correctly and name resolution is solved correctly on it, then there won't be any issues.  Of course, MSFT often creates their own standards to make things easy, but that doesn't mean that Unix will support those out of the box.

For example, when you say that you "cannot see ubuntu PC on Win7 network" - that tells me that perhaps you have unrealistic expectations about how networks actually work and expect systems to broadcast they on on a subnet.  MSFT does that. Nobody else does.  All the other OSes expect name resolution to be handled by a server - usually DNS, but you can edit the /etc/hosts files on every system to they know about each other too.  That's what I do, but I only have about 40 devices so it isn't very hard.  For many people, it is just easier to use the IP address to access other systems.

Should point out that Unix has ways to act like Windows, but that means installing other services and configuring them.  Avahi, zeroconf, and samba are examples.

So ... can your Windows machine 'ping' the ubuntu machine by name?  By IP?  And vice versa?  Solve that first.

And please don't use plain FTP ... er ... ever.  [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by kg4muc on 2016-10-31
Thanks for the good information regarding FTP. Basically I only use it within the network to transfer video files from their origin to a storage location. I have tried getting windows to open the samba shares by inputting the ip address in the run command but it can't find it that way either. It's possible I have a different DNS entry on the Ubuntu side than what is entered in Windows. Completely forgot to check that until you mentioned name resolution.. Think I need to look into installing openssh-server. That may simplify things considerably. All I really need is the ability to add and or remove files from the Ubuntu machine when needed so any way I can accomplish that would be fine.

Thanks again for the great info!

---

### Post by TheFu on 2016-10-31
Installing the ssh gets you ssh, scp, sftp, sshfs and tunneling capabilities - all over IP, on a single port, secure from anywhere in the world or on your local network.

Windows clients are filezilla or/and winscp.  Probably others. I know putty has scp included.

I'm kinda confused. How did you expect to move files around without installing any file server programs?

And on other distros, you'd need to open the firewall too.  With Ubuntu, anytime you add a network service, it would be smart to enable the firewall for only the clients you expect and block everyone else.

And don't use plain FTP anymore.  If a hosting company suggests it - that is your clue to leave them, running.  There just isn't **any** good reason to use plain FTP anymore ... unless you are hosting files for everyone in the world, without authentication of any sort.  Ah - there is 1 more reason - RHEL exams require it, but ther are better alternatives to plain FTP that for what RHEL want it to be used for (kickstart servers).

---

### Post by kg4muc on 2016-10-31
Definitely will be installing ssh and soon. As for the file moving what I had intended to do was either view a shared folder via the network tab in WIN and select the needed file and transfer it that way or what I have done in the past is use Windows Explorer to open the shares. I can't get either method to work currently but I can ping the server and I can see it's name show up under the connections tab on my router page

---

### Post by TheFu on 2016-11-01
If you didn't install samba, then the system won't announce on the network "I'm here, I'm here" for Windows to see.  Samba has a place, in a trusted network, with Windows clients. For all other clients, there are likely better choices that are either faster (NFS) or more secure (scp/sftp) and can be used from anywhere in the world to access your files by you.

ssh rocks!  Too bad most Windows-people have never heard about it.  About a year ago, MSFT said they were finally working to add ssh to their new systems.  Haven't heard anything about it since, but I don't pay attention to them anymore. If they are still around in 4 years, I might care.

So, install these things now:```

$ sudo apt install openssh-server fail2ban
```
fail2ban blocks brute-force attempts.
Load either winscp or filezilla on your windows machine.  Open winscp, point it at the ubuntu machine. Be happy.

OR .... you can go the other way.  On Windows, enable file sharing. On Linux, using almost any file manager tool, look on the network for the Windows machine, point-n-click to that storage, drag-n-drop your files between them. Be happy.

Setting up samba can be trivial or very hard.  I don't know why it is hard for so many people, but they seem to have great difficulty that confuses me. ssh is much easier, so I don't bother trying to help people with samba anymore.

---

### Post by kg4muc on 2016-11-01
I have finally managed to get updated to 16.04 LTS and that seemed to have solved my problem of unpredictable Internet access and everything is visible under network tab in WIN 7 now.

Only problem is when I attempt to install open ssh under terminal it prompts me that the command is bad.  Not quite sure what I did or didn't do here but I'm still poking around to find out :)

Thanks for the suggestions!  Get open ssh going I should be golden !

---

### Post by kg4muc on 2016-11-02
I did some further research and discovered nothing really installed like it should and most had fatal errors. I reinstalled 16.04 once again only this time I set up the network prior to the actual install which provided for downloading any third party items and updates it might need. This time I was able to install ssh server without any problems. Still haven't gotten SAMBA working correctly but I doubt I'll bother much with that since ssh is working so fluidly !  The Fu is exactly correct SSH absolutely rocks !

Thanks for all the help , guidance and suggestions ! It's all good now!


King , This Case Is Closed !

---

### Post by TheFu on 2016-11-02
There is a place for samba. It is faster than scp/sftp - because it doesn't have any encryption.

I doubt a reinstall was needed.  Just suspect you are so very new and things that old-guys like me see all the time and don't bother mentioning are catching you with issues.  Honestly can't imagine the network stuff was an issue under any release since 10.04 ... unless the machine is VERY, VERY, VERY new and uses new network chips.

Also - if you have issues with CLI/shell commands, copy/paste the exact command and relevant output here (please use "code tags") - facts beat _descriptions_ always. Often, our descriptions are really interpretations and not correct. That still happens to me.

---

### Post by kg4muc on 2016-11-02
I've gotten to the point with samba that it doesn't accept my password. I right clicked on the folders for the share and the settings were automatically added ( supposedly)
You're correct on the new part. I haven't been working with Linux systems but a year or so and no formal training just what I read and learn by mistake  :)
One other reason I did the reinstall was my mouse no longer worked. NO cursor even shown.  I lightened the load on my laptop by uploading several music,video and still photographs early this AM.  Hopefully later on I can add an additional drive so most of the storage can be on it leaving my primary drive free with just the OS. Hopefully that way updates to a new distro won't chance a loss of important files.  Definitely been and continues as a great learning experience!   Thankfully I have had excellent instruction so far :)

---


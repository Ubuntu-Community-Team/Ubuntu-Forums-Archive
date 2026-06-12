---
title: "Network Two Linux Laptops"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by jeffreyldavidson on 2007-05-05
I have two laptops that both have Fiesty on them. I connect to the internet with them both through a wireless router. I would like to have a shared folder on both to share files but cannot make the connection. Please help. 

Thanks JLD

---

### Post by sudo_nym on 2007-05-05
> **jeffreyldavidson said:**
> I have two laptops that both have Fiesty on them. I connect to the internet with them both through a wireless router. I would like to have a shared folder on both to share files but cannot make the connection. Please help. 

Thanks JLD

Your router's LAN settings might be a little restrictive.

I have a D-Link [wired] router, and although I do appreciate its *internet* security features, I don't need a secure LAN [you might though; that's one major difference between wired and wireless networking].  The built-in defaults were really, ridiculously, unnecessarily secure, but now I have ports 1 to 55555 open to local IPs, ranging from 192.168.0.1 to 192.168.0.254 but only on the LAN, *not* open to the internet.  This makes my life easier, but you might want to open only specified ports and IPs, not a whole range.

I don't know what sort of router you have, or how you'd change its settings, but have a look at firewall settings, how to open ports for local IPs and such.  Pretty soon your Linuxen should have no trouble seeing eachother.

Hope it helps, but do be careful.



Cheers,

Patrick.

---

### Post by jeffreyldavidson on 2007-05-05
I am using a Belkin wireless router. Everything works will with my internet connections and I can ping each laptop but I cannot figure  out how to establish a shared connection. Do I need to use Samba? I thought Samba was just for connecting Linux with Windoze but I cannot get a connection.

---

### Post by sudo_nym on 2007-05-05
> **jeffreyldavidson said:**
> I am using a Belkin wireless router. Everything works will with my internet connections and I can ping each laptop but I cannot figure  out how to establish a shared connection. Do I need to use Samba? I thought Samba was just for connecting Linux with Windoze but I cannot get a connection.

Well, you do need some sort of client/server arrangement, but as you say, Samba might not be the best choice.  Could work though.

Sorry, I don't know anything about remote desktops over SSH, but if you just want to move some files around, gFTP and ProFTPD [client and server, respectively] might be the way to go.  And then there's GProFTPD; a graphical front-end to make configuring the FTP daemon a little easier.  With the basic installation, no special options to set up, you should be able to log-in on the FTP server using your own user-name and password.

I have a Mac, PC, and of course this Linux box, so FTP suits me because it's *not* platform-specific.  Your milage may vary.



Hope it works for you though,

Patrick.

---

### Post by tact on 2007-05-05
I know this is too ridiculously simple (for anyone used to linux and setting things up...  hehehe) but its like this in fiesty...

- Create the folder you want to share.  
- Right click on it.
- Select "Share Folder"    (if this is the first time you will get a dialog box "You must install NFS or SAMBA to share folders).
-  I left the default settings (both NFS and SAMBA selected) and so both installed.

done.

too easy.  :)

---

### Post by liftback on 2007-05-06
Im in the same boat and have tried the simple option above but to no avail. I can make a smb share show up on the pcs but when i try to open any share it tells me that it cannot be found...

It seems to be really difficult to do something so simple as basic file sharing...

---

### Post by jeffreyldavidson on 2007-05-06
> **tact said:**
> I know this is too ridiculously simple (for anyone used to linux and setting things up...  hehehe) but its like this in fiesty...

- Create the folder you want to share.  
- Right click on it.
- Select "Share Folder"    (if this is the first time you will get a dialog box "You must install NFS or SAMBA to share folders).
-  I left the default settings (both NFS and SAMBA selected) and so both installed.

done.

too easy.  :)

That is the easy part...I agree. The problem is getting the other computer to see it. How is that done?

---

### Post by Cheese Sandwich on 2007-05-07
> **tact said:**
> I know this is too ridiculously simple (for anyone used to linux and setting things up...  hehehe) but its like this in fiesty...

- Create the folder you want to share.  
- Right click on it.
- Select "Share Folder"    (if this is the first time you will get a dialog box "You must install NFS or SAMBA to share folders).
-  I left the default settings (both NFS and SAMBA selected) and so both installed.

done.

too easy.  :)

Can the rest of the world access those folders as well, or just local computers?

---

### Post by sudo_nym on 2007-05-08
> **liftback said:**
> Im in the same boat and have tried the simple option above but to no avail. I can make a smb share show up on the pcs but when i try to open any share it tells me that it cannot be found...

It seems to be really difficult to do something so simple as basic file sharing...

Well, I kind of hoped tact's `right-click and share' thing would work for him.  It seemed so simple, and I actually had a similar problem in WinXP; spent days hunting around for CD-burning software, before I noticed the right-click on file/folder > Send To... > CD-RW Drive (E:) menu item in Explorer...  Doh!  And it was right there the whole time.

But as for basic file-sharing being `difficult' in Linux, all I had to do was install three packages, and use them.

I do hope jeffreyldavidson finds something that works for him too [might not be FTP, but something equally clear and straighforward I hope].



Cheers,

Patrick.

---

### Post by unikuser on 2007-05-08
I can mount smb/ftp share from nautilus using File->Connect to Server. I did not find anything similar for nfs. Also smb:// works and nfs:// does not work for me. Found [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430) which is related to this.

---

### Post by sudo_nym on 2007-05-08
> **Cheese Sandwich said:**
> Can the rest of the world access those folders as well, or just local computers?

Just local, if you're behind a router and it's set up properly. You'd have to explicitly open some ports on the router, before anything on the Big Net could see anything on your local net.

NFS and Samba must have options to limit which IPs they'll talk to as well [like 192.168.*.* for local-only stuff].



Patrick.

---

### Post by sudo_nym on 2007-05-08
> **unikuser said:**
> I can mount smb/ftp share from nautilus using File->Connect to Server. I did not find anything similar for nfs. Also smb:// works and nfs:// does not work for me. Found [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430) which is related to this.

Hey, you can do that in Nautilus?  Cool.  Okay, no need to install a[nother] client application then.

As the header thing says, I'm a Xubuntu user, and Thunar, the default file-manager in Xfce doesn't have those kinds of bells and whistles.  So thanks, guess I learned something new today.


Cheers,

Patrick.

---

### Post by tact on 2007-05-10
> **jeffreyldavidson said:**
> That is the easy part...I agree. The problem is getting the other computer to see it. How is that done?

Oh... ok for other linux machines to see the share they click Places>Network> and browse the network.  Or Places> Connect to server   and choose either SMB share or NFS share...  type in server name and share name etc.

For windows machines they just look in network neighbourhood (or equivalent).

I did find that i had to adjust permissions on the shared folder to allow (or disallow as you wish) ability to read and or write.

In case it helps - I created the shared folder THE /home...     ie /home/a_shared_folder   NOT in "my" home folder (/home/my_username)

I put it there because I had changed permissions to secure MY home folders such that no other user can even see my home folder (/home/my_username)  and I did not want to open a hole in that just to share a folder thats inside my /home/my_username tree.

So of course I had to use sudo to create the directory and set permissions so others can read and/or write to it.

If you share a folder via NFS or SMB then you dont need to worry about how the partition is formatted (ext2/3, FAT etc) as this is transparent to all who connect to the folder.

---

### Post by tact on 2007-05-10
> **Cheese Sandwich said:**
> Can the rest of the world access those folders as well, or just local computers?

I am behind a router so only those on local net can see the share...  same as in windows-land shares.  People from other offices in my company can see the share if they are VPN'd in to the local LAN

---

### Post by Huffalump on 2007-05-12
It is easy to right click a folder and select "Share" because Fiesty informed me that I would need to install NFS and/or Samba.  I did both.  Then, after those were installed, I tried to share the folder as an NFS and later as a Samba.  However, I could never open/find the shared folders using my other Ubuntu on the LAN.

So, to repeat the earlier question, once you've easily set a folder to be shared.... how do you accomplish the seemingly difficult task of opening/finding that folder from another machine?

---

### Post by tact on 2007-05-12
Sorry - i have not had the pleasure of testing with another linux box.  just win-boxes and samba, not nfs. After setting up as per previous posts the win-box user goes to their network places, windows network etc...and there is the linux samba share.

some notes:
windows shares can take 15min or more to show up in your (and their) network places.  Even the workgroup may takes so long to appear .... if you open your system log reader utility   (System>administration>system log) and click on file>open then navigate to /var/log/samba then open up the log called log.nmdb... then scroll to the end... see if your (or either, or any)  linux PC has become master browser yet for the workgroup...  

if the network is just the two linux boxes then one of them will become the master browser for the workgroup eventually.  once you see that in the log(s) ...its is live monitoring... then your PCs should see the workgroup, each other and any offered shares.

---

### Post by tact on 2007-05-13
....and by way of a follow up.  In that time before you have a masterbrowser on the windows network:
 - if you open up your Places>Network you will see an icon for "Workgroup" and nothing else.  Not your computer or any other.


...when the browse master is settled:
- then in the Places>Network folder you will see "Workgroup" and also an icon for your own PC (and any others in the same workgroup... as well as any other workgroups).  Double click on your own PC and it will open a folder showing whatever you have shared.

---

### Post by sudo_nym on 2007-05-13
[sigh...]

No offense, but this `easy' method is looking more and more complicated with every post.

How about this;[LIST=1]
[*]Install the proftpd package from the Ubuntu repositories.
[*]Reboot.
[*]Launch any FTP client [including Nautilus], on any machine on your LAN, and point it to the server machine's IP, using your own login name/password for that machine.
[*]There is no step 4.  You're done.
[/LIST]

You can turn it on or off from the command line;
sudo /etc/init.d/proftpd start
sudo /etc/init.d/proftpd stop

It's on by default, so you shouldn't usually have to bother with this.  Might be a good idea to turn it off though, before you head out to an internet cafe or something [I *think* it will refuse anonymous logins by default, but can't say for sure].

If you want more control and config options, you can install the GProFTPD package; a graphical front-end for the daemon.

> **tact said:**
> some notes:
windows shares can take 15min or more to show up in your (and their) network places.
Proftpd is ready to accept new connections as soon as it's launched.



And that's about it,

Patrick.

---

### Post by sudo_nym on 2007-05-13
Sorry if that last post came off a bit grouchy.  I've said pretty much all I had to say about this anyway.

Oh, and please excuse the messy desktop.  I wasn't expecting company.



Patrick.

---

### Post by tact on 2007-05-14
> **sudo_nym said:**
> Sorry if that last post came off a bit grouchy.  I've said pretty much all I had to say about this anyway.

Oh, and please excuse the messy desktop.  I wasn't expecting company.



Patrick.

No need to apologise - I didnt think u were at all grumpy.  Whats to be grumpy about?  No one is arguing one way is better than another right?  All are just trying to communicate ways.

I mentioned the way samba works, quite easy really if you just want to share folders between machines.  I was impressed how when I right clicked to share a folder (first time) I was prompted to install NFS or SMB and so let both install.  I am in a sea of windows users at my office so I will be forced to use "windows networks" thus SMB is my only real option.   

The rest of what I wrote  is not the "simple method" getting more complicated.   More like a "just for info" how you can complicate it for yourself if you like.  (eg, some weeks back me deciding to set permissions so my home folders are invisible/inaccessible to any other user on my laptop and wanting to put the "shared" folder outside of my home folders)

Some of the rest (how it takes 15 min or more for a browsemaster to show its face, and workgroups and shares to appear etc) is just "how windows networks works".  If you want to share folders with windows users in a windows network, without forcing them to install SSH or other programs...  then SMB and waiting for shares to show up is the only show in town.

The original poster is talking about sharing between two linux boxes...  I would have thought following what I did above, and using NFS (thats the unix way to share as opposed to SMB and windows) would be sensible.  But I cannot elaborate as I never used NFS.  Only SMB and such.   Wish I had another linux box to try NFS with.  But alas all my colleagues are using XP

Cheers

---

### Post by sudo_nym on 2007-05-15
> **tact said:**
> No need to apologise - I didnt think u were at all grumpy.  Whats to be grumpy about?
Well thanks for saying, but I was feeling kind of rough at the time.  Had nothing to do with you, or this thread though [1].

> No one is arguing one way is better than another right?  All are just trying to communicate ways.No, and in fact my first choice was Hotline, because it worked so well for Mac and Windows.  The chat features also made it very easy to move my passwords and stuff from from one machine to the other, without leaving it all sitting around in plaintext, on disk [don't know if that sounds like paranoia or regular old dumb-mistake-prevention, but it did work out pretty well].

Unfortunately, I've had no luck finding a decent HL client or server for Linux, so I can't recommend it.

Hmm.  No that's not quite true; hxd looked like a pretty good server, but either disallowed transfer of whole directories, or didn't understand the newer protocol.  Of course, I'm not too clear on the compile-time options for hxd, maybe there's a way to enable that kind of thing [and who's sounding complicated now, I wonder...?  ;-) ].

Might be worth a look though, if your office is mostly M$ powered.  Starts up fast, uses very little resources, and the software averages less than 1 MB on disk, without sacrificing features.

Oh, and the Mac/PC versions ship in binary form.  ;-)

> [...]
The rest of what I wrote  is not the "simple method" getting more complicated.   More like a "just for info" how you can complicate it for yourself if you like.No, and I could probably go into ridiculous detail on some subject or other, while completely losing track of the `simplicity and ease of use' aspects that made me like it in the first place.  Not that you did that, but I might have in the way I read it.  Also, maybe, in what I wrote just now...

Umm, okay nevermind the Hotline stuff.

> (eg, some weeks back me deciding to set permissions so my home folders are invisible/inaccessible to any other user on my laptop and wanting to put the "shared" folder outside of my home folders)Oh hey, I'd meant to ask you about that;

Would you get a similar effect, setting execute permissions on directories, but not read?  I think the execute bit means you can `pass-through' a restricted directory in a specified path, but can't get any listings on the way.

I guess someone could still `lucky-guess' a filename contained in a folder like that, but even if they did, couldn't download the file itself if read is turned off for that as well [kind of like a 403-Forbidden, as apposed to 404 from a web server].  So any subdirectories you wanted to share could be made readable, along with their contents.

Of course, what you've already done sounds like a much simpler, and generally cleaner approach than this one.

[list=1][*]Been struggling with some very Windows-oriented hardware, including a wireless card that's not essential to my well-being or anything, but would be nice to have around if it worked.  But the good news is, I just noticed Xubuntu has no trouble handling all functions of my Xircom dual-purpose ethernet/56K modem card.  Handy, because I have several resumes to FAX.

Ah, and dialup networking was supposed to be the hard part...[/list]



> Cheers

To your health,  :-)

Patrick.

---

### Post by tact on 2007-05-16
> **sudo_nym said:**
> 

Oh hey, I'd meant to ask you about that;

Would you get a similar effect, setting execute permissions on directories, but not read?  I think the execute bit means you can `pass-through' a restricted directory in a specified path, but can't get any listings on the way.
[...]
Of course, what you've already done sounds like a much simpler, and generally cleaner approach than this one.


Have never tried what you mention (the execute bit thing).  It might work.  :)    As you also note - what I have done is simple and clean and works well for me.  No complications.

Another aspect to putting my "shared" folder outside of my home directories - I only ever use the shared folder as a temporary repository.  I stick copies of files there just long enough for those who need it to log in and grab a copy - or to log in and deposit a copy of their document/file for me to grab.  Then I empty the shared folder again.  ie. nothing ever lives there long at all.

I back up my home directories totally and don't really want what maybe lurking in the shared folder to be backed up with the rest of "home".  It would be just needless duplication.

But thats how I organised my stuff.   Someone who works differently may put a lot of stuff in a shared folder and leave it there forever (kinda like a poor man's ftp server) may be happy to have it backed up too.  :)

---


---
title: "New to Ubuntu Server"
date: 2023-06-16
forum: Networking &amp; Wireless
---

### Post by lwalper on 2023-06-16
I'd like to set up a home file server and have installed Ubuntu Server. I'm at the CLI with a blinking cursor. Where do I go from there? Is there a reference manual somewhere on where to begin? What's the Windows equivalent for ipconfig /all? How do I ping my router? That sort of simple stuff ...

---

### Post by TheFu on 2023-06-16
> **lwalper said:**
> I'd like to set up a home file server and have installed Ubuntu Server. I'm at the CLI with a blinking cursor. Where do I go from there? Is there a reference manual somewhere on where to begin? What's the Windows equivalent for ipconfig /all? How do I ping my router? That sort of simple stuff ...

If you are this new to Linux, you'd be much better off installing a desktop distro and using that as a file server.  The server distro is meant for server admins, not people completely new to linux.  It has a very steep learning curve already and without a GUI, it will be 20x harder.
Any "server" program can be installed onto a desktop installation, so this doesn't impact that at all.

As for where to get help, there are literally thousands of places.  help.ubuntu.com has guides for the most common things.  There's a desktop guide and a server guide there.  There are 20+ books.  Thousands of youtube videos, hundreds of blogs, all about doing things on Linux and Ubuntu Specifically.
The 22.04 server documentation is here: [https://ubuntu.com/server/docs](https://ubuntu.com/server/docs)

If you like, you can ignore my suggestion to install a desktop version of Ubuntu and stick with the CLI only server.  That's perfectly fine, but nobody will be able to teach you exactly what to type. Your system and needs are slightly different from ours, so exactly what we would type on our systems will be different for you on your system.  

Anyway, for people who want to become server admins, they need to learn about 200 commands and where to look up all the options those commands take to achieve what they need.  The commands are in /usr/bin, and /bin and /sbin and /usr/sbin on your system.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is a book that will teach Linux CLI in the correct order, since simple ideas grow into more and more complex solutions.  Learning in the correct order will make your path quicker overall.

There are manpages for each one of the commands which has a summary at the top and gets into more specifics as you read deeper into each manpage file.  Start with **man man** to learn how to use manpages.

BTW, there are many different protocols that can be used by a file server. Which one you should use would depend.  You may want to use 2 or three of these protocols to make access from different clients easier and secure.  

For example, access from anywhere in the world over your WAN connection to the internet can be provided using the sftp protocol. This uses ssh for authentication and the default encryption is considered highly secure.  Most Linux file managers have sftp support built in, so accessing files on a different machine is a drag-n-drop thing.  Android has a number of sftp clients. I use Ghost Commander, but there must be 20 others.  MacOS definitely has programs for sftp, I haven't used anything from Apple in over 10 yrs, so don't know the names.  MS-Windows has a few good sftp clients - FileZilla and WinSCP come to mine. All these options also have CLI sftp clients, but I suspect you'd be happier with a GUI.
There's also the sshfs, which individual users can use to access storage from anywhere in the world, provided ssh is enabled and access isn't prevented. sshfs used ssh credentials, ssh encryption, and I fear only Unix-like OSes can act as clients, though there may be an MS-Windows port by now. IDK.  

If the client systems are all MS-Windows and on the same LAN, then you probably want to use CIFS. That implementation is via samba. There are all sorts of samba how-to guides, including at help.ubuntu.com.  This protocol is what MSFT has used between clients and servers they make for decades, but there are new versions for Win10 and later.

If the client systems are Unix-like (MacOS, Linux, BSD, Unix) and on the same LAN, then you probably want to use NFS.  This is a server to server storage connection and the remote storage is mounted by the system admin for all users to access just like local storage.  NFS has been around longer then CIFS and is extremely stable.  NFS has been the fastest remote storage protocol for decades, though samba isn't far behind anymore.

Or are you trying to share media and really would be better off with a media server, perhaps Jellyfin or Plex or Kodi?  There are a few other choices. I use Jellyfin and Kodi. Started with XBMC about a decade ago.

Or do you want files to sync automatically between devices and the server?  Perhaps OwnCloud, NextCloud, SeaFile are what you want?  Been using NextCloud for 3-4 yrs (I don't really recall how long).  It fits a need for notes, lists, for me. There are lots of addons for nextcloud for photos, music, videos, documents, calendars, contacts, etc.  I use a photo gallery that pulls the GPS from the photos and places them all on a map. Plenty of "cheese" to see travel photos in a completely different way, without uploading details of your life to a cloudy service that will suck your privacy away and sell it.

There are lots of options. Just depends on your needs.
So, which "file server" protocol fits your needs?  I'm fairly certain I forgot a few.

---

### Post by TheFu on 2023-06-16
>  ipconfig /all? How do I ping my router? 

Try:
```
ip a
ping {ip address to router}
```

But if you are running Ubuntu Server (or any Linux server), you'd be expected to know this.  Do yourself a favor. Install a Linux Desktop distro instead, use as many CLI/shell commands as possible, and perhaps in 6-12 months, with hard learning, the server edition would make more sense?

---


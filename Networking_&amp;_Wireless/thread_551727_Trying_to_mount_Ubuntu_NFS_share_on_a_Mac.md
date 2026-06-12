---
title: "Trying to mount Ubuntu NFS share on a Mac"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by joehack on 2007-09-15
Hello

After struggling a couple of hours trying to mount an NFS share, maybe someone can give me a hint.

Server: Ubuntu 7.04
Client: Mac OSX 10.4.10

GID/UID are not matching (I should fix that one day)

Here is the /etc/exports
```

/stuff          192.168.1.0/255.255.255.0(rw,all_squash,anonuid=1000,anongid=1000) 192.168.2.0/255.255.255.0(rw,all_squash,anonuid=1000,anongid=1000)

```
My idea is to map all requests to uid/gid 1000.

When I try to mount (Apple-K) the Finder tells me: 'Could not connect to ther server because the name or the password is not correct'
The kern.log of Ubuntu tells me
```
Sep 15 21:24:49 reykjavik kernel: [10061.846321] nfsd: request from insecure port (192.168.1.100:50737)!
```

Any ideas?

Thanks!

Jochen

---

### Post by Trismegister on 2007-12-13
According to [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) you need make your export 'insecure' also.
I am just about to try this too when I get over to my Mac box!

---

### Post by Trismegister on 2007-12-13
Well, it seems to work to some extent.
Despite the rw proprty the Mac box isn't able to rename files or directories.
We can read files though ... hohum :-)
/home/<directory_name>       192.168.1.0/24(rw,insecure,no_subtree_check,anonuid=1001,anongid=1002)

---

### Post by bobosky on 2008-01-08
Okay. I am very new to all this so please give me a great deal of detail.

I have two PowerBook G4s on a wireless net with my Ubuntu 7.10 on the net work with an Ethernet cable. 

I have all my external hard drives plugged into the Ubuntu box and I want to be able to access them from the two laptops over the network. This seems to be what you guys have done but I would need to step by step walk through on how to make this work. 

Thanks for you time!

bobo

---

### Post by Eiríkr on 2008-02-22
> **Trismegister said:**
> Well, it seems to work to some extent.
Despite the rw proprty the Mac box isn't able to rename files or directories.
We can read files though ... hohum :-)
/home/<directory_name>       192.168.1.0/24(rw,insecure,no_subtree_check,anonuid=1001,anongid=1002)

I get this too -- and it's absolutely baffling.  I've got UIDs and GIDs mapped using the "map_static=[filename]" option in /etc/exports (NB -- you need nfs-user-server to use this option), and while [font=courier]ls -ln[/font] and [font=courier]ls -l[/font] from the Mac side confirm that I'm getting the proper UIDs and GIDs, I still cannot write.  I've got the "rw" option in /etc/exports, and I've even tried using "mount -t -o rw ..." to specify in the mount command, but no go...

Anyone with other hints?

TIA,

Eiríkr

---

### Post by Eiríkr on 2008-02-23
Fixed my previous issue -- duh, should've checked the logs first thing, I had added the option "nohide" to my /etc/exports file previously and didn't think to check after swapping out [font=courier]nfs-kernel-server[/font] for [font=courier]nfs-user-server[/font].  

[font=courier]Feb 22 21:56:08 Zephyrus nfsd[7579]: Unknown keyword "nohide" in export file[/font]

Once I found that entry in /var/log/syslog, removed the offending option, and restarted NFS, pow -- my NFS shares are writable from OSX!  Moral of the story: **Remember, kids, if something doesn't work right, *always* check your logs!**

[color=white]added keywords: os x[/color]

--------------------------------------------------------------------------------

**About UIDs and GIDs -- **

You're really **much** better off using proper ID mapping than the [font=courier]anonuid / anongid[/font] cludge, unless you *only* have a single-user setup.  And I've seen some folks working on mapping all client UIDs and GIDs to 0 -- this is the root UID, and mapping everything to that **is a Very Bad Idea&#8482;.**  There, you've been warned.  :)

The challenge with ID mapping is that the [font=courier]nfs-kernel-server[/font] package, the default NFS server for Ubuntu at present, *has no means for doing this*.  Despite lots of documentation findable online and even the man page itself describing how having matching UIDs/GIDs on all client and host systems is often times undesirable and commenting on the need to map, the default Ubuntu package cannot do this.  

The solution is to fire up synaptic or apt-get and pull down the [font=courier]nfs-user-server[/font] package, which *can* handle UID/GID mapping.  Here's my /etc/exports file by way of sample:

```
# Zephyrus exports to Boreas (Gutsy):
/data   Boreas(rw,no_root_squash,insecure)

# Zephyrus exports to Odysseus (OSX): (mapping requires nfs-user-server)
/data   Odysseus(rw,no_root_squash,insecure,**map_static=/etc/nfs/Odysseus.map**)
```

I've got two clients here, the one another Ubuntu machine and the second an OSX iBook.  The two require slightly different options, so I define two separate NFS shares, each one specific to the client.  (Note that I'm running DNS and so use the hostnames; you could also run DNS, or specify the hostnames instead in your [font=courier]/etc/hosts[/font] file, or just use IP addresses as seen in joehack's example at the top of this thread.)  Here's a run-down of the options involved:

[list][*][color=blue]rw[/color]   --   Read/write.  Pretty straightforward.
[*][color=blue]no_root_squash[/color]   --   Allows for things like [font=courier]sudo mkdir blah[/font] and other root-based file operations in shared directories, when accessed from the client.  Not required for casual users.  
[*][color=blue]insecure[/color]   --   Tells nfsd to use an insecure port (not one of the first 1024).  Things I've read online suggest that Mac's nfs client requires this; it can be useful for Linux clients as well for those folks browsing the [font=courier]nfs:/[/font] space using Konqueror, for instance. 
[*]**[color=blue]map_static=/some/directories/filename[/color]**   --   This is the kicker for the successful Ubuntu host --> Mac OSX client connection.  This tells nfsd to map UIDs and GIDs using the map file indicated by the path after the equals sign.  There are other ways of mapping IDs (read the man page for [font=courier]exports[/font] for details), but this is probably the easiest.  [/list]

And here's my Odysseus.map file for reference.  I think the map file can be anywhere on the filesystem that the nfsd process can access, so no specific need to put it in /etc/nfs/ if you don't want to.

```
# NFS UID and GID mapping for client Odysseus
#       remote          local
uid     501             1000
uid     502             1001
gid     100             100
gid     501             1000
gid     502             1001
```

The file format is pretty straightforward.  Here I've got two users each on the Ubuntu host and the Mac client, and one group (users, which I'm using together with the [font=courier]setgid[/font] permissions bit on my /data directory to set up an easy communally shared file server [more below]; even though the GID # is the same on both my Ubuntu and Mac machines, I found I had to add it to the map file or it wouldn't work).  Depending on your setup, change the values included as needed.  One easy way to figure out what ID numbers you need is to run the command [font=courier]id username[/font] on the client and host machines.  Output should look something like this for an Ubuntu machine:
```
admin@Zephyrus:~$ id username
uid=1001(username) gid=1001(username) groups=1001(username),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),100(users),104(scanner),106(fuse)
```

So after figuring out what UIDs and GIDs you need to map to and from, and entering all that in the appropriate map file(s) and entering the pathname(s) in your [font=courier]/etc/exports[/font] file, restart nfsd like so: [font=courier]sudo /etc/init.d/nfs-user-server restart[/font].  Now try [font=courier]mount -t nfs servername:/path/to/share /path/to/mount[/font] from your Mac OSX client to make sure all is well.  If something isn't working, **check your logs** ([font=courier]less /var/log/syslog | grep nfsd[/font]).  Then try again.  This setup described here should get things working.  :)

--------------------------------------------------------------------------------

**About easy GUI-based NFS share access from a Mac OSX client -- **

Most of the online materials I've found that discuss setting up an OSX client for NFS shares go through the cumbersome process of configuring via NetManager.  The downside I discovered to this, particularly for iBooks, is that the Finder will rather ungracefully hang when I'm out somewhere else and it tries to access the shares defined for my local home LAN.  Plus, the NetManager settings are essentially hard-coded in a way, so any time I make changes to my server setup, I have to replicate them in my iBook's NetManager configuration.  How tedious.  

I stumbled across a much more elegant setup a while back (incidentally, when researching how SMB broadcasts its presence) -- use **Avahi / Zeroconf / Bonjour**.  [Avahi](http://en.wikipedia.org/wiki/Avahi_%28software%29) is the Linux daemon; [Zeroconf](http://en.wikipedia.org/wiki/Zeroconf) is the spec; and [Bonjour](http://en.wikipedia.org/wiki/Bonjour_%28software%29) is what Apple calls its implementation (formerly "Rendezvous").  Setting up Avahi on your Ubuntu NFS server to broadcast announce your NFS shares can greatly simplify GUI access from your Macs, and also potentially simplify how your /etc/exports file is organized.  There are a couple useful links [post=4059639]here[/post] in one of my previous posts which you should read.  

Once you get Avahi installed and running on your Ubuntu server machine, open a terminal and cd over to /etc/avahi/services.  There shouldn't be much of anything here to begin with, so start off by typing in [font=courier]sudo vim nfs.service[/font] (pick your editor of choice; I just like vim :) ).  Any config files for announcing services via Avahi *must* be in this directory (or linked to from it) and *must* have the extension [font=courier]service[/font].  Now type in something like this:

```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name>[color=blue]Zephyrus Shared Music[/color]</name>
  <service>
    <type>[color=blue]_nfs._tcp[/color]</type>
    <port>[color=blue]2049[/color]</port>
    <txt-record>[color=blue]path=/data/shared/Music[/color]</txt-record>
  </service>
</service-group>
```

The **black** text should be identical on your end; change the **[color=blue]blue[/color]** as needed to suit your own setup.  Also note the underscores in the <type> tag -- these are required.  The port is the NFS port used when you've got the [font=courier]insecure[font] option specified in your /etc/exports file, so that might need changing.  And obviously you'll need to specify your own path to your NFS share.  One caveat here is that, as best as I can figure, **you can only specify one share per service file**.  The Avahi daemon for Linux is still a young project, and documentation is limited, but I expect better docs and software to help configure daemon options will appear in due time.  

Once you've got your service files in place, restart the Avahi daemon by typing in [font=courier]sudo /etc/init.d/avahi-daemon restart[/font].  Then go to your Mac machine, open a Finder window, and click the Network globe thingy in the upper left.  You should now have a "My Network" folder here, which will contain whatever NFS shares you've specified.  And the nice thing is that **this is a purely dynamic setup** -- automount takes care of mounting automagically via the special Network folder, and the the Finder won't hang now when you go somewhere else and happen to accidentally try to access a non-existent share, unlike the NetManager setups I've often seen described online when researching how to do this.  

I mentioned earlier that this can simplify your /etc/exports file somewhat.  The trick here is the <path> tag.  As you see further above, my exports file just shoves out the whole /data directory.  Meanwhile, my Avahi service config file here only broadcasts one subdirectory, so that's all the GUI user will see (you can also see these via Konqueror by typing [font=courier]zeroconf:/[/font] into the address bar).  That's also all the GUI user can access.  :)

**But --** the whole [font=courier]/data[/font] share is still available for anyone to mount via the CLI, so be forewarned that this simplified /etc/exports file approach is not a good way to limit access to any sensitive data.  You **will** need to spend some time setting up proper file permissions to ensure that no one who shouldn't can mess with your files.  For instance, one of the subdirectories I advertise via Avahi is a user's documents folder, at [font=courier]/data/[username]'s Docs[/font].  Although anyone on my LAN can *see* this directory in any zeroconf-enabled browser (like Konq or the Finder), I've set up permissions so only certain users can actually *open* the directory to see the contents -- anyone else just gets an error that they don't have the required permissions.  In this case, I did this by typing in [font=courier]sudo chmod 750 /path/to/directory[/font].  This way, the owner (the first digit) gets full read/write/execute permission, group members (the second digit) get read-only and execute (needed on a directory so you can open it), and anyone else (the last digit) can't do anything to it (except root, of course).  Another useful trick for directories shared within a group is the [font=courier]setgid[/font] bit, which I've set on the above-shown Music folder by typing in [font=courier]sudo chmod 2770 /path/to/directory[/font].  The 2 on the front ensures that any files or directories created within this directory are created with the same group ID as the directory itself (after the 2 come the usual user, group, and other permissions).  Note also that **any binaries executed with the [font=courier]setgid[/font] bit set will *run* with the permissions of the file's group**, so **make sure to choose an unprivileged group** when setting up your shared groups.  Wikipedia has a very useful article on [file system permissions](http://en.wikipedia.org/wiki/File_system_permissions), particularly the section [Notation of traditional Unix permissions](http://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions), which I'd recommend reading.  

--------------------------------------------------------------------------------

Anyway, that's a *veeeery* long post, but then again it represents about two weeks of off-and-on research on my part.  I certainly hope it helps other folks get their Ubuntu - Mac OSX sharing set up more easily.  :D

Cheers,

Eiríkr

---

### Post by Wulfrunner on 2008-04-28
I was getting incredibly frustrated with this because I kept getting an "insufficient privileges" message every time I tried to do something on the mac. If you are troubleshooting, make sure you tell Finder to "unmount" your network share every time you make a change to it -- otherwise the old settings persist and you get problems.

---

### Post by sorgud on 2008-05-25
Eiríkr
Great guide. I could mount nfs my home directory on my macbook.
Two commentaries.
1) I couldn't use avahi to make the connection appear "automagically"
Seems that there is a "feature" missing in Leopard.
"This Function seems to be now broken in Mac OS X 10.5. A workaround is posted at [http://www.macosxhints.com/article.php?story=20071116042238744](http://www.macosxhints.com/article.php?story=20071116042238744)
"
But I couldn't make the patch work.
Instead I use in Finder, GO-> Connect to Server and there:
nfs://servername/directory_shared
Seems that I had to use netatalk+avahi.
2) For sharing music, is simpler. I installed mt-daap on the Ubuntu box
I follow the instructions in:
[http://dotnet.org.za/matt/articles/48417.aspx](http://dotnet.org.za/matt/articles/48417.aspx)
And then the iTunes gets all the tracks in the ubuntubox, without mounting the whole directory. It just get the audio stream.

thanks anyway for that guide
talueguito
raul

---


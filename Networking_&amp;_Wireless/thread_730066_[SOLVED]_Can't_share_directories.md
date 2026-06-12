---
title: "[SOLVED] Can't share directories"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by keithclark on 2008-03-20
For the life of me, I cannot share directories between two Ubuntu machines!

If I try NFS, they never show up.

If I try SMB, they show up but I can't log on to them.  I cannot figure out the password.  It is not the one that I log in with on either machine.

Thoughts?

Keith

---

### Post by Eiríkr on 2008-03-20
**For NFS** -- Nautilus, your standard Ubuntu file browser, **cannot** browse NFS shares -- they must first be mounted to the local filesystem, and only *then* may they be viewed with Nautilus.  
```
sudo mount -t nfs SERVER:/SHARE /MOUNTPOINT
```
See [font=courier]man mount[/font] and [font=courier]man nfs[/font] for more options and details.  Note that the numerical user IDs and group IDs for the client and server machines *must* match in a simple setup such as yours, or you'll get very wierd permissions behaviour.  You can check numerical IDs by running the following command:
```
id USERNAME
```

**For Samba** -- You must also run the following command to add users to the Samba user access list.
```
sudo smbpasswd -a USERNAME
```
Then type in the password you want at the prompt.

**For even easier sharing that works in Nautilus too** -- just make sure you have the [font=courier]ssh[/font] package installed on both machines.  Then in the Nautilus location bar (hit Ctrl+L or click View -> Location Bar if it's not visible -- the Gnome devs mysteriously decided to hide it by default), type [font=courier]sftp://IP.ADD.RE.SS[/font], replacing the caps with the IP address of the machine you're connecting to.  

Cheers,

Eiríkr

---

### Post by keithclark on 2008-03-20
Thanks for the reply!  Too complicated.  Maybe I'll just use ftp with my website, way easier.

Keith

---

### Post by Eiríkr on 2008-03-20
What exactly are you looking for?  NFS can indeed be complicated to set up, but from what you've described, you're only missing one step before your apparently mostly-working Samba configuration should be good to go.  And the last option is almost painfully simple, and is already a flavour of FTP anyway.  (As an added bonus, if you have hostname resolution figured out [either via DNS or the old-fashioned [font=courier]/etc/hosts[/font] file way], you can use the hostname instead of the IP address in the location bar.)

---

### Post by keithclark on 2008-03-20
I have 5 machines in the house and I just want to share directories between them in a simple fashion.

I tried your recommendations to no avail.  They don't see to work on my network and I'm not sure why.  The machines just don't see each other.  I can ping them fine, but that is about it.

I had it once that I could see the directory being shared via smb, but then it disappeared.  Very unpredictable.

Keith

---

### Post by keithclark on 2008-03-20
Hey, success with the ssh method!!!!  Thanks for the help!  I just left it for about 5 minutes and tried again with no issues.

Keith

---

### Post by Eiríkr on 2008-03-20
Have you tried installing [font=courier]ssh[/font] and browsing via [font=courier]sftp://[/font]?  You should see an "Authentication Required" dialog the first time you do this, prompting for a username and password with the option to either forget the authentication, or remember it forever (adding it to your Gnome keyring) for automatic login next time around.  If this doesn't happen, you've likely got either a firewall in the way, or some funky network issues that should probably be resolved.  SSH and sftp are a very straightforward means to sharing, and not much can go wrong.  

Samba, meanwhile, can be quirky, in part as it's a huge and complicated program, and in part as things change from version to version in the quest to keep compatibility with Windows and its arbitrary wierdness.  By "see the directory being shared", where do you mean?  In Nautilus, click Go -> Network, and you should see a Windows Network icon; opening this will show a similar icon with the name of your workgroup; opening this will show the various workgroup member computers; opening one of those will show the shares on that computer; opening a share will finally prompt for login and password and then give you access to the files.  Sometimes opening the workgroup will produce an error about being unable to display all files; I've seen this on my end from time to time as I've changed my smb.conf file, but I haven't been able to figure out exactly what's doing it.  Anyway, if that happens, typing [font=courier]smb://HOSTNAME[/font] into the Location Bar should do the trick.  If that fails, try the IP address instead of the hostname.  If *that* fails, you've got a) a firewall in the way, b) a broken smb.conf setup, or c) some other network problem.

---

### Post by Eiríkr on 2008-03-20
Oh hey cool, glad to read it!  :D  Your post must have come in right as I was typing in mine.  So if sftp does what you need it to and your issue in this thread is fixed, please remember to also mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---


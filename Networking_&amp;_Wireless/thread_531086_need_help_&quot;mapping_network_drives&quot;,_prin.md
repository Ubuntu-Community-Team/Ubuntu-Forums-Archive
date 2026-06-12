---
title: "need help &quot;mapping network drives&quot;, printer for law school"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by amisus on 2007-08-21
I'd really like to use Ubuntu on my notebook for law school, but I'm having trouble getting access to the shared drives.

Here's how the school says to do it for Windows (Step 2):
[http://law.wlu.edu/technology/page.asp?pageid=532](http://law.wlu.edu/technology/page.asp?pageid=532)

I tried following this guide to get it to work:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

But it didn't seem to have any effect.  I was a little unclear on what the media name and mount name should be, though, so maybe I did that wrong, and that's why nothing happened.

If possible, I would also like to connect to the network printer -- that would be awesome, that is step three of the first link.

Any help toward keeping my legal education windows-free would be greatly appreciated.

---

### Post by callan79 on 2007-08-21
> **amisus said:**
> I'd really like to use Ubuntu on my notebook for law school, but I'm having trouble getting access to the shared drives.

But it didn't seem to have any effect.  I was a little unclear on what the media name and mount name should be, though, so maybe I did that wrong, and that's why nothing happened.



Hi There,

I wonder if the school is using Novell .... if they are, I'm not sure of the results as I've never used it. But just to make sure you're on the right track, you need to be doing this :

```

cd /media
sudo mkdir schoolnetwork
sudo chown yourusername:yourgroupname schoolnetwork
sudo apt-get install smbfs

```

Doing that will give you a place where you can mount ("map") your network drive, and install the smbfs file system driver. Once that is done, you need to actually attempt to mount it ...

```

sudo mount -t smbfs -o uid=yourusername,gid=yourgroupname,defaults,username=username,password=password,dmask=0777,fmask=0777 \\MFSLAW1\STUHOME\2008L\SmithJ /media/schoolnetwork

```

So, see if that does anything .... if not, paste your errors and either myself or someone wiser can point you in the right direction.

Might also pay to ask the sysadmins what type of sharing is it ... ie is it a Windows Share, aka Samba? Or something else?

Good luck!

Cheers
Callan

---

### Post by amisus on 2007-08-21
Thanks for the suggestions.  I'm afraid I need some clarification, though.

Is the username here my ubuntu username, or is it the username for my school network?  Also, I'm not sure what the groupname would be.  Can you offer any guidance.

Incidentally, I think there is a good chance they use Novell, because I connect to email through Groupwise 7.0

---

### Post by callan79 on 2007-08-22
> **amisus said:**
> Is the username here my ubuntu username, or is it the username for my school network?  Also, I'm not sure what the groupname would be.  Can you offer any guidance.
Incidentally, I think there is a good chance they use Novell, because I connect to email through Groupwise 7.0



G'day,

In my post above, 'yourusername' and 'yourgroupname' refer to the username of YOUR UBUNTU SYSTEM. To find out your group name, just go to terminal and do an  (ls -l)  command, and you'll see all your files listed there, with an owner and group name in there. On my system, it's callan and callan, yours is probably the same in that user + group name are the same.

The 'username=username' and 'password=password' refers to your login details on the school's network.

Good luck :)

CD

---

### Post by amisus on 2007-08-22
I entered:

> sudo mount -t smbfs -o uid=jlamont,gid=jlamont,defaults,username=lamontj,password=********,dmask=0777,fmask=0777 \\MFSLAW1\STUHOME\2010L\lamontj /media/schoolnetwork


and received:

> Usage: mount.smbfs service mountpoint [-n] [-o options,...]
Version 3.0.24

Options:
      username=<arg>                  SMB username
      password=<arg>                  SMB password
      credentials=<filename>          file with username/password
      krb                             use kerberos (active directory)
      netbiosname=<arg>               source NetBIOS name
      uid=<arg>                       mount uid or username
      gid=<arg>                       mount gid or groupname
      port=<arg>                      remote SMB port number
      fmask=<arg>                     file umask
      dmask=<arg>                     directory umask
      debug=<arg>                     debug level
      ip=<arg>                        destination host or IP address
      workgroup=<arg>                 workgroup on destination
      sockopt=<arg>                   TCP socket options
      scope=<arg>                     NetBIOS scope
      iocharset=<arg>                 Linux charset (iso8859-1, utf8)
      codepage=<arg>                  server codepage (cp850)
      unicode                         use unicode when communicating with server
      lfs                             large file system support
      ttl=<arg>                       dircache time to live
      guest                           don't prompt for a password
      ro                              mount read-only
      rw                              mount read-write

This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
  mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test


Which seems a little confusing, since it looks like I entered it according to what it required.  So I tried it twice just to be sure.  What am I doing wrong?

---

### Post by callan79 on 2007-08-22
> **amisus said:**
> Which seems a little confusing, since it looks like I entered it according to what it required.  So I tried it twice just to be sure.  What am I doing wrong?


Bugger, I think I've led you up the garden path. Looking at the mount usage, you need to have the server and local mount point BEFORE the -o options ..... stuff.

Like this :

```

sudo mount -t smbfs //MFSLAW1/STUHOME/2010L/lamontj /media/schoolnetwork -o uid=jlamont,gid=jlamont,defaults,username=lamontj,password=********,dmask=0777,fmask=0777

```


Also two more things :

  -  Looks like you need forward slashes on the server name, not backslashes
  -  Your code that you pasted has a space between , and password - careful, spaces will break it.

Let me know how you go, and sorry for giving you some bad information!

Cheers
Callan

---

### Post by amisus on 2007-08-22
I copied and pasted the input you provided, and put my password in, and this is what I got:

> 6928: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


---

### Post by callan79 on 2007-08-22
> **amisus said:**
> I copied and pasted the input you provided, and put my password in, and this is what I got:

Cool - at least your system is accepting your command, now it's just a password thing, or perhaps the remote server does not actually use smbfs.

Try this - go to Places >> Computer, and in the address bar type :  

   smb://MFSLAW1/STUHOME/2010L/lamontj

And see if your system either bombs out completely, or if it asks you for a username + password. If you get the user+pass prompt, well at least it's trying to connect.

If you don't get the prompt, you might need to ask the sysadmins for some details regarding the network system. Just ask them if it's regular Windows file sharing (Samba/SMB), or if it's something else. Once you find out what it is, you can begin your quest to work out how to make it happen.

Also at terminal :

  man mount

which will have a heap of info regarding which network file sytems are supported.

Cheers
Callan

---

### Post by amisus on 2007-08-22
Sweet!  That worked perfectly!

Though it was a little weird.  It asked for the username and password, and then gave the option of forgetting the password immediately, remembering it until I log out, or remembering it indefinitely.  Or something like that.  The first time I tried forget immediately, and it responded by saying Nautilus could not display the contents, so I tried it again, this time telling it to remember until logout, and it worked without a hitch!  So I bookmarked the location.  Perfect.  Thank you!

Now I if I can just connect to the networked printer I'll be perfect.

---

### Post by callan79 on 2007-08-22
> **amisus said:**
> Though it was a little weird.  It asked for the username and password, and then gave the option of forgetting the password immediately, remembering it until I log out, or remembering it indefinitely.  Or something like that.  The first time I tried forget immediately, and it responded by saying Nautilus could not display the contents, so I tried it again, this time telling it to remember until logout, and it worked without a hitch!  So I bookmarked the location.  Perfect.  Thank you!

Cool, glad it's working for you!

I'd encourage you to mess around with the command line mount, as it seems there's just some glitch with the username and password you're providing on the command line. If you can get that sorted out, then all you have to do is whack it in your fstab with the 'noauto' option, and you can mount it on demand!

Say you set it up in fstab with the mount point as /media/schoolnetwork, and you set noauto. This means it won't auto-mount at boot. To mount it, you just go to terminal and type :  sudy mount ./media/schoolnetwork, and it'll mount the drive for you.

Re your printer, that should not be too hard either. Go to [http://localhost:631](http://localhost:631) which should take you to CUPS admin. Click on ADD PRINTER, and you probably want to add via IPP and then specify the address of the printer, find the driver, and you should be done :)

Let us know if you get stuck with that.

Cheers
Callan

---

### Post by amisus on 2007-08-23
Thanks for the tip.  That seems to have gotten me somewhere.  I can print something, and then up on the task bar I have a printer icon that says lists the job, but in the state it says "job-hold-until-specified"

So it seems like it might be doing something.  In fact, I think it might be related to how the system works.  I was looking out how to connect with a Mac:
[http://law.wlu.edu/technology/page.asp?pageid=544](http://law.wlu.edu/technology/page.asp?pageid=544)

And it says that when you print from a Mac, you have to identify and release the job to a specific printer.  Maybe that's what's going on.

---

### Post by callan79 on 2007-08-24
> **amisus said:**
> Thanks for the tip.  That seems to have gotten me somewhere.  I can print something, and then up on the task bar I have a printer icon that says lists the job, but in the state it says "job-hold-until-specified"

I've seen this before, and it was basically where I had not set up the printer driver properly. I'd suggest you do a couple of things :

1. In your CUPS admin page, see if the printer is listed as online, i.e. does Ubuntu recognise that the printer actually exists?

2. Look at the printer model, and search the forums to see if anyone has had any issues/success with that printer.

3. Look at the log files in  /var/log/cups  (either terminal, or open with gedit), see if there is any info in there that may help you (in terminal, [tail -n 30 -f filename] is pretty cool, as it will echo new lines of the logfile as the file grows. man tail for more details).

4. If all else fails, check out [Turboprint](http://ww.turboprint.info) which is really cool. I purchased this for my sister-in-law who has a Canon IP1300. No success with regular drivers, but Turboprint had it up in 5 minutes. You can use the trial version to see if it works.

Hear from you soon, I guess :)

Callan

---

### Post by maddielu on 2008-03-19
hi,

i'm also trying to map my network drive at school, and i tried all of the suggestions above, but so far i've been unsuccessful. 

the tech department at my school has the following instructions for windows and macs (but of course there's very little documentation on using linux)

[http://helpdesk.princeton.edu/kb/display.plx?id=8474](http://helpdesk.princeton.edu/kb/display.plx?id=8474)

the only thing i've found (but can't understand) is this link:

[http://webscript.princeton.edu/~pug/faqwiki/index.php?title=Using_SAMBA/CIFS_to_access_Windows_Shares](http://webscript.princeton.edu/~pug/faqwiki/index.php?title=Using_SAMBA/CIFS_to_access_Windows_Shares)

i'd really really appreciate the help!:)

---


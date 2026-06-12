---
title: "SAMBA mystery"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by Uta on 2005-06-21
My setup is this: Kubuntu, KDE 3.4.1 running as a stand alone OS on a Dell Laptop C800 and a Mac running 10.3.9 OS. On the Linux side, it can see and share to my Mac but the Mac sees the Linux machine but when I enter my username and password I get the error message that the alias "MYSHARE" could not be opened because the original item cannot be found. How could that be? How do I trouble shoot that? Additionally, SAMBA is not automatically starting when I boot up. I always have to line command, /etc/init.d/samba start
to start samba. Is there some way I can have it automatically start running when I boot? Thanks!

---

### Post by cwaldbieser on 2005-06-21
If I run the following command, I see the following output:

```
$ ls -al /etc/rc3.d | grep samba
lrwxrwxrwx    1 root root   15 Jan 24 22:10 S20samba -> ../init.d/samba
```

That tells me that when Ubuntu boots into runlevel 3, it is going to start up samba.  There are slightly different ways of configuring this on different Linux distros-- I don't recall if there is some utility on Ubuntu you are supposed to use to do it or not.

Anyway, that entry is just a symbolic link to /etc/init.d/samba.  I think you can just add the link on your own and samba should start up when you reboot.

Not sure why you are having problems browsing from your Ubuntu box.  Maybe there is some setting in your /etc/samba/samba.conf file that needs tweaking.  You can install the samba documentation in HTML form from Synaptic.  I think it installs it in /usr/share/doc/samba-doc/htmldocs.  Also, you could try using SWAT to change the settings.

---

### Post by Uta on 2005-06-22
...being new to Linux (Kubuntu) and more Mac OS centric; could you tell me which config file gets the symbolic link? In Mac OS land we have a startup folder, where any app(link) placed in that folder is started on boot. Thanks! 
Additionally where exactly does a shared folder and who has to own the folder in order for Samba to share it on the LAN? I have a 2nd HD I am trying to share on my LAN via SAMBA and I am getting error messages that only folders at root can be shared? Thank you.
OK, I ran the command you suggested and nothing happened other than popping back to the prompt?
Also when I do a right click on a folder to set it up to share I get this message:
An error occurred while trying to share folder '/home/metheuser/myshare'. Make sure that the Perl script 'fileshareset' is set suid root. I'm confused, is that because I am not logged on as root? I thought a user could create a share in the user's home folder? The good news is that I did create a shared folder as root, placing the shared folder in root's home directory and now have samba sharing between my mac and linux laptop (bi-directional, o, joy) but I still don't know if it is possible to share my 2nd HD, is that possible? Thanks to all who can help me unravel this samba share mystery!

---

### Post by cwaldbieser on 2005-06-22
I had that same "Make sure that the Perl script 'fileshareset' is set suid root" error at one point.  According to the package manager, /usr/bin/fileshareset is installed as part of the kdelibs-bin package.  For whatever reason, when the file was installed, the proper permission (the SUID bit) was not set.

The SUID bit allows you to run a program in the security context of the owner of the file.  So for example, since root owns that file, a normal user can run the program and it can do things that normally only root could do.

To set the SUID bit:

```
$ sudo chmod u+s /usr/bin/fileshareset
```

That should get your right click file sharing in working order.  Once that is working, file sharing should be pretty easy.

As for the starting samba on boot-up:
This command:
```
$ ls -al /etc/rc3.d | grep samba
```
basically says give me a list of all the files in the folder /etc/rc3.d, and then filter out and show me only the files with the text "samba" in them somewhere.  Since you just got the command prompt back, that means you don't have the symbolic link there.

When samba is installed, it is supposed to put a symbolic link to it's startup script in there for you.  If you just do a:
```

$ ls -al /etc/rc3.d
```
you should see a bunch of links.  Here are mine, for example:
```

total 12
drwxr-xr-x    2 root root 4096 Jun  8 02:13 .
drwxr-xr-x  122 root root 8192 Jun 22 17:31 ..
lrwxrwxrwx    1 root root   17 Mar 25 23:01 K11anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   17 Mar 25 22:59 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx    1 root root   18 Oct 15  2004 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   15 Oct 15  2004 S11klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   13 Mar 25 23:04 S13gdm -> ../init.d/gdm
lrwxrwxrwx    1 root root   13 Mar 26 02:22 S13kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   13 Oct 15  2004 S14ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   17 Oct 15  2004 S18portmap -> ../init.d/portmap
lrwxrwxrwx    1 root root   16 Mar 25 23:03 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   22 Mar 29 19:03 S19spamassassin -> ../init.d/spamassassin
lrwxrwxrwx    1 root root   15 Oct 15  2004 S20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   14 Oct 15  2004 S20alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   14 Oct 15  2004 S20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 Oct 15  2004 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   24 Mar 27 13:30 S20emifreq-applet -> ../init.d/emifreq-applet
lrwxrwxrwx    1 root root   13 Oct 15  2004 S20fam -> ../init.d/fam
lrwxrwxrwx    1 root root   21 Jun  8 02:13 S20firestarter -> ../init.d/firestarter
lrwxrwxrwx    1 root root   15 Oct 15  2004 S20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   15 Feb 20 00:27 S20l2tpd -> ../init.d/l2tpd
lrwxrwxrwx    1 root root   14 Jan 24 22:07 S20lisa -> ../init.d/lisa
lrwxrwxrwx    1 root root   17 Oct 15  2004 S20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   27 Jan 25 01:26 S20nfs-kernel-server -> ../init.d/nfs-kernel-server
lrwxrwxrwx    1 root root   16 Oct 15  2004 S20pcmcia -> ../init.d/pcmcia
lrwxrwxrwx    1 root root   17 Oct 15  2004 S20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 Oct 15  2004 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 Oct 15  2004 S20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   15 Jan 24 22:10 S20samba -> ../init.d/samba
lrwxrwxrwx    1 root root   13 Oct 27  2004 S20ssh -> ../init.d/ssh
lrwxrwxrwx    1 root root   16 Feb 22 18:33 S20webmin -> ../init.d/webmin
lrwxrwxrwx    1 root root   20 Jan 25 01:26 S21nfs-common -> ../init.d/nfs-common
lrwxrwxrwx    1 root root   15 Oct 15  2004 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   17 Mar 25 23:01 S89anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   13 Oct 15  2004 S89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   14 Oct 15  2004 S89cron -> ../init.d/cron
lrwxrwxrwx    1 root root   22 Oct 15  2004 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   19 Oct 15  2004 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   19 Oct 15  2004 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx    1 root root   23 Oct 15  2004 S99stop-bootlogd -> ../init.d/stop-bootlogd
lrwxrwxrwx    1 root root   18 Mar 31 21:19 S99timidity -> ../init.d/timidity
```

Now if you look closely at the file names, they look like S##name -> ../init.d/name.  The two digits after the S tell what order the services get started at boot time.  So in my example, CUPS (S19) starts before cron (S89).  Samba starts after CUPS (S20).  The "->" points to the real file that the link is linked to.  In this case, all the real start-up scripts are in the /etc/init.d folder.

If you do:
```

$ ls -al /etc/init.d | grep samba
```
you should see the samba program listed there as output.  To create the symbolic link you need for it to start samba at boot time:

```
$ cd /etc/rc3.d
$ sudo ln -s /etc/init.d/samba S20samba
```

That should do the trick.

That kind of boot up config is often called "SysV" in the literature.  Ubuntu actually has some other place for you to put in your own custom start up scripts, but I forget where that is-- it might be listed in the Ubuntu Guide.

---

### Post by Uta on 2005-06-22
Thank you, you are a wealth of information, I very much appreciate your instructions...but my right click is still giving me that darn error message.
I "$ sudo chmod u+s /usr/bin/fileshareset" as you suggested and the permissions list as follows.
-rwsr-xr-x  ? Is that right? If not and I suspect not, what's wrong? Also I did create a link, I see it listed but SAMBA doesn't really start (meaning it never shows up in my Mac's network browser) until I line command it to start on the linux side, STRANGE! But stranger still once it starts, the folders of my linux shares refuse to be written to, giving me an error message, "You cannot copy some of these items to the destination because their names are too long or contain invalid charcters for the destination." I am only trying to copy one file and it's name is RU.rtf Something is wacky somewhere? Also any ideas about sharing a second HS on the Linux side, is it possible? Thank you--

---

### Post by cwaldbieser on 2005-06-23
Hmm,

Hmm, maybe samba *is* starting up-- it is just not letting itself be browsable.  Try  to get a process status of samba after you boot up:
```
$ ps -Al | grep smbd
```
That means, give me the process status of ALL processes on the system in long format, but only show me the lines that have "smbd" (the samba daemon) in them.  If this doesn't come back blank, then samba is actually running.

Concerning the right click-- can you print the entire output of:
```
$ ls -l /usr/bin/fileshareset
```
Maybe the owner is not root?

Concerning the "names are too long" error message-- Maybe it is complaining about the full path of the share?  Do the folders have long names or spaces in them?

Concerning sharing the second HD.
I think normally, a user is only allowed to share their home directory, but you can configure it through the right click once you get it working.  There will be a button that says something like "Configure File Sharing".  It will take you to a dialog that lets you select different types of file sharing options for users (the simplest being that they can share from their home directories).

You can also configure this using tools like SWAT or directly editing the the /etc/smb.conf file.  

```
$ man smb.conf
```
will give you a lot of information on this, and I think you can also get the samba-doc package which includes HTML manuals for how to configure samba.  I have only ever actually tried doing the simple sharing, but in theory, it shouldn't be too different.

---

### Post by Uta on 2005-06-23
"$ ps -Al | grep smbd"

Came back blank-- But when I started samba via the command line, I got this:

5 S     0  7709     1  0  78   0 -  2161 -      ?        00:00:00 smbd
1 S     0  7718  7709  0  78   0 -  2161 pause  ?        00:00:00 smbd


Concerning the right click-- can you print the entire output of:
```
$ ls -l /usr/bin/fileshareset
```
Maybe the owner is not root?

It is root, -rwsr-xr-x 1 root root 10997 2005-05-23 07:15 /usr/bin/fileshareset

  "Do the folders have long names or spaces in them?"

No, one is named "DROPBOX" the other is "MYSHARE"

Strange? Ok what else could be the reason why SAMBA isn't starting? I have a symbolic link...SAMBA only seems to start if I type /etc/init.d/samba start

Thanks for helping me trouble shoot this...

---

### Post by cwaldbieser on 2005-06-23
Hmm.  Maybe you are booting into a different runlevel?  In Ubuntu, runlevels 2-5 are the same, from what I understand.  Try:
```
$ runlevel
```
This will come back with something like "N 2" where the number after the N is the runlevel.  If you were in runlevel 3, then the /etc/rc3.d/ symbolic link should have worked.  If you are booting into runlevel 2, then you need a link in /etc/rc2.d/.  Generally, for runlevel N, you need a link in /etc/rcN.d/.

The BUM (Boot Up Manager) sub forum might have some helpful links:
[http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75)
Here is a link from that forum that explains how boot up scripts work in Debian and Ubuntu:
[http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75)

The SUID problem has me stumped for now.  I will have to give it some more thought.

As for the folders with spaces, what about the full paths to DROPBOX and MYSHARE?  Are they something like:

```
/home/user name with spaces/MYSHARE
```
Just a wild guess, there.  The error seems more like it is means the file you are trying to copy from your Mac, but the file name looks normal to me.

Try posting your /etc/samba/smb.conf as an attachment, and I will look it over and see if I notice anything odd.

---

### Post by Uta on 2005-06-23
[QUOTE=cwaldbieser]Hmm.  Maybe you are booting into a different runlevel?  In Ubuntu, runlevels 2-5 are the same, from what I understand.  Try:
```
$ runlevel
```
This will come back with something like "N 2" where the number after the N is the runlevel.  If you were in runlevel 3, then the /etc/rc3.d/ symbolic link should have worked.  If you are booting into runlevel 2, then you need a link in /etc/rc2.d/.  Generally, for runlevel N, you need a link in /etc/rcN.d/.

Yes that was the problem samba now boots with the system startup--thanks!
I'll post more info tomorrow, thanks--

[Tomorrow is today]

Again thanks for your trouble shooting my samba issues; I have learned a lot about samba and linux line commands! Strange but true I now have bi-directional sharing via samba, Linux laptop and the other 3 Macs are all on speaking terms. The only thing I added in my smb.conf file was this line, available = yes.
I'm sure over the past few days, changing and changing the permissions I have probably hit the right combo to make my Mac and Linux understand one another, not very exact on my part but it works and that is what counts at this point! Thank You!

---

### Post by Cirrocco on 2006-04-05
here's how to access the share once samba is running:

on the linux machine:
```
sudo smbpasswd -a username
```
where username is your username.

---


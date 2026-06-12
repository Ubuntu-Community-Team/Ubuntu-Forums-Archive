---
title: "Problem with samba/CIFS"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by dyefade on 2008-05-01
Hi all,

I upgraded to Hardy yesterday (after only a little fighting with it).

I'm really impressed with the VGFS system, letting you access shares through smb://share/folder is really handy - but so few apps let you do it! Specifically, Banshee does not feature support for this.

So, the problem is I can't mount samba shares any longer. The error I'm getting when I run
```
sudo mount -a
```
is
```
mount error 13 = Permission denied
```
but I know the credentials are correct because fstab hasn't been changed since the upgrade. Also, if it needs these credentials, how is nautilus able to just go right ahead and mount it?
[http://ubuntuforums.org/showthread.php?p=4852738](http://ubuntuforums.org/showthread.php?p=4852738) seems to be a similiar problem, but with different errors.

My only thought is: does is matter that the password is blank (don't stone me)? Could that be confusing CIFS?

If anyone can offer help here I'd be happy. The ideal solution would be for Gnome apps to just support the new protocols, but no doubt the answer there will be "wait for the upstream updates". And it doesn't help with things like Eclipse.

Thanks all,
B.

---

### Post by dyefade on 2008-05-13
Bump.

This hasn't been a big deal, but is now getting to be a real problem. There are lots of people having similar problems, but very few answers out there.

SOMEONE must know what changed between Gutsy and Hardy to cause these problems - anyone able to shed any light?

Another question I have is: why do some gnome apps give access to Samba shares while others don't?

Finally: would it be easier to just change the shares on my server to use NFS? Maybe I should have been doing this all along?

Thanks for any replies.

---

### Post by napzilla on 2008-05-19
I am having the same exact problem here. I changed smbfs to cifs in /etc/fstabs, but I'm still getting "mount error 13". I haven't found anything helpful in the manpages yet, and looking for help online has thus far only brought me here. I even tried a fresh install of Hardy, but still without luck. As access to the Windows shares is fairly critical to my research, I'm fairly desperate to find a solution. I'll post again if I find anything that helps.

---

### Post by Iowan on 2008-05-19
I found [this]("http://ubuntuforums.org/showthread.php?t=800313&highlight=cifs") today - see if it helps.

---

### Post by dmizer on 2008-05-19
> **napzilla said:**
> I am having the same exact problem here. I changed smbfs to cifs in /etc/fstabs, but I'm still getting "mount error 13". 

you'll need to do more than just change smbfs to cifs.  these are different protocols, the options are different, and the credentials file format is different.  please see the mounting samba shares link in my sig, which also includes the fix that Iowan linked to.

---

### Post by napzilla on 2008-05-20
Thanks for pointing me to your excellent post, dmizer. After reviewing your instructions and some of the responses, I finally got the mount to work. Fortunately, all my colleagues have gone home, so no one was here to witness my shout for joy and my happy dance. In case anyone else is having trouble, I will include a censored version of my personal log on this issue:

> 
After upgrading from Gutsy to Hardy, I was no longer able to mount Windows shares via Samba. Some sniffing around indicated that this was due to a change from [FONT="Fixedsys"]smbfs[/FONT] to [FONT="Fixedsys"]cifs[/FONT] as the standard network filesystem for mounting.

I changed '[FONT="Fixedsys"]smbfs[/FONT]' to '[FONT="Fixedsys"]cifs[/FONT]' in [FONT="Fixedsys"]/etc/fstab[/FONT]

[FONT="Fixedsys"]syslog[/FONT] and [FONT="Fixedsys"]messages[/FONT] reported '[FONT="Fixedsys"]NT_STATUS_LOGON_FAILURE[/FONT]'

[FONT="Fixedsys"]auth.log[/FONT] reported that [FONT="Fixedsys"]/lib/security/pam_smbpass.so[/FONT] could not be found

[FONT="Lucida Console"]*Bug Report # 216990 in pam*[/FONT] on *Launchpad* ([http://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990](http://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990)) reported that the error was due to a missing package named '[FONT="Fixedsys"]libpam-smbpass[/FONT]'

A check confirmed that installing [FONT="Fixedsys"]libpam-smbpass[/FONT] caused [FONT="Fixedsys"]pam_smbpass.so[/FONT] to appear in [FONT="Fixedsys"]/lib/security[/FONT]. Unfortunately, [FONT="Fixedsys"]mount -a[/FONT] still returns a 'mount error 13 = Permission denied'. I'm going to shoot something.

I found that I could access gak [The Windows share] through nautilus using [FONT="Fixedsys"]Places->Connect to server...[/FONT]

I then discovered that I still needed to install [FONT="Fixedsys"]winbind[/FONT]. I installed [FONT="Fixedsys"]winbind[/FONT] and rebooted the system.

I still received mount error 13. In frustration, I repeatedly issued the command. Eventually, the message changed from '[FONT="Fixedsys"]NT_STATUS_LOGON_FAILURE[/FONT]' to something like '[FONT="Fixedsys"]NT_SERVER_LOCKOUT[/FONT]', indicating that it is contacting a server at least.

After reading another post on samba and cifs ([http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)), I added '[FONT="Fixedsys"]wins[/FONT]' to [FONT="Fixedsys"]/etc/nsswitch.conf[/FONT] after '[FONT="Fixedsys"]files[/FONT]'. I then rebooted.

Still no [censored] success. I'm almost ready to throw this [censored] [censored] [censored] out the window. What the hell does 'mount error [censored] 13' even mean, anyway?!!

Adding '[FONT="Fixedsys"],domain=onepurdue,nounix,iocharset=utf8[/FONT]' to the line in [FONT="Fixedsys"]/etc/fstab[/FONT] upgraded me from error 13 to '[FONT="Fixedsys"]mount error 5 = input/output error[/FONT]'. I don't know what this means either, but at least it's a different freaking error.

Somebody mentioned that they needed to use the IP address instead of the DNS in [FONT="Fixedsys"]/etc/fstab[/FONT]. I was using the '[FONT="Fixedsys"]honeylocust[/FONT]' shortcut from [FONT="Fixedsys"]/etc/hosts[/FONT], but for the heck of it, I changed it to the IP address. Here's the final version of the line in [FONT="Fixedsys"]/etc/fstab[/FONT]:

```
 //128.210.108.174/gak /mnt/gak cifs credentials=/root/.smbcredentials,domain=onepurdue,nounix,iocharset=utf8 0 0 
```

My word, it actually worked!!!!!! YES!!!! YES! YES! YES!


---

### Post by dmizer on 2008-05-20
fantastic, glad you got it going!

just a bit more information about your error 5.  you need a wins server in order to resolve host names over samba.  configuring /etc/hosts is not sufficient.

so, unless you have:
[LIST]
[*]a properly configured linux samba server <or>
[*]a windows pc on your network <and>
[*]all computers in your network are on the same domain
[/LIST]

you will have to connect by ip.  in many cases, this is also true for windows clients.  so, if you had to use the "domain=" option, that's probably one reason why you cannot connect unless you explicitly denote the ip of the server in your mount command.

---

### Post by snoopy66 on 2008-06-10
I too have been looking for a solution for this problem for days.  I read MANY posts, and I found that the following things worked for me.

1) Make sure the following package are installed:

- samba
- smbfs
- winbind

2) Edit the file /etc/nsswitch.conf, changing the line that reads

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

to

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4

Between installing winbind and putting this line in the nsswitch.conf file, Samba on Kubuntu is able to find the Windows share.

3) Restart samba with the following command:

$ sudo /etc/init.d/samba restart

Note that my goal was to to mount a share using "smbmount", so I continued as follows:

4) Create a credentials file with your user name and password:

$ echo "username=myid
password=mypassword" > $HOME/.smbmount

** BE SURE NOT TO PUT SPACES BEFORE/AFTER THE EQUALS SIGN.  That's what kept causing my error 13 - permission denied.

5) Don't forget to change the security of the credentials file so only you can see it.

$ chmod 600 $HOME/.smbmount

6) Finally, mount the Samba share.

$ sudo smbmount //windowsservername/windowsharename $HOME/mymountpoint -o credentials=$HOME/.smbmount

Note that I am running Kubuntu 8.04, and I am using the default /etc/smb.conf file that came with the install.  You may need to change the workgroup or other settings in this file so it matches your Windows settings.  You may also want to add some other options to the smbmount command such as uid= or gid=.

---


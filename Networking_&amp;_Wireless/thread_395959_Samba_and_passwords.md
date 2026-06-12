---
title: "Samba and passwords"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by MJWhiteDerm on 2007-03-28
I have a LAN, with a Windows network shared by the linux boxes.  My wife and stepson are not yet ready to jump to linux, so I am trying to run a linux file server for us.  I had it working when the linux boxes were all Suse Linux 10.1, but the ubuntu box wants me to log in when I connect remotely from the Windows box, then doesn't accept any of the userid and password combinations.

Any clue what i might be doing wrong?

Michael

---

### Post by dmizer on 2007-03-28
edit /etc/samba/smb.conf
```
gksudo gedit /etc/samba/smb.conf
```

look for "security = user" and change it to "security = share"

also ... under your share configuration look for "guest ok = no" and change it to "guest ok = yes"
if "guest ok" does not show, create it.

make sure your ubuntu login is added to the samba group:
```
sudo smbpasswd -L -a your_ubuntu_username
sudo smbpasswd -L -e your_ubuntu_username
```
when it askes you for your password, make SURE you use the same password as your ubuntu signin password.

restart samba:
```
sudo /etc/init.d/samba restart
```

see if it works now.

if it doesn't work after this edit, or you don't fully understand my directions, please post the contents of your /etc/samba/smb.conf file

---

### Post by ResumeMan on 2007-12-06
I tried making the changes in this thread, but still ended up with problems.

Background:

I'm in the process of setting  up an Ubuntu-based file server running Samba. I'm trying to get the "main" PC running Win XP Media Ctr Edition to consistently and transparently recognize the samba shares.

Both my wife and I have accounts on the XP computer, and have fast switching enabled and no passwords set on the accounts (we're behind a firewall and there's nobody else w/access to the computer).

I setup user accounts on the server for the usernames that exist on the XP machine for both of us.  So if I map a shared drive, and enter the appropriate username with the password I set up on the server, it maps no problem. But any time we log out and back in again it demands a password.

I looked into saving passwords on the Windows side, but no luck -- XP MCE seems to have that disabled :mad: If I establish password protection on the Win side (using the same pword as on the server side) it retains the share, but I don't *want* (or more accurately my wife doesn't want) to have to type the password every time we switch between profiles.

So I made dmizer's changes -- changed security to "share" and added "guest ok = yes." But now when I try to map a share using the non-password-protected profile, it asks for a password for "Guest." And none of the passwords I've used work...

any ideas???

Thanks!!!

---

### Post by infinitezero on 2007-12-07
Following this link and download the Samba Install on Kubuntu 7.04 - rev1.3.pdf.tar.gz .




[http://ubuntuforums.org/showthread.php?t=575214](http://ubuntuforums.org/showthread.php?t=575214)


Hope it helps,
iz

---

### Post by jonandrews on 2007-12-07
I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Let me know if it works for you..

---

### Post by ResumeMan on 2007-12-07
Just a quick follow up that using the smb.conf syntax in [this thread]("http://ubuntuforums.org/showthread.php?t=628733") solved my problem. It's important that guest is a user on the computer and a samba user, and that guest has permission to read and write the shared files. Other than that, worked like a charm.

---


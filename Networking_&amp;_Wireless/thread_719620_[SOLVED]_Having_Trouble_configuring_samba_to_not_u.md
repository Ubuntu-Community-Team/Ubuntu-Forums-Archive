---
title: "[SOLVED] Having Trouble configuring samba to not use accounts to login"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2008-03-09
I have samba set up and one share set up. I want to be able to access my linux server and its shares without the need to use a username and password.

Here's the single share config:

[http_folder]
comment = Web Folder
writable = yes
locking = no
path = /var/www
public = yes
valid users = jordanwb
create mask = 0775

When I click on the SERVER icon in the Network folder in Vista I'm prompted for a username and password. I want to be able to map a network drive in Vista to the share shown above.

---

### Post by Eiríkr on 2008-03-09
A couple thoughts:
[list][*]Is there any particular reason you want to avoid any authentication?  Even *with* authentication, on my setup, I only ever had to enter my Samba username and password once when initially mapping a drive in XP to a share on Ubuntu, and after that, XP just mounts the drive (share) automagically every time I log in.  
[*]Your share setup is self-contradictory -- you state [font=courier]public = yes[/font] (a synonym for [font=courier]guest ok = yes[/font]), which can be used to allow anyone at all to login, but then at the same time you restrict access with [font=courier]valid users = jordanwb[/font].  (And is there any compelling reason to set [font=courier]locking = no[/font]?  This refers to how files are locked when accessed by an appliction, and setting this to "no" can actually be dangerous in some circumstances and lead to corrupted files.  See [here]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING") for details.)  Anyway, I would *highly* recommend that you read over the relevant portions of the smb.conf man page, particularly the bits about [security]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY"), [mapping to the "guest" user]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPTOGUEST"), and about [mapping usernames]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP").  [/list]

Note that once you've mapped a drive and marked that you want the connection to be restored on next boot, Windows should record your authentication information for that share and use it automatically next time around.  You're only being prompted now because you haven't mapped a drive yet.  (Of course, it's entirely possible that Vista has borked this up; I can only speak for XP myself.)

HTH,

Eiríkr

---

### Post by Jordanwb on 2008-03-09
I took out the "users = jordanwb" bit when I found out I couldn't access the share on my ubuntu laptop. When it said "locking = no" I thought it went that if it was set to yes it would be locked. When I was prompted for a username I typed in the following:

jordanwb@192.168.1.2
jordanwb@SERVER
SERVER\jordanwb

I also put in the correct password but I couldn't login so...

---

### Post by Eiríkr on 2008-03-09
One other wrinkle for Samba access -- there is a separate Samba password list.  This is an added security measure, as it means that even if your Samba password is stolen, your Ubuntu login is still safe (so long as the two are different, of course ;)).  As such, though, you also need to make sure you've added your Samba username to the Samba password list, like so:
```
sudo smbpasswd -a USERNAME
```
... then type in your desired Samba password at the prompt.  Without this, you *cannot* access your share.  But once you've done it, you should be good to go.  :)

HTH,

Eiríkr

---

### Post by Jordanwb on 2008-04-04
I was never emailed about this message so that's why I'm so late replying. Anyways thanks I'll try that. The tutorial didn't mention that.

[Edit]Sweet thanks.

---

### Post by Eiríkr on 2008-04-04
> Sweet thanks.

I take it that means things are working?  Great!  :D  If that does it for you for this thread then, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

### Post by Jordanwb on 2008-04-04
Yep it works just fine. I plan to install Samba onto my laptop to access it from my Windows PC.

---

### Post by Eiríkr on 2008-04-04
Great!  Hope it works out.  :)  Post back if you run into any problems.

Cheers,

Eiríkr

---


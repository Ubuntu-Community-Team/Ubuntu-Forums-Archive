---
title: "Backing up server settings"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by NeonSamurai on 2010-10-09
The time has finally come to upgrade my Xubuntu server with new (and hopefully quieter) components. I also think it's time to rebuild the Xubuntu install.

My machine currently runs the following for me:

[COLOR="DarkRed"]Samba shared folder
Cups
Deluge Torrent
FTP
And I have also mounted another HDD on it.[/COLOR]

What I'd like to do is backup these settings so that after the reinstallation I can replace the files and have most of the configuration work completed.

I just need to know which files would be the ones that I'll need to copy.

Can anyone help me out with that?

Thanks


Neon

---

### Post by mvklingeren on 2010-10-09
The config files for your applications on Ubuntu

Samba -> /etc/samba/smb.conf

Cups  -> /etc/cups/cupsd.conf
      -> /etc/cups/printers.conf

Deluge config is in a home directory: ~/.config/deluge/

FTP? > depends on which FTP server, /etc/ftpd?

'And i also have mounted another HD to it'

That's in /etc/fstab

>

Best thing you can do is, make a copy of your complete etc directory
/etc 

and your ~/  home directory

So you certainly wont loose anything

---


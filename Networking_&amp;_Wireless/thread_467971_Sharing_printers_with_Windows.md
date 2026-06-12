---
title: "Sharing printers with Windows"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by inselaffe on 2007-06-08
I've installed Ubuntu server 704, and managed to share a printer (a Samsung ML 2010) with Windows XP desktops. I followed this setup (albeit for 6.10) [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

Whilst it works, I need to refine/fix a couple of points:
* Can the server provide the Windows driver to the Windows clients (as would a Windows server), to save having to browse for the Windows driver on each machine?
* In the Windows driver, a list of 6 paper sizes are shown as available, whereas in reality there is only A4. This seems to break the automatic letter/A4 resizing Word does. Can this be configured server side? In CUPS admin the paper size is set as A4.
* I have set up a new samba user, specifying a blank password as they have no password on the Windows machine, (and aren't going to start using a password now just because I want to use an Ubuntu rather than Windows box to share the printer). This user is refused permission to access the printer, whereas another user with a password may access it.

---

### Post by dannyboy79 on 2007-06-08
for the first question, I beleive you need to set that within your smb.conf possibly, because that's what is sharing it out? I don't use the cups web interface, I use Ubuntu's Printer Dialog Box but I am pretty sure that there's an smb.conf option which can be set to let network users know where the printer's drivers are.

number 2: if you're saying that you already set the default paper size within cups to A4, than you've already done it "server side". Sounds like a word preference?

number 3: you need to put guest ok = yes for the printer service that you are sharing, then and only then will users without passwords be able to connect. What security option are you using in your smb.conf. The defualt is "user" if you didn't change it, which means only users who are users within the smbpasswd file can be authenticated and use the services of your samba server.

Here is an older guide but it should be pretty applicabled: [http://forums.gentoo.org/viewtopic.php?t=110931](http://forums.gentoo.org/viewtopic.php?t=110931)

---


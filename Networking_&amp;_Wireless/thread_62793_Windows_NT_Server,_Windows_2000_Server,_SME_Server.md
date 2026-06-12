---
title: "Windows NT Server, Windows 2000 Server, SME Server (AKA e-smith) domain login"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by Marc Higgins on 2005-09-05
We've been trying to authenticate to a SME box is 6.0.1 with the (esmith unofficial update script applied that just make esmith so very much better), we have also been testing with a NT4 server & a Windows 2000 server

We know it can be done because mandrake seems to do a domain login with SME or W2K Server or NT4 Server out of the box as long as you join the domain during the initial build, but well it's just not our desktop of choice we love Ubuntu - we are Hoary Hedgehogs... well at least until October, then we will be Breezy boys.

We have been following & playing with this;
[http://ubuntuforums.org/archive/index.php/t-5409.html](http://ubuntuforums.org/archive/index.php/t-5409.html)

but unfortunately haven't got it working yet. It seems to join the domain & everything tests OK, but when we reboot, we can't log in as any user, as in we're locked out.

If you do intend to play with this, BACK UP YOUR FILES FIRST.

This is a simple script to do just exactly that; copy & paste this with your favorite text editor & save it as winbindbak.sh

#winbind_back_up script
cp -v /etc/login.defs /etc/login.defs.bak
cp -v /etc/nsswitch.conf /etc/nsswitch.conf.bak
cp -v /etc/samba/smb.conf /etc/samba/smb.conf.bak
cp -v /etc/pam.d/common-account /etc/pam.d/common-account.bak
cp -v /etc/pam.d/common-auth /etc/pam.d/common-auth.bak
cp -v /etc/pam.d/common-password /etc/pam.d/common-password.bak
cp -v /etc/pam.d/common-session /etc/pam.d/common-session.bak
cp -v /etc/pam.d/sudo /etc/pam.d/sudo.bak

then at a comand prompt run;
sudo sh /path_to_where_you_saved_it/winbindbak.sh

That way if you end up locked out like i did, you can come back up in rescue mode & put them all back;

& heres a script to do just that again copy & paste this to your favorite text editor & save as winbindrest.sh

#winbind_restore_backed_up_files & save the broken ones for investigation script
cp -v /etc/login.defs /etc/login.defs.bak2
cp -v /etc/nsswitch.conf /etc/nsswitch.conf.bak2
cp -v /etc/samba/smb.conf /etc/samba/smb.conf.bak2
cp -v /etc/pam.d/common-account /etc/pam.d/common-account.bak2
cp -v /etc/pam.d/common-auth /etc/pam.d/common-auth.bak2
cp -v /etc/pam.d/common-password /etc/pam.d/common-password.bak2
cp -v /etc/pam.d/common-session /etc/pam.d/common-session.bak2
cp -v /etc/pam.d/sudo /etc/pam.d/sudo.bak2
cp -v /etc/login.defs.bak /etc/login.defs
cp -v /etc/nsswitch.conf.bak /etc/nsswitch.conf
cp -v /etc/samba/smb.conf.bak /etc/samba/smb.conf
cp -v /etc/pam.d/common-account.bak /etc/pam.d/common-account
cp -v /etc/pam.d/common-auth.bak /etc/pam.d/common-auth
cp -v /etc/pam.d/common-password.bak /etc/pam.d/common-password
cp -v /etc/pam.d/common-session.bak /etc/pam.d/common-session
cp -v /etc/pam.d/sudo.bak /etc/pam.d/sudo

then at a command prompt run;

sudo sh /path_to_where_you_saved_it/winbindrest.sh

& you should be back up & running in seconds

What is it we are trying to do;


1) SME Server / NT4 Server / or 2000 Server domain, authentication login control that flows to local hoary clients

Winbind looks like the right tool to do this

2) get hoary accepting form SME Server / NT4 Server / or 2000 Server the equivalent of "roaming profiles", ...

login here, here's your profile stuff & your mounts,
move to a new machine, there it is again,
pick your notebook up & leave the office, you still have your stuff held locally in your local profile, but your mounts to the server are broken,
change something while your away, log back into the domain, thankyou we have your changes.

In short, the same functionality that windows NT/W2K/XPpro clients have.

The most frustrating thing is knowing it can be don't but not having the skills to do it, would appreciate any advice on how this can be achived, in a secure way.

---

### Post by jworr on 2005-09-19
think thread might help you a little:

[http://www.ubuntuforums.org/showthread.php?t=5409&highlight=login+windows+server](http://www.ubuntuforums.org/showthread.php?t=5409&highlight=login+windows+server)

---

### Post by Marc Higgins on 2006-10-08
These guys at Canterbury School Tech rock ... cool school!

[http://tech.canterburyschool.org/tec...tuWorkstations](http://tech.canterburyschool.org/tec...tuWorkstations)

tested this & it looks like it also works for Dapper!

Only issues I had was with the e-smith box (SME7) need to issued "smbpasswd -a -m LOCAL MACHINE NAME" to authenticate for each machine to join the domain.

Also would be worth while noting that when you edit /etc/gdm/Xsession & add these lines:

ICEAUTHORITY="/tmp/ICEauthority-${USER}"
export ICEAUTHORITY

It needs to be placed early in the file. If you just tag it on the end of the file you will end up with .ICEauthority-c issues

We should have a look at trying to get this into a simple script.

For some people all the editing would be intimidating & probably too much trouble for some many & to do a lot of machines this way would be a huge PITA
Edit/Delete Message

---


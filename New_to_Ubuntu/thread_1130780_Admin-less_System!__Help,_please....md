---
title: "Admin-less System!  Help, please..."
date: 2009-04-20
forum: New to Ubuntu
---

### Post by mark111 on 2009-04-20
Greetings.

I have been on Ubuntu for a couple of weeks and am now a convert.  I have, however, been reading the forums too literally and am now in trouble.  I have a PC install of Ubuntu 8.10 with one user.  In one forum while adjusting my settings, someone advised that it is advisable for users not to have admin privileges (in System/Administration/Users and Groups).  The advice was good, but now I am really stuck because that abvice was not intended for the ONLY user.  Doh!

I have tried the following:

- set up a new user (not permitted as I don't have admin privileges, and does not work if I use a boot disk)
- edited the file etc/group to add my username under the admin line (as I do not have edit rights, I can read but not write)
- no sudo command works (including sudo -) as I am not in the sudoers file.

OK, now what?  I have been advised to avoid setting up a root password as it may have other characteristics (expiry for example) that are undesirable. 

HELP!  I can't possibly have to reinstall...

---

### Post by jayjay960 on 2009-04-20
There should be a root user at least. Try typing "su" into a terminal and see what comes up.

---

### Post by CatKiller on 2009-04-20
If you reboot, you should find that you have a single-user "Recovery" mode. This will automatically log you in as root and take you to a console. You should be able to add your user to the admin group there.

More information [here]("http://www.psychocats.net/ubuntu/fixsudo").

---

### Post by hesjnet on 2009-04-20
> **CatKiller said:**
> If you reboot, you should find that you have a single-user "Recovery" mode. This will automatically log you in as root and take you to a console. You should be able to add your user to the admin group there.

It is actually quite scary how easy it is to own a ubuntu-box. With windows you at least have to insert a live-cd...

---

### Post by kpatz on 2009-04-20
> **CatKiller said:**
> If you reboot, you should find that you have a single-user "Recovery" mode. This will automatically log you in as root and take you to a console. You should be able to add your user to the admin group there.You may need to hit Esc just before Ubuntu starts to boot to bring up the grub menu, which will have a recovery mode option.

---

### Post by aeiah on 2009-04-20
if you cant use su (which is probably true since im guessing your user is no longer in the sudoers list) then you're best booting into recovery mode. this drops you to the CLI shell as root. you can then issue commands to restore your username, add a new user etc. you'll probably find it easier to boot into the GUI though as root and do the work necessary from there. i cant remember how ubuntu sets it up but either ```
startx
``` or ```
/etc/init.d/gdm start
``` should do the trick. remember not to be lazy though and just use root as your regular login. if you cant fix your normal user then its best to create a new one and then hope over all your home files and folders etc (remember to change permissions if you do this though else the files will be owned by your old username).

---

### Post by aeiah on 2009-04-20
> **hesjnet said:**
> It is actually quite scary how easy it is to own a ubuntu-box. With windows you at least have to insert a live-cd...

you can own just about any operating system if you have physical access to it.. if your pc is mobile or in a public area you should have at least a BIOS password, if not some form of harddrive encryption

---

### Post by mikewhatever on 2009-04-20
According to <man adduser>, you can add yourself back to the admin group with the following command:
**adduser --group your-user-name admin**
You have to do it from the recovery mode.

> **hesjnet said:**
> It is actually quite scary how easy it is to own a ubuntu-box. With windows you at least have to insert a live-cd...

I consider this to be pure FUD.[-X

---

### Post by CatKiller on 2009-04-20
> **hesjnet said:**
> It is actually quite scary how easy it is to own a ubuntu-box. With windows you at least have to insert a live-cd...

Not really. Physical access means that the box is owned anyway. As you say, a live cd makes whatever you used for security at this point effectively non-existent. Removing single-user mode just makes it more inconvenient to fix your box when, for example, you've removed all the users from the admin group....

---

### Post by hesjnet on 2009-04-20
> **CatKiller said:**
> Not really. Physical access means that the box is owned anyway. As you say, a live cd makes whatever you used for security at this point effectively non-existent. Removing single-user mode just makes it more inconvenient to fix your box when, for example, you've removed all the users from the admin group....

I know, but tell this to my friend who got all his private pictures stolen at a party. It is easyer for a "noob" to hit "Esc" and type "startx", than it is to download and burn an iso-file with whatever live-disc and boot this to crack/delete/bypass the password.

A BIOS password though. That is a good suggestion.

---

### Post by aeiah on 2009-04-20
bios password just means someone's gotta physically remove your hard drive or set jumpers / remove the cmos battery / whatever it takes to hard reset the bios. most bios can be hard reset if you forget the password.

if you have your pc around untrusted people you're best encrypting your harddrive. you can encrypt everything except /boot and stop anyone from getting at anything.

i dont bother though, because i trust my friends and if anyone's gonna actually break in and steal my computer my data is lost whether it's encrypted or not.

---

### Post by mark111 on 2009-04-20
You guys are fantastic!!!!

I was able to ge into the root using the recovery boot (thanks KPatz!).  I tried to edit the groups file, but gedit does not work in recovery boot as there is no GUI, and I was looking around for a text editor that was already installed, when I saw mikewhatever's post using the adduser command in the root.  Worked great. As I have no groups, for posterity, the command was:

adduser --<username> admin

Many thanks - I am now back up and running. Way cool!!!

---

### Post by kpatz on 2009-04-20
> **mark111 said:**
> I tried to edit the groups file, but gedit does not work in recovery boot as there is no GUI, and I was looking around for a text editor that was already installed...Time to learn how to use vi (vim)... ;)

---

### Post by CatKiller on 2009-04-20
> **kpatz said:**
> Time to learn how to use vi (vim)... ;)

Sicko :shock:

**nano** would be a much better choice for a new user.

---


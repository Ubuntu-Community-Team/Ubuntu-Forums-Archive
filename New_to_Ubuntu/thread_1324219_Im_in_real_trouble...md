---
title: "Im in real trouble.."
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Goldline on 2009-11-12
Alright so i was configuring root access under the user manager and then i thought hey
If i deselect "administer file system" under my account then only root can have access to the filesystem which is more secure. But it turned out the other way. I have the root password however, im unable to do any administrative tasks. Can you help me somehow!?
How can i restore access to the file system and regain access!?

---

### Post by Azrael3000 on 2009-11-12
can you run
```

gksudo users-admin

```

in a terminal?

and change permissions back

---

### Post by Goldline on 2009-11-12
I can run it however, after typing in the password it says:

copied/pasted:

Failed to run users-admin as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by ukripper on 2009-11-12
click on System-->Administration-->Users & Groups-->Then unlock and type in the root password there and select your account and give privilidges u want to give it!

hope it helps

---

### Post by Goldline on 2009-11-12
is there nothing else that can be done ?

Repair File System Perhaps!?

By using System restore to go back to a previous restorepoint!?

---

### Post by Goldline on 2009-11-12
Not working ukripper still requires Root.

---

### Post by Goldline on 2009-11-12
I have the Root password but the problem here is that i deselected 
administer File System under my user account.

---

### Post by Dougie187 on 2009-11-12
You could try this.

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

except, I don't think you need to do the passwd part. What you really want to do is edit the file /etc/group and add your name back to the admin group.

---

### Post by Goldline on 2009-11-12
Dougie the problem is not that i don't have access to root or that 
i need the root password i got the root password but i cannot administer the filesystem
with my account.

---

### Post by Goldline on 2009-11-12
Theres no group dir visible/.

---

### Post by philinux on 2009-11-12
I think you'll have use the recovery mode from grub or use livecd and then edit the file 

/etc/group and put you user name back in the group admin. In recovery file you use **nano /etc/group**

This is what mine looks like. You can just check your before you tinker with the same command. It does not require root to look a to the file.
```

cat /etc/group

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
**adm:x:4:username**
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:username
fax:x:21:
voice:x:22:
cdrom:x:24:username
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:username
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
fuse:x:103:
lpadmin:x:104:username
ssl-cert:x:105:
messagebus:x:106:
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:
couchdb:x:113:
haldaemon:x:114:
**admin:x:115:username**
saned:x:116:
pulse:x:117:
pulse-access:x:118:
gdm:x:119:
philcb:x:1000:
sambashare:x:120:username
winbindd_priv:x:121:
ntp:x:122:
```

The names have been changed to protect the innocent. ;)

---

### Post by Goldline on 2009-11-12
found the file, which line do i need to change exactly i dont want
to screw up the file.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> found the file, which line do i need to change exactly i dont want
to screw up the file.

You missed my post #11 you cannot change from where you are.

---

### Post by Dougie187 on 2009-11-12
Yeah, so you need to add your username back into the admin group.

So in a terminal try this, if you have the root password.

```
su
nano /etc/group
```

then, find the line that looks like this.
```

admin:x:115:
```

and modify it to look like this
```
admin:x:115:*username*
```

Where you replace username with your login name. Then you should be able to use sudo and administrative tasks again. At least if that is the correct problem, which is what I am understanding from your posts.

---

### Post by ukripper on 2009-11-12
i am not sure this will work but give it a shot. Boot into livecd and amend /etc/sudoer to include your username in that with privileges like below:
> username ALL=(ALL) ALL

---

### Post by Azrael3000 on 2009-11-12
dougie I think you are pointing out the right thing

but does he not also need

```

adm:x:4:username

```
?

[edit]
As Phil pointed out in post #11 :)
[/edit]

---

### Post by philinux on 2009-11-12
> **Azrael3000 said:**
> dougie I think you are pointing out the right thing

but does he not also need

```

adm:x:4:username

```
?

I highlighted that in my post #11.

---

### Post by Goldline on 2009-11-12
can i press a key to startup in recovery mode because by default the grub list is not being shown at my pc cuz i only got linux installed as os.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> can i press a key to startup in recovery mode because by default the grub list is not being shown at my pc cuz i only got linux installed as os.

Either escape key for legacy grub or shift key for grub2.

---

### Post by Azrael3000 on 2009-11-12
follow phils post... he was faster :)

---

### Post by philinux on 2009-11-12
> **Azrael3000 said:**
> follow phils post... he was faster :)

Lets hope he gets back up and running eh. ;)

---

### Post by Goldline on 2009-11-12
tried pressing esc key or shift but ubuntu proceeds as normal with the logonscreen.
Im not starting up in recovery mode hmz.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> tried pressing esc key or shift but ubuntu proceeds as normal with the logonscreen.
Im not starting up in recovery mode hmz.

You'll have to be quicker. If this is 9,10 then its the shift key.

Keep jabbing it after the bios post messages.

---

### Post by Goldline on 2009-11-12
During restart im pressing the left shift key numerous times but yet
no recovery screen pops up.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> During restart im pressing the left shift key numerous times but yet
no recovery screen pops up.

Do you see the  **grub loading** message?

If it not 9.10 then its the escape key hold it down after the bios stuff or hold down the shift key.

> GRUB 2's default menu will look familiar to GRUB users but there are a great number of differences beneath the surface.

    * On a new install of Ubuntu 9.10 with no other installed operating system, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed.
    * Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy).

---

### Post by Goldline on 2009-11-12
Its version 9.10

---

### Post by Saghaulor on 2009-11-12
I just had the same issue. 

I was trying to add my Active Directory admins to the sudoers file and accidentally locked myself out of the sudoers because I created my username as the same username in AD.

Anyways, changing the sudoers file can help if he adds him(her)self, but (s)he could just as easily re-add his/herself to the admin group.

As soon as your computer leaves the bios screen, hold down shift of esc, then the menu will appear.

---

### Post by Goldline on 2009-11-12
saghaulor,

Seems that you can only use the commandline in recovery mode hell i have no idea 
how-to do it without graphical interface. Can you help me !?
Q Which commands should i type to open groups etc/group in notepad.
And to edit the line "admin"

Thx

---

### Post by philinux on 2009-11-12
```
nano /etc/group
```

Just type it as I showed in my example. Print it out if need be, or right the highlighted ones down.

Use the up down left right arrow keys to navigate.

control+x to quit and choose Y to save the file.

type **reboot** after you finished.

---

### Post by Goldline on 2009-11-12
Thanks will try that.:D

---

### Post by Goldline on 2009-11-12
Update: ive edited the file and I granted myself permission to administer the filesystem.
Q about the recovery mode: so basically every1 who can access my computer internal
can goto recovery mode and use root!? isnt that a security risk !?

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> Update: ive edited the file and I granted myself permission to administer the filesystem.
Q about the recovery mode: so basically every1 who can access my computer internal
can goto recovery mode and use root!? isnt that a security risk !?

Yeah you fixed it.

Physical access to a pc means you got the lot if you know what you are doing. There are no security measure you could take save for encrypted drives. I cant be bothered with that for a home pc.

You could password the bios or grub. I think though with a live cd you could easily get at dat.

---

### Post by Goldline on 2009-11-12
Oh another thing in version 9.04 you could logon as the root user account
in a graphical environment there was an option 4 it. is this still possible with version 9.10? if so, how?

Need to edit a few files with root. And its ahwole lot easier with a graphical environment.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> Oh another thing in version 9.04 you could logon as the root user account
in a graphical environment there was an option 4 it. is this still possible with version 9.10? if so, how?

Not sure what that was on the recovery menu.

---

### Post by Goldline on 2009-11-12
let me epxlain it to you:

In the prev ubuntu version you could logon as root with your username and password at the logon screen. I cannot find that option anymore. Has it been removed ? or does it still exist in the current ubuntu version ?

In a desktop(graphical-environment_ I dont mean the commandline.

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> let me epxlain it to you:

In the prev ubuntu version you could logon as root with your username and password at the logon screen. I cannot find that option anymore. Has it been removed ? or does it still exist in the current ubuntu version ?

In a desktop(graphical-environment_ I dont mean the commandline.

That cant be a default as there is no root account set up in ubuntu.

There is only access to root via sudo as your problem showed. Some other distros have a root account.

---

### Post by Goldline on 2009-11-12
EDIT see this thread: [http://ubuntuforums.org/showthread.php?t=1324417](http://ubuntuforums.org/showthread.php?t=1324417)

---

### Post by Goldline on 2009-11-12
EDIT see this thread: [http://ubuntuforums.org/showthread.php?t=1324417](http://ubuntuforums.org/showthread.php?t=1324417)

Created a new thread and edited this post so its not posted twice.

---

### Post by philinux on 2009-11-12
Ah, right to enable that to work you must have first unlocked the root account which is disabled by default.

Not recommended at all.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Dougie187 on 2009-11-12
Glad you got it all fixed. Sorry I had to run to class.

---

### Post by Saghaulor on 2009-11-13
> **Goldline said:**
> Update: ive edited the file and I granted myself permission to administer the filesystem.
Q about the recovery mode: so basically every1 who can access my computer internal
can goto recovery mode and use root!? isnt that a security risk !?

Yes, if someone has physical access to your computer, then all security has been compromised.

You could encrypt your file system, but that only offers limited protection.

Password locking Grub and the Bios would help some.

Basically, all the aforementioned methods are effective at keeping most people out. However, if your computer was exposed to a very sophisticated hacker, the above mentioned methods would only function as speed bumps.

You can google Bios password hacks, and find a plethora of information regarding hacking into Bios. Also, google Evil Maid, it's a new attack that compromises disk encryption. I'm sure that there are ways to circumvent Grub.

But if I wanted what you had, and I had physical access to your computer, then I would just run a livecd and copy what I wanted. The Grub password would be useless. The Bios password would help insofar as you disabled the ability to boot from cd or usb. But Bios password is apparently easily circumvented. That's why disk encryption is important. At least then significant work must be done to extract the data.

I'll say it again. **Physical access is the single most important security measure. All other security measures can be overcome much easier once physical access to the computer is granted.**

---

### Post by Saghaulor on 2009-11-13
> **Goldline said:**
> Oh another thing in version 9.04 you could logon as the root user account
in a graphical environment there was an option 4 it. is this still possible with version 9.10? if so, how?

Need to edit a few files with root. And its ahwole lot easier with a graphical environment.

Just simply run one whatever program you need to do the editing with as root.

For example,

```
gksu nautilus
```
```
gksu gedit
```

Then you can edit with root privileges to your heart's desire. I recommend making backup copies of any file you modify so that you can easily restore it if you make a mistake.

Also, once you're done doing whatever it is that requires root privileges, be sure to close the program. It's unwise to run as root all the time, hence the reason why the root account was removed from Ubuntu; it's too much of a security risk.

Fyi, if you do decide to use disk encryption, make sure you backup your passkey, passwords, what have you, so that if you lose/forget them you are not locked out of your data.

---


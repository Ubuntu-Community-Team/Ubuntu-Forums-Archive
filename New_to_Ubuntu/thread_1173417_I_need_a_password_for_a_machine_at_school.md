---
title: "I need a password for a machine at school"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2009-05-29
I want to upgrade the Ubuntu machine at the school (there are 109 updates first). The login password is giving me an error message.

"Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '50331651' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpa_Gfl-' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Does anyone have suggestions?
I would really rather not reinstall.

---

### Post by s.fox on 2009-05-29
Hi,

Couple of questions:

1)  What is in your /etc/sudoers file?

```
cat /etc/sudoers
```

2)  Does that someone else have a root privilege on your machine?  What's the output of this command from a terminal?
[B]
Applications -> Accessories -> Terminal[/B]

```
groups
```

Thanks

-Ash R

---

### Post by dizzy1kenobi on 2009-05-29
mfs@mfs105:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied

mfs@mfs105:~$ groups
mfs adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse

---

### Post by s.fox on 2009-05-29
Hi,

You need to belong to both groups adm & admin in /etc/group but currently, admin is not in your group! That's why sudo won't work.

I [COLOR=Red]**THINK**[/COLOR] you need to boot into recovery mode from GRUB menu and at the prompt, do:

```

adduser mfs admin
id mfs
shutdown -r now
```(I assume mfs is your username...)

I would wait just to confirm that I am right,  but I am pretty sure thats the next stage.

-Ash R

---

### Post by anarchyinc on 2009-05-29
have you tried su with the root password instead? If it was a public computer that I managed I sure as hell wouldn't give anyone sudo rights.

---

### Post by dizzy1kenobi on 2009-05-29
when I booted into recovery mode, there was no prompt only a menu that would allow me to enter a password to enter root.  I am running 8.04.

---

### Post by k3lt01 on 2009-05-29
You use an interesting phrase as the title.

Most people would say "a machine at work" but you say " a machine at school". Are you a student? or a teacher? or someone who works at the school and has the right and responsibility to work with the PCs in such a way?

---

### Post by mikewhatever on 2009-05-29
The obvious question to ask the OP would be, Are you the system administrator, or are you trying to hack the machine?

---

### Post by dizzy1kenobi on 2009-05-29
Good question. I didn't even think of that.  I am the only one who is going to update the system and the person who installed it is not even here anymore.  I assure you though, there is no sensitive information on this machine.  Though I think the kids would be disappointed if I were to wipe everything with a reinstall.

---

### Post by wsonar on 2009-05-29
If you don't have the root password
and the original admin is no longer there
Back up the profile the kids use then reinstall

---

### Post by dizzy1kenobi on 2009-05-29
Now that you mention it this is probably not the place to have this conversation. The thread would be public. If I have to I'll just wait until the end of the year and do an install of 8.10.  Thanks for the help.

---

### Post by dizzy1kenobi on 2009-05-29
> **wsonar said:**
> If you don't have the root password
and the original admin is no longer there
Back up the profile the kids use then reinstall

Good idea why didn't I think of that?

---

### Post by k3lt01 on 2009-05-29
Like Wsonar said.

Back up the /home partition (or folder if its not a partition) and then do a complete reinstall. After you have reinstalled Ubuntu just copy the backup to /home and the vast majority of the settings will be reinstalled to as well as the students info.

The other option is if /home is a seperate partition and not just a folder, you dont even need to touch it. All you do is reinstall Ubuntu in the / partition. There are threads and sites that can help you do this, Psychocats site is very helpful and so is UbuntuGeeks. Just Google them and you will find the info you need to help you on your way.

---

### Post by bodhi.zazen on 2009-05-29
Boot to recovery mode

drop to a shell, this will give you root access.

Add your user to the admin group.

```
usermod -G admin -a <user>
```

Substitute "<user>" for your log in user name.

Note: sure the information *could be misused, however the OP has physical access so the system is open.

---

### Post by The Cog on 2009-05-29
The alternate CD has a recovery mode where you can choose a partition to switch to (I forget the exact wording of the option). Once you have switched partitions, you are root on the target partition, and can change your password as usual with the **passwd** command.

---

### Post by bodhi.zazen on 2009-05-29
chroot ?

---

### Post by Sef on 2009-05-30
Read [Psychocats Reset Password]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by huwnet on 2009-05-30
I don't think there is any need to use a recovery CD or similar. Just boot into single user mode, which makes you root. Then you can change any passwords or account permissions and reboot.

Google has the details!

---

### Post by The Cog on 2009-05-30
> **huwnet said:**
> I don't think there is any need to use a recovery CD or similar. Just boot into single user mode, which makes you root. Then you can change any passwords or account permissions and reboot.

Google has the details!

But post #6 says recovery mode wants a password. This happens if a root password has been set. I don't think recovery mode will get him in. This is why I suggest the repair option on the alternate install CD, which can mount the disk and then chroot to it so he can use the passwd command to correct or remove the root passwd.

---

### Post by dizzy1kenobi on 2009-05-30
Thanks for the help.  I will work on it Monday and see what I can do.  I ran out of time Friday.

---

### Post by durand on 2009-05-30
If you wait till october, you'll be able to install 9.10.

---


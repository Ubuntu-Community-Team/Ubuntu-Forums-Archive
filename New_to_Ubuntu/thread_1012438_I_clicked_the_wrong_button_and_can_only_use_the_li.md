---
title: "I clicked the wrong button and can only use the live cd"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by becca4225 on 2008-12-15
This is my third day using ubuntu 8.4.1 (after having installed it from a live cd) and when trying to alter file permissions (by using nautilus in root aka typing sudo nautilus in the terminal).

I highlighted all the files in the / and right clicked, went to permissions but acciendtally pressed a button called "apply permissions to enclosed files".

The text on the screen went to boxes and my red desktop went gray-rebooted the computer and get a "busybox" screen?!

I have tried googling this to no avail-thank you for any help!

---

### Post by jerome1232 on 2008-12-15
Yeah that pretty much borked the system, you recursively changed all permissions on all files, if you have personal files that must be backed up I would do so from a live cd and then reinstall the OS. 

This is why it's bad to get in the habit of running nautilus as root, it's to easy to make an 'ooops'. Certain system files have to have their permissions set a certain way or the system will not work, restoring those files to their original state would be an incredibly tedious task.

---

### Post by becca4225 on 2008-12-15
thank you for that, i will do a reinstall-a nice lesson i have learnt!-thank god my important files are backed on a separate drive!
and thank you for the quick reply!

---

### Post by starcannon on 2008-12-15
I think the easiest way is to just reinstall the system.
I read somewhere how to "fix" this issue once, but if memory serves, it was a bit complicated, and a reinstall would actually probably take less time.

If you have information that you need to back up first, then do so using an external storage device (thumbdrive or some other usb drive) while using the liveCD.

If you decide to do a reinstall, be sure to take the time to choose manual at the Partition dialogue page.
Set root aka / to around 10gb, if you think you'll try out a ton of software make it larger.
Set swap to >= the amount of ram in your computer (general rule is twice as much swap as ram)
Set the remainder of the hard drive to /home

Now if you have a mess up you can recover much more easily as /home (where all your good stuff is) will be on its own partition.

I would also take this time to mention that unless you know what your doing, and/or have some real need, do not mess with permissions; there lie dragons, and ye are crunchy and tasty with ketchup.

GL and have fun

PS: when running any gui as root you should use:
```
gksu some_command
```
not sudo

---

### Post by becca4225 on 2008-12-15
for future reference what would be the way of "fixing it" if there is one?

---

### Post by oldos2er on 2008-12-15
You don't say why you want to alter permissions, or which files you wish to alter. What exactly are you trying to "fix"?

 You might want to read [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) and [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

---

### Post by becca4225 on 2008-12-15
i have the account which controls the settings-not root, dont know the name but it was the first account created during installation-and i dont want other users to see system files etc

perhaps i went about it the wrong way?

---

### Post by starcannon on 2008-12-15
sorry I just can't remember, I remember running across the fix on a completely unrelated search a couple months ago, and I'll be damned if I can remember how I found it, I know its here in the forums, but thats like saying, "theres a needle at the bottom of the ocean". If I run across it I'll pm you, I googled it till my fingernails bled but no dice sorry :(

---

### Post by Tatty on 2008-12-15
Just a small note,

When running graphical applications with superuser privilages you should use gksu instead of sudo.

So to run nautilus as superuser you should do:

```
gksu nautilus
```

---

### Post by becca4225 on 2008-12-15
> **starcannon said:**
> sorry I just can't remember, I remember running across the fix on a completely unrelated search a couple months ago, and I'll be damned if I can remember how I found it, I know its here in the forums, but thats like saying, "theres a needle at the bottom of the ocean". If I run across it I'll pm you, I googled it till my fingernails bled but no dice sorry :(

Thanks for that-however I will just have to reinstall and be more careful....how do you set permissions as so other users like a "guest account" can not access any files but their own home directory?-or is that a difficult task for a newbie?

---

### Post by oldos2er on 2008-12-15
> **becca4225 said:**
> i have the account which controls the settings-not root, dont know the name but it was the first account created during installation-and i dont want other users to see system files etc

perhaps i went about it the wrong way?

 You really should read the links I posted. You're trying to fix something which isn't broken.

---

### Post by jerome1232 on 2008-12-15
I'm seconding reading up on the file permissions and just to add, a regular user cannot modify any system files, they cannot view some either. The logs are an example, they cannot be viewed unless you are root or in the syslog or adm groups.

---

### Post by becca4225 on 2008-12-15
thank you ann and jerome 1232, however, i wasn't aware that this didn't need to be changed-i was of the opposite opinion.
The ways of a newbie I suppose-but next time I will google it and ask on the forums, and try not to do anything i could regret.

thank you to all those who helped!

---

### Post by Tatty on 2008-12-15
> **becca4225 said:**
> Thanks for that-however I will just have to reinstall and be more careful....how do you set permissions as so other users like a "guest account" can not access any files but their own home directory?-or is that a difficult task for a newbie?

Do you mean so they cannot see these files?  Obviously they cannot edit these files by default.

---

### Post by becca4225 on 2008-12-15
> **Tatty said:**
> Do you mean so they cannot see these files?  Obviously they cannot edit these files by default.


Yes so they can not see the files, is that also possible?

---

### Post by starcannon on 2008-12-15
In /home set the permissions on your username folder to how you want them.

in nautilus you would surf to /home/your_folder

R-click the /home/your_folder and set the permissions, you can recurse them if you like. Just don't fool around with your root directory hehe.

---

### Post by becca4225 on 2008-12-15
thank you to all, with your help i have resolved to reinstall and continue to research on the program.

---

### Post by jflaker on 2008-12-15
> **becca4225 said:**
> Thanks for that-however I will just have to reinstall and be more careful....how do you set permissions as so other users like a "guest account" can not access any files but their own home directory?-or is that a difficult task for a newbie?

Guest is jailed to the desktop, has no home and no access to any /home folder and I believe that any folders/files created are removed when guest logs off.......I wouldn't worry about guest.

Regular users have access to their home only and not to others' /home.  If you create an elevated rights account, that is where you will see some issues as they can always become su.

If I remember correctly, file/folder permissions are deny FIRST, then allow. That means that if the user is part of one group that HAS access to a file/folder and is also a member of another group that is restricted from that file/folder, then the user won't have rights...

If possible, try to control access by group instead of users

---

### Post by redseventyseven on 2008-12-15
> **becca4225 said:**
> Thanks for that-however I will just have to reinstall and be more careful....how do you set permissions as so other users like a "guest account" can not access any files but their own home directory?-or is that a difficult task for a newbie?

As already mentioned in this thread, this is a problem that doesn't exist in Linux, though I can understand your concern as secondary users tinkering around with system files is a big problem in Windows!

Essentially there are three types of users available in Linux:

1) Root - this is the user that has permanent administrative privileges to tinker about with anything and everything without being asked for verification. This type of user is disabled in Ubuntu, though exists in other forms of Linux (e.g. PCLinuxOS)

2) Users which can adopt root privileges temporarily (using sudo or gksudo). They have their own The first user account created in ubuntu is of this type of account.

3) Users which can't adopt root privileges (and therefore can't tinker about with system files).

I would suggest experimenting, rather than purely relying on reading and googling. Try creating a temporary user account as though it were the secondary user account and see if it behaves the way you want to (e.g. log on as that user and try to do something that requires temporary root privileges and see if the system thwarts you from doing so).

Hope this helps!

---


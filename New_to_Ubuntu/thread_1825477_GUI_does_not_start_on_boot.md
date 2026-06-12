---
title: "GUI does not start on boot"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by ssn116 on 2011-08-15
Hello,
I have Windows XP/Ubuntu 11.04 (upgraded to 11.04 from old Ubuntu versions) dual boot installed on my laptop. Yesterday, all of a sudden, my GRUB stopped loading. I kept getting error 24.
Based on a bit of searching on google, I made a bootable USB drive and booted my laptop using this. When I tried to access the partition on which Ubuntu was installed, I would get a message saying that the disk could not be mounted. I tried re-installing GRUB, but I still got the same error 24. After a little more searching on the net, I did a disk check fsck and after doing the suggested changes, I finally got GRUB to load. I can boot into XP and Ubuntu, but the GUI does not load in Ubuntu. I have used Ubuntu for a while, but I am not experienced enough to be able to operate without the GUI. 
I need to extract my Evolution work e-mails that were stored on this partition. I was stupid enough to forget to back these up. All my other data I had backed up less than a week ago. I found out that these should be stored in the /.local/share directory, but I cannot see the file. Maybe the disk check corrections I made have deleted or corrupted some data. I am getting the feeling that I should have made this post before doing that.
Can anybody please help?
Regards,
Sameet.

---

### Post by androssofer on 2011-08-15
> **ssn116 said:**
> Hello,
I have Windows XP/Ubuntu 11.04 (upgraded to 11.04 from old Ubuntu versions) dual boot installed on my laptop. Yesterday, all of a sudden, my GRUB stopped loading. I kept getting error 24.
Based on a bit of searching on google, I made a bootable USB drive and booted my laptop using this. When I tried to access the partition on which Ubuntu was installed, I would get a message saying that the disk could not be mounted. I tried re-installing GRUB, but I still got the same error 24. After a little more searching on the net, I did a disk check fsck and after doing the suggested changes, I finally got GRUB to load. I can boot into XP and Ubuntu, but the GUI does not load in Ubuntu. I have used Ubuntu for a while, but I am not experienced enough to be able to operate without the GUI. 
I need to extract my Evolution work e-mails that were stored on this partition. I was stupid enough to forget to back these up. All my other data I had backed up less than a week ago. I found out that these should be stored in the /.local/share directory, but I cannot see the file. Maybe the disk check corrections I made have deleted or corrupted some data. I am getting the feeling that I should have made this post before doing that.
Can anybody please help?
Regards,
Sameet.

when you boot ubuntu... what happens?

command line?

 if so, log in. type your username then password(what else :-p). then type ```
sudo /etc/init.d/gdm start
``` and that should lanuch the gui for ya. post any errors etc if it doesnt work...

---

### Post by ssn116 on 2011-08-15
Thank you androssofer for your prompt reply. When I boot into Ubuntu, I get this message 
'init: ureadahead main process (264) terminated with status 5'
After that I get the login screen. After logging in, I get the following lines:
'apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
/usr/lib/update-notifier/update-motd-updates-available: 52 : cannot create /var/lib/update-notifier/updates-available: Directory nonexistent
run-parts: /etc/update-motd.d/90-updates-available exited with code 2
/usr/lib/update-manager/release-upgrade-motd: 40 : cannot create /var/lib/update-notifier/release-upgrade-available: Directory nonexistent
/usr/lib/update-notifier/update-motd-fsck-at-reboot: 66 : cannot create /var/lib/update-notifier/fsck-at-reboot: Directory nonexistent
run-parts: /etc/update-motd.d/98-fsck-at-reboot exited with code 2
.
.
.
.
.
No directory, logging in with HOME=/'
When I enter the command from your message, I get 
'Rather than invoking init scripts through /etc/init.d, use the service( 8 ) utility, e.g. service gdm start

Since the script you are trying to invoke has been converted to an Upstart job, you may also use the start( 8 ) utility, e.g. start gdm gdm start/running, process 2592'

Then the screen goes blank for a second and then I get the prompt again.

Regards,
Sameet.

---

### Post by androssofer on 2011-08-15
> **ssn116 said:**
> Thank you androssofer for your prompt reply. When I boot into Ubuntu, I get this message 
'init: ureadahead main process (264) terminated with status 5'
After that I get the login screen. After logging in, I get the following lines:
'apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
apt-config: error while loading shared libraries: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory
/usr/lib/update-notifier/update-motd-updates-available: 52 : cannot create /var/lib/update-notifier/updates-available: Directory nonexistent
run-parts: /etc/update-motd.d/90-updates-available exited with code 2
/usr/lib/update-manager/release-upgrade-motd: 40 : cannot create /var/lib/update-notifier/release-upgrade-available: Directory nonexistent
/usr/lib/update-notifier/update-motd-fsck-at-reboot: 66 : cannot create /var/lib/update-notifier/fsck-at-reboot: Directory nonexistent
run-parts: /etc/update-motd.d/98-fsck-at-reboot exited with code 2
.
.
.
.
.
No directory, logging in with HOME=/'
When I enter the command from your message, I get 
'Rather than invoking init scripts through /etc/init.d, use the service( 8 ) utility, e.g. service gdm start

Since the script you are trying to invoke has been converted to an Upstart job, you may also use the start( 8 ) utility, e.g. start gdm gdm start/running, process 2592'

Then the screen goes blank for a second and then I get the prompt again.

Regards,
Sameet.

hummmm. on the login screen, does it say sumthing like "tty1" anywer...? if so try hitting: 

ctrl alt f7

after u do the command: 

```
sudo /etc/init.d/gdm start
```

see if that works.

or try: 

```
sudo apt-get --reinstall install gdm
```

tht will reinstall and hopefully fix any dependencies issues that it has. past that, might need to backup and reinstall ubuntu. unless sum1 else comes along who knows more.. i'm still noobish myself :p 

after some research your emails should be in:

/home/<username>/.evolution

so hav a look ther. 
```

cd /home/<username>/.evolution

ls
```(not sure how much command line u know :) )

then u could move em to a pen drive or external hd...

---

### Post by ssn116 on 2011-08-15
Thank you again, androssofer for your prompt reply. 
You were right about the tty1 message. If I did 
sudo /etc/init.d/gdm start, I would get tty2. Ctrl+Alt+F7 after sudo /etc/init.d/gdm start brought up a blank screen with a flashing cursor and then nothing happened. The re-install too, failed. And strangely enough, the home folder is missing. ls shows the home folder after I login, but after doing cd home, I get a message saying that home is not a directory.
I will re-install Ubuntu, no worries. And remember to also back-up my mail this time.
Thanks for your help.

---

### Post by androssofer on 2011-08-16
> **ssn116 said:**
> Thank you again, androssofer for your prompt reply. 
You were right about the tty1 message. If I did 
sudo /etc/init.d/gdm start, I would get tty2. Ctrl+Alt+F7 after sudo /etc/init.d/gdm start brought up a blank screen with a flashing cursor and then nothing happened. The re-install too, failed. And strangely enough, the home folder is missing. ls shows the home folder after I login, but after doing cd home, I get a message saying that home is not a directory.
I will re-install Ubuntu, no worries. And remember to also back-up my mail this time.
Thanks for your help.

no worries. no idea wot is wrong with your gui... sounds perhaps like a refresh rate problem in the Xserver. but thts a guess at best, and i hav no idea how to fix sed guess... :-(

reinstall ubuntu is prob the best option now... tho lets get these emails 1st!
 try:

```
cd
```

cd on its own should take you to your home.(ie: /home/username) then do:

```
ls -a
``` and tht will show up all the folders in ur home. .evolution should show up with them. if so, then do ```
cd .evolution
``` and your in!

---


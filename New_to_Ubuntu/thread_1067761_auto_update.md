---
title: "auto update"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Billisnice on 2009-02-12
I am using 8.04.2 and want the computer to update the OS and programs automatically. I get tired of updating. How? 

Thanks

---

### Post by drs305 on 2009-02-12
You can install security updates automatically with:
System > Administration > Synaptic. Settings > Repositories > Updates. Install Security Updates without confirmation. Set the time period you want to check for updates as well.

Since Hardy is a LTS, this should cover a lot of the updates available to you.

---

### Post by Billisnice on 2009-02-12
Will this auto update program like totem, etc too?

thanks

---

### Post by hyper_ch on 2009-02-12
it will update everything that was installed from the repositories - if there are updates in the repositories.

---

### Post by drs305 on 2009-02-12
I believe only major security fixes would be automatically installed with the settings I provided in Hardy. With other updates you will  still be asked if you want to install them.

To get updates for normal applications, one way you could do it would be to either make a cron job or use anacron. You could run a "sudo apt-get update && sudo apt-get upgrade" command to automatically run updates.

Here are some considerations:
You would need to use the "-y" switch with the upgrade command so it would run without asking you if you wanted to update the packages.
Since it runs with "sudo", you would need to modify your *sudoers* file to allow "apt-get" to run without asking for a password or place the script somewhere in your /etc/init.d folder.
You can use an app called gnome-schedule to help create the cron job. Once it is installed, the app is in the System Tools menu.

---

### Post by Billisnice on 2009-02-12
sound complicated for a beginner, can i just install gnome-schedule? If so, where can i get it?

thanks

---

### Post by drs305 on 2009-02-12
gnome-schedule is available in synaptic. Make sure you have "universe" selected in the "Ubuntu Software" tab. You would still have to make a simple BASH script, make it executable, and then edit the sudoers file to allow you to run the command without entering a password. 

You are correct that it is a bit complicated. If you want to learn about BASH scripting and the sudoers file it would be an excellent exercise. 

Two options you might find more to your liking: 
1. Do a search of these forums for topics for "automatic updates" - the topic has most likely already been addressed and you can probably use other people's efforts to easily automate the task.
2. ubuntu can automatically tell you when updates are available. Without making any changes, you can always just click "Yes" when it asks. If you aren't getting notified of updates, you can change the setting in the Settings > Respository section of synaptic.

---


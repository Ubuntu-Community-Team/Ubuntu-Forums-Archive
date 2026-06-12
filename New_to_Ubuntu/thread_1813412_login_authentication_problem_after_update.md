---
title: "login authentication problem after update"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Shahram A on 2011-07-27
27 July 2011
  Last night after new updates, during shutdown, a debug dialogue box appeared saying the Authentication… crashed.  Since the computer was shutting down nothing could be done.
  Starting the system again, the login screen either responds with authentication failure or it disappears for seconds with a black screen with text and returns to the login screen again.
  I have tried all the options for logging in including safe mode, but the same thing happens.
  I have also tried to login by using other and typing my username and password, but get the same problem.
  The problem is similar to thread:
  [http://ubuntuforums.org/showthread.php?t=1804806&highlight=Ubuntu+login+fail](http://ubuntuforums.org/showthread.php?t=1804806&highlight=Ubuntu+login+fail)
  I have tried to login by using alt+ctrl+F1 which I saw in other questions in the forum; however in the text screen again using my username and password, the response is login incorrect, which means the user named is not be recognized.
  Following how to reset your password & username in 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
   I have tried to boot (holding shift down) to recovery mode and *Drop to root shell prompt* option.
  When typing ls /home
  I have my computer name with a question mark.
  Typing my username to change it:
  passwd *username*
  It responds the username does not exist.
  I have also used the recovery mode with the option repair broken packages but the problem was not fixed.
  Since I am not technical, I had used the easiest installation, i.e. everything in one partition, and I don’t want to lose my data.
  I am using the latest Ubuntu installation which is an upgrade on the previous version.
  Can anyone guide me in very simple, step by step instructions.
  Thank you.

---

### Post by schnelle02 on 2011-07-27
Perhaps you would be able to get in using the root account, for details on that read [this]("https://help.ubuntu.com/community/RootSudo").  Otherwise you could use a live cd from boot to save all your files.

---

### Post by Shahram A on 2011-07-27
> **schnelle02 said:**
> Perhaps you would be able to get in using the root account, for details on that read [this]("https://help.ubuntu.com/community/RootSudo").  Otherwise you could use a live cd from boot to save all your files.
The problem is that in root (via recovery council) it still needs login which fails.
Are there any instuction pages for copying from boot to save all files from a live CD?
Thank you

---

### Post by schnelle02 on 2011-07-27
I am about to head home so I didn't get a chance to find the best site.  This one is for recovering a drive from a dead windows machine, but it should work all the same.  Read about recovering files [here]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/").

---

### Post by Shahram A on 2011-07-27
> **schnelle02 said:**
> I am about to head home so I didn't get a chance to find the best site.  This one is for recovering a drive from a dead windows machine, but it should work all the same.  Read about recovering files [here]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/").
Thank you Andrew
You last suggestion gave me the idea to go in to recovery mode as described in
 [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
  I used the name root as the login name and reset the password to my own password and the rebooted normally. Then on the login screen I used other and for user typed root and added the password.
Now I have actually logged in but to a new desktop which I assume is with root permissions. I might be able to reset my username or at least copy my files. I'll post the result once I look around to see what I can do. But if there is any guide for this situation I would appreciate if you can advise me.

---

### Post by westie457 on 2011-07-27
Here is a suggestion that so far has worked for me every time. Whether up-grading to a newer version or some disaster recovery.

Reinstall to the same partition and same file system (EG ext4) and not formatting, also remembering to use as / 'root'. The installer complains a bit about not formatting, click Forward, and the install goes ahead leaving everything in your home folder alone.

It is a not very elegant (read simple) solution but it does work.

---

### Post by Shahram A on 2011-07-27
> **westie457 said:**
> Here is a suggestion that so far has worked for me every time. Whether up-grading to a newer version or some disaster recovery.

Reinstall to the same partition and same file system (EG ext4) and not formatting, also remembering to use as / 'root'. The installer complains a bit about not formatting, click Forward, and the install goes ahead leaving everything in your home folder alone.

It is a not very elegant (read simple) solution but it does work.
Thank you for this suggestion. I think because of the risks I leave it as the last option. In other threads I read that the same solution sometimes damages or wipes documents etc...
Right now I am trying to get to my home folder with root login to copy everything. Then to find if I can resuse the home folder with the previous username or a new one.

---

### Post by Shahram A on 2011-07-27
From the file system I can go to home directory but there is a message in a text format there that the directory has been unmounted to protect my data, there is a command line instruction to run: ecryptfs-mount-private 
However in the terminal the script gives the following result:
ERROR: Encrypted private directory is not setup properly.

---

### Post by Shahram A on 2011-07-27
I tried from system - users and groups to see if I could regain my last username and password, However the application does not respond, gets stuck not being able to close it.
--------------------------------------------------------------------
On a different note because of a message that I had seen about crash report fail
In GUI with root I followed instruction by [Nuc72]("http://ubuntuforums.org/member.php?u=1290625") on
[http://ubuntuforums.org/showthread.php?t=1745793&page=2](http://ubuntuforums.org/showthread.php?t=1745793&page=2)
- Edit the file "apport" as superuser in /etc/default/
- Set 1 to Enabled (it was 0 by default in my case)

I hope it would have some effect

---

### Post by westie457 on 2011-07-27
> **Shahram A said:**
> From the file system I can go to home directory but there is a message in a text format there that the directory has been unmounted to protect my data, there is a command line instruction to run: ecryptfs-mount-private 
However in the terminal the script gives the following result:
ERROR: Encrypted private directory is not setup properly.

Maybe this will be helpful for you. 
[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

---

### Post by Shahram A on 2011-07-27
1

---

### Post by Shahram A on 2011-07-27
> **westie457 said:**
> Maybe this will be helpful for you. 
[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)
It certainly appears to be very relevent to my problem. I have downloaded the Ubuntu Image to make CD and shall try this a little later.
Thank you very much

---

### Post by Shahram A on 2011-07-30
I was able to recover my documents and my default username and pass; the following is the shorterned story:

Having in mind the instructions on the following page:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I tried to remake my user name through recovery console by root, but failed.
Since my default user first letter was capital and I didn't know how to address the problem, I added a user with the same name but with no capital letters. However it didn't open my default account, and I had just added a user without a home folder.

Using the same instruction on psychocats webpage, I gave root a password and restarted the computer.
Now by choosing other I logged in as root.

on the terminal as root again I tried to regain my user name and password:

root@Flourishing:~# ls /home
flourishing7
root@Flourishing:~# passwd Shahram
passwd: user 'Shahram' does not exist

I tried to reach my documents by going to my user home folder, however because of encryption, I could not see my folders and documents.

In my user home folder there was document called: Access-Your-Private-Data
clicking on this document gave the following dialogue box:

Untrusted application launcher
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not knowthe source of this file, launching it may be unsafe.

& on the dialogue box there was no option apart from cancelling.
There was also a read me text saying:

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"
or
From the command line, run:
 ecryptfs-mount-private

Therefore I used the terminal to run ecryptfs-mount-private
to decrypt my home folder in the following way which gave error.

I looked up the following page suggested to me by Andrew (above) as help in doing this:

[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

root@Flourishing:~# ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

I used sudo in the following manner with no result:

root@Flourishing:~# sudo mount /dev/sdal/mnt
mount: can't find /dev/sdal/mnt in /etc/fstab or /etc/mtab

So I changed root to my home folder's name with the following result:

root@Flourishing:~# su - flourishing7
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

I followed the instruction with the following result:

flourishing7@Flourishing:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [c864b7f6948e2a22] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/flourishing7

Since I had logged in a graphic mode with root, now I could open the home folder showing all my documents which I copied to an external drive.

Meanwhile I discoverd that if I closed the terminal the home folder became inaccessible again and I had to reenter the code to decrypt and keep the terminal open.

I tried again to set my user name and pass right again:

flourishing7@Flourishing:~$ passwd Shahram
passwd: user 'Shahram' does not exist

Then I tried the user that I had added without capital characters:

flourishing7@Flourishing:~$ passwd shahram
passwd: You may not view or modify password information for shahram.

I tried the following:
flourishing7@Flourishing:~$ adduser --no-create-home Shahram
Command 'adduser' is available in '/usr/sbin/adduser'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
adduser: command not found

I tried it with root:

flourishing7@Flourishing:~$ su - root
Password: 
root@Flourishing:~# adduser --no-create-home Shahram
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM} configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.

It took a little bit searching and trial and error to find the correct code:

root@Flourishing:~# adduser --no-create-home --force-badname Shahram
Allowing use of questionable username.
Adding user `Shahram' ...
Adding new group `Shahram' (1002) ...
Adding new user `Shahram' (1002) with group `Shahram' ...
Not creating home directory `/home/Shahram'.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for Shahram
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y
root@Flourishing:~# 

Now I had regained my default username and Password.
I logged out of root and logged in to my default user name.

Although now I have two Shahram (with capital) one of which does not work and a third one shahram (without capital) that does not work because it doesn't have a home folder. Also it takes a little longer for the desktop and the menus to appear after login; and on the shutdown button I see "Shahram (Shahram)" as my user name; apart from this everything else is ok.

---


---
title: "Authentication failure in Terminal"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-09-09
I can't figure out what I'm doing wrong, and this is driving me nuts!  This is only the second or third time I've been playing with Xubuntu (I have a quad boot), and I can't figure out how to use the terminal.  I figured it out once before. I thought I ran su then put in my password, but now it won't recognize my password.  I've been messing with this for over an hour with no luck.  

I searched Google without any luck, and I can't search youtube because flash won't install.  I tried to update the system, and it keeps on telling me that I have 200 updates available...  I then wanted to just upgrade to the 10.10 alpha, and it let me run update-manager -d, but it doesn't actually install anything.  I went to reboot, and it won't let me reboot, only log out!

If someone could guide me to a good tutorial on how to use the Xubuntu terminall I'd appreciate it.  I'd like to fix my problems with it...


Thanks

---

### Post by Peter09 on 2010-09-09
Not sure about XUbuntu but in Ubuntu you should use the sudo command to elavate your priviledges.
 
```
sudo <command you wish to execute>
```
 
so you would want
 
```
sudo update-manager -d
```

---

### Post by giddyup306 on 2010-09-09
> **Peter09 said:**
> Not sure about XUbuntu but in Ubuntu you should use the sudo command to elavate your priviledges.
 
```
sudo <command you wish to execute>
```so you would want
 
```
sudo update-manager -d
```

I know my way around the Ubuntu terminal, but when I try to run sudo in Xubuntu it says...

```
sudo: must be setuid root

```

---

### Post by jrev on 2010-09-09
if you type <sudo su> into terminal you should get the # invite which means you are the admin.
If you forget your password you can type a new one by the command ```
sudo passwd 
``` 
via a live CD

---

### Post by JohnHeikkila on 2010-09-09
[QUOTE="http://ubuntuforums.org/showpost.php?p=1467656&postcount=4"]I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```
but I knew better...


so I put 

chown root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.[/QUOTE]

Search function is not to be forgotten!

---

### Post by giddyup306 on 2010-09-09
> **jrev said:**
> if you type <sudo su> into terminal you should get the # invite which means you are the admin.
If you forget your password you can type a new one by the command ```
sudo passwd 
```via a live CD

I tried both of those (I read the documentation in the terminal about 5 times).

They both give me the same message...

```
sudo: must be setuid root

```

I didn't forget my password because I use the same password on all my computers so I don't forget them.

This is really starting to annoy me.  What gives???

---

### Post by giddyup306 on 2010-09-09
> **JohnHeikkila said:**
> Search function is not to be forgotten!
I did several searches.

```
No command 'chwon' found, did you mean:
 Command 'chcon' from package 'coreutils' (main)
 Command 'chown' from package 'coreutils' (main)
chwon: command not found

```

---

### Post by Peter09 on 2010-09-09
I think its a typo - its the 'chown' command which changes the owner of a file.

---

### Post by JohnHeikkila on 2010-09-09
Yeah, sorry for the typo. It's "chown" not "chwon".

---

### Post by coffeecat on 2010-09-09
@giddyup306, I'm not quite sure whether you noticed the mention of recovery console in JohnHeikkila's post. This is important because it gives you root powers to repair the damaged /usr/bin/sudo file without using sudo.

Here's a useful link complete with screenshots:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

And another link that says much the same thing, but more concisely:

[http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html](http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html)

---

### Post by JohnHeikkila on 2010-09-09
I would recommend the "psychocats.net" article on fixsudo. It's exactly what I was trying to say.

---

### Post by giddyup306 on 2010-09-14
> **JohnHeikkila said:**
> I would recommend the "psychocats.net" article on fixsudo. It's exactly what I was trying to say.


> **coffeecat said:**
> @giddyup306, I'm not quite sure whether you  noticed the mention of recovery console in JohnHeikkila's post. This is  important because it gives you root powers to repair the damaged  /usr/bin/sudo file without using sudo.

Here's a useful link complete with screenshots:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

And another link that says much the same thing, but more concisely:

[http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html](http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html)

I tried both of them, neither of them worked.  It did tell me

```
*sudo is mode _____, should be 0440*, then  you'll want to type
```This is really annoying me!  It's not recognizing my password, or giving me root permission.  I can't update the system.  I can't install programs.  I can't mount partitions.  Ahhhh!!!!

This is what it says in the terminal.

```

NAME
       sudo_root - How to run administrative commands

SYNOPSIS
       sudo command

       sudo -i

INTRODUCTION
       By default, the password for the user "root" (the system administrator)
       is locked. This means you cannot login as root or use su. Instead,  the
       installer  will  set  up  sudo to allow the user that is created during
       install to run all administrative commands.

       This means that in the terminal you can  use  sudo  for  commands  that
       require  root privileges. All programs in the menu will use a graphical
       sudo to prompt for a password. When sudo asks for a password, it  needs
       your password, this means that a root password is not needed.

       To  run  a command which requires root privileges in a terminal, simply
       prepend sudo in front of it. To get an interactive root shell, use sudo
       -i.

ALLOWING OTHER USERS TO RUN SUDO
       By  default, only the user who installed the system is permitted to run
       sudo. To add more administrators, i. e. users who  can  run  sudo,  you
       have  to  add these users to the group 'admin' by doing one of the fol&#8208;
       lowing steps:

       * In a shell, do

           sudo adduser username admin

       * Use the graphical "Users & Groups" program in the  "System  settings"
         menu to add the new user to the admin group.

BENEFITS OF USING SUDO
       The benefits of leaving root disabled by default include the following:

       * Users  do  not  have  to  remember  an extra password, which they are
         likely to forget.

       * The installer is able to ask fewer questions.

       * It avoids the "I can do anything" interactive login by default -  you
         will  be  prompted  for  a  password before major changes can happen,
         which should make you think about the consequences of  what  you  are
         doing.

       * Sudo adds a log entry of the command(s) run (in /var/log/auth.log).

       * Every  attacker  trying  to  brute-force their way into your box will
         know it has an account named root and will try that first. What  they
         do not know is what the usernames of your other users are.

       * Allows  easy  transfer for admin rights, in a short term or long term
         period, by adding and removing users from the admin group, while  not
         compromising the root account.

       * sudo can be set up with a much more fine-grained security policy.

       * On systems with more than one administrator using sudo avoids sharing
         a password amongst them.
DOWNSIDES OF USING SUDO
       Although for desktops the benefits of using sudo are great,  there  are
       possible issues which need to be noted:

       * Redirecting  the output of commands run with sudo can be confusing at
         first. For instance consider

           sudo ls > /root/somefile

         will not work since it is the shell that tries to write to that file.
         You can use

           ls | sudo tee /root/somefile

         to get the behaviour you want.

       * In  a  lot  of office environments the ONLY local user on a system is
         root. All other users are  imported  using  NSS  techniques  such  as
         nss-ldap. To setup a workstation, or fix it, in the case of a network
         failure where nss-ldap is broken, root is  required.  This  tends  to
         leave  the  system  unusable. An extra local user, or an enabled root
         password is needed here.

GOING BACK TO A TRADITIONAL ROOT ACCOUNT
       This is not recommended!

       To enable the root account (i.e. set a password) use:

           sudo passwd root

       Afterwards, edit the sudo configuration with sudo  visudo  and  comment
       out the line

           %admin  ALL=(ALL) ALL

       to disable sudo access to members of the admin group.

SEE ALSO
       sudo(8), https://wiki.ubuntu.com/RootSudo



```
I have no idea...

---


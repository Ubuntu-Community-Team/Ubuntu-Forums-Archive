---
title: "windows &amp; ubuntu printer sharing"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by tarclee on 2006-08-29
can i know how to use windows pc to print printer in ubuntu pc?when i connect to the ubuntu pc,it ask me the username n password.how can i add samba user n password?

---

### Post by cosborn72 on 2006-08-29
tarclee

Assuming you have already set up samba.  You may need to add the windows user to the samba users file.  

Here are the directions on how to use smbpasswd to add a user.

[http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users)

Next, you may need to edit the smb.conf file to make the printer available.

[http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba](http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba)

Try this and see if you can then print.  Use the username and password you set up for samba to connect to the printer.  I relatively new at cups and samba, but these steps seemed to work for me.


(Thanks to the Ubuntu Guide for the directions.)

---

### Post by tarclee on 2006-08-29
yes,samba already setup.but how to change the user environment to root environment?to add a samba user is it need did in root environment?i have try in user environment,it say the username already exist in unix system.

---

### Post by tarclee on 2006-08-29
the error msg is as below:
failed to initialise SAM_ACCOUNT for user may.does this user exist in the unix password database?
failed to modify password entry for may.

---

### Post by huygens on 2006-08-30
Try this post :)
[http://www.ubuntuforums.org/showthread.php?p=1441899#post1441899](http://www.ubuntuforums.org/showthread.php?p=1441899#post1441899)

---

### Post by tarclee on 2006-09-04
i have try the step,but it ask me the username n password when i am in window pc click on ubuntu pc network.what should i put?

---

### Post by huygens on 2006-09-04
The username you have to enter is the username that you would use on the Ubuntu PC to access the share drive you are interested in. As for the password, it is the password you set via the command smbpasswd.
You can set this password just like I explained in this message: [http://www.ubuntuforums.org/showpost...85&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1333185&postcount=2")
There is a paragraph starting with: "Nevertheless, you are still not ready." read and follow subsequent instructions written in this message from that point.
The username you have to use for the smbpasswd command is the same as the one I was mentionning above.

So to resume. Go to your Ubuntu computer, log in (let say that your username is huygens) and open a terminal (Applications->Accessories->Terminal). Finally type the following:
```
sudo smbpasswd -a *huygens*
```
Do not forget to replace huygens by _your_ username.
This command will first prompt you for your user password, so you gain administrator privilege (this is the sudo effect). Then it will prompt you again for another password, this will be the password for your share drive (this is the smbpasswd effect). As this last command is about setting a new password, of course it ask you to re-type your password, just to be sure you do not have a typo mistake. So basically, this command will ask you at maximum 3 passwords.
Once you have done it, just go to your Windows computer, double click on the Ubuntu computer in your network neighbourhood. And when prompt for a username and password enter huygens (or whatever your username is) and the password you have setup above. That's it :-)


I hope this help,

Huygens

---


---
title: "How to autologin to Ubuntu Edgy and NetworkManager"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by noidear on 2006-12-11
How to autologin to Ubuntu Edgy and NetworkManager

Firstly, I have written this because I only use this pc at home and dont care about any local security issues do do with login passwords etc. I am the only person using this pc and am fed up with having to type my username and password, and then another password every time I turn the pc on. If you need your ubuntu setup to remain secure from local tampering then don't use this guide.

I have taken this info from several other threads and put it all together in 1 post because I wanted to help others having similar problems tracking down the various related info, so thanks go to all those who's threads I have used for this, notably 

[http://ubuntuforums.org/showthread.php?t=305278&highlight=autologin](http://ubuntuforums.org/showthread.php?t=305278&highlight=autologin)

and

[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

This how to has 2 parts. The first part is to setup the bypassing of the NetworkManager keyring password. The second part is to setup autologin and still keep from having to enter the keyring password.

PART 1.

1. Download and Install pam-keyring_0.0.8-1_i386.deb from here

[http://ubuntuforums.org/attachment.php?attachmentid=20101&d=1164657897](http://ubuntuforums.org/attachment.php?attachmentid=20101&d=1164657897)

Open terminal and go to directory where the file downloaded to and type

sudo dpkg -i pam-keyring_0.0.8-1_i386.deb

2. Then edit the gdm file by typing in terminal

 sudo gedit /etc/pam.d/gdm

Add the following 4 lines to the end of the contents in that file

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

3. Click save and quit.

NOTE that this only works if the password for the networkmanager keyring applet is the same as your ubuntu login pasword. If your password is different then you will need to do the following.

4. Go to menu and select System - Administration - Keyring Manager

5. Click View - Keyrings and select default keyring. In the right menu there should be a setting called 'Passphrase for wireless network ESSID'

where ESSID is the name of your WPA essid

Delete this by selecting Keyring - Delete

NOTE - I only advise to do this if you only use the keyring manager for networkmanager passwords. I haven't tried this if there are passwords for other applications stored in the keyring manager.

6. Restart Ubuntu and after login for 1 time only a window will popup asking for your wireless network WPA keypassword.  Enter that and after a few moments NetworkManager applet window will appear asking for a password. Again for 1 time only type in the same password as your ubuntu login password.

PART 2.

To setup autologin go to System - Administration - Login Window and select Security tab

1. Do not Enable Automatic Login as there seems to be a bug that Gnome will login before HAL services are fully running and as such things like CDRom, SDCard and other devices aren't properly set or not even running at all. See following link for more details [http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/](http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/)

Instead you need to enable Timed Login, then select your username and set the Pause before login to 5 seconds. This seems to give HAL service just enough time to process what it needs to before Gnome starts up.

Close the Login Window 

2. In order to get around the NetworkManager keyring applet from showing up and requesting your keyring password again, do the following

Create a script file called autologin by typing in terminal

sudo gedit /home/user/autologin

where 'user' is your username home folder

then enter the following lines 

#!/bin/bash
PATH=$PATH:$HOME/bin
echo password | /usr/libexec/pam-keyring-tool -u -s

replace 'password' with your password i.e. the same password as your login password and keyring password

Save and quit

3. Make it executable by typing 

sudo chmod 755 /home/user/autologin

and make sure the file is set to your user and group. Type

sudo chown user /home/user/autologin 

and 

sudo chgrp user /home/user/autologin

4. Go to System - Preferences - Sessions

select Startup Programs tab

select Add

then browse to the autologin script you just made and add it.

Close.

5. Restart Ubuntu and if all has gone well Ubuntu will login with just a few seconds of delay, but quicker than typing in all those passwords

I hope this helps any out there who have had similar probs and if I have got anything wrong please let me know.

Thanks again to all those whose info I have used in making this how to.

---

### Post by .Dani on 2007-01-22
Thank you :) It works flawlessly on Xubuntu 6.10, as far as bypassing entering the keyring password is concerned. I'm fine with manually logging in but that keyring box was annoying. I read [ here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager) that this issue should be resolved in future releases of the Network Manager package. Till then, thanks a lot for finding this out using pam.

---

### Post by nzruss on 2007-02-18
Originally I followed all the instructions but still got asked for the keyring password.  (The first reboot I got asked for a new keyring password which I set to the same as the login password)

For some reason, the changes to my >preferences>session>startup tab were not being retained across logins. ....

I was able to fix this with 

```
 sudo chown [COLOR="Orange"]<my_user_name>[/COLOR] ~/.config 
```

Now my system boots into the user, then does not ask for the keyring password. 

(IMHO its allot of work for something quite trivial.)

---

### Post by Per Olav on 2007-04-06
Works like a charm on Ubuntu 6.10.. Thank you!

---

### Post by KrazyPenguin on 2007-04-07
Pain to get this working in Fiesty.

Had to change:#!/bin/bash
PATH=$PATH:$HOME/bin
echo password | /usr/libexec/pam-keyring-tool -u -s

to

#!/bin/bash
PATH=$PATH:$HOME/bin
echo password | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and now works like a charm 8) 

The timed login cannot be set to 5 seconds, the lowest it would go is 10 seconds.
Is there a file I can edit to lower it down to 5 seconds??

---

### Post by ewg on 2007-04-08
Thanks for the post/how to. It works fine for me in Ubuntu 6.10

EWG

---

### Post by Avraham on 2007-04-25
it didnt work for me in feisty..  any ideas?
Thanks

---

### Post by eldersoares on 2007-08-04
how to autologin to Knetworkmanager?????????
thanks

---

### Post by goughs on 2008-03-12
I attempted to get this going in gutsy (AMD64), it didnt work, so I ran the script in the terminal and got: 

/home/user/libpam-keyring/pam-keyring-tool: error while loading shared libraries: libgnome-keyring.so.0: cannot open shared object file: No such file or directory

Can anyone give me any assistance?

 libgnome-keyring.so.0 is present in /usr/lib, it seems that the script can't find it, or more likely is looking in the wrong place for it.

---


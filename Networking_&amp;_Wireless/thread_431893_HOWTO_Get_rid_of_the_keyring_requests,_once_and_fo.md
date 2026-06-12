---
title: "HOWTO: Get rid of the keyring requests, once and for all, for permanent!"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by jonlatane on 2007-05-03
Okay, I've seen lots of guides about using PAM Keyring to make nm-applet (and other keyring programs) stop asking for your password all the time.  However, all of them have their problems (especially with suspend/resume) so I'd like to share my solution with everybody.  This fixes the problem with suspend/resume AND makes allows you to use PAM-keyring even if you don't have the same keyring and user passwords.

**NOTE:** This method, from what I understand, is not considered as secure as many others.  It involves keeping your user and keyring passwords in plain text files.  Technically, someone else can get your passwords from this if they have access to your computer (say you leave your desk, someone comes over, knows where the hidden file is, opens it, and gets your password).  However, this is honestly just a hack for convenience.  You shouldn't use this if you're really deeply concerned about your data.

[LIST=1]
[*]**Install PAM Keyring package**
Simply do:
```
sudo aptitude install libpam-keyring
```
[*]**Unlock Keyring when you login**
Here we will create a script that will unlock your keyring as soon as you log in.  In a terminal, do:
```
mkdir ~/.bin
gedit ~/.bin/pam-keyring-unlock.sh
```
You may pick a different file if you want, but I'd recommend preceding something with a "." so the file or its containing directory will be hidden.
In this file, copy and paste this:
```
#!/bin/bash
echo <PASSWORD> | /usr/lib/libpam-keyring/pam-keyring-tool --unlock --keyring=default -s
```
And replace <PASSWORD> with your default keyring password.  Now run this to make it executable:
```
chmod a+x ~/.bin/pam-keyring-unlock.sh
```
After that, just go to System->Preferences->Sessions.  In the "Startup Programs" tab (the default one) click "New."  In the dialog, enter "PAM Keyring Configuration" for the name and /home/<USERNAME>/.bin/pam-keyring-unlock.sh for the command, replacing <USERNAME> with your username.
[*]**Unlock keyring when you resume**
This step is optional, but really really useful for laptop owners and even easier than the last.  Execute:
```
sudo gedit /etc/acpi/resume.d/99-pam-keyring-unlock.sh
```
In the text editing window that appears, copy and paste this:
```
#!/bin/bash
echo <USERPASSWORD> | sudo -u <USERNAME> -S echo <KEYRINGPASSWORD> | /usr/lib/libpam-keyring/pam-keyring-tool --unlock --keyring=default -s
```
And replace <USERPASSWORD> with the password you use to login, <USERNAME> with your username, and <KEYRINGPASSWORD> with your keyring password.  Then do:
```
sudo chmod a+x /etc/acpi/resume.d/99-pam-keyring-unlock.sh
```
You should never be asked for a keyring password after resume again!
[/LIST]
Hope this works for everyone, and I didn't forget anything.  I can confirm that it works flawlessly on my Thinkpad T43.  Please, reply with any feedback or thoughts or things I missed or any other problems.

---

### Post by MonkeyWrench32 on 2007-05-04
It worked perfectly on my VAIO!  Thanks!

---

### Post by jakev383 on 2007-05-05
On 6.10 (Edgy) I don't have libpam-keyring in my repos.... What repos do you have enabled to get this?

---

### Post by SamuelDr on 2007-05-06
Would it work if you changed the owner and groups from the .sh file you created and remove read+write from everyone, but keep execute from everyone? Would executing it as another user work?

Example:
you create pam-keyring-unlock.sh and put what is needed into, then:
```
sudo chown root:root pam-keyring-unlock.sh # could also change it to nobody
sudo chmod a-rw pam-keyring-unlock.sh # not sure if it is the proper way to do it
```

Would it make it a little bit more secure, at least, the only way I see that you could read it is to reboot the machine under another OS which would not care for the ACL, like windows with ext3 driver.

---

### Post by jakev383 on 2007-05-06
> **SamuelDr said:**
> Would it work if you changed the owner and groups from the .sh file you created and remove read+write from everyone, but keep execute from everyone? Would executing it as another user work?

Example:
you create pam-keyring-unlock.sh and put what is needed into, then:
```
sudo chown root:root pam-keyring-unlock.sh # could also change it to nobody
sudo chmod a-rw pam-keyring-unlock.sh # not sure if it is the proper way to do it
```

Would it make it a little bit more secure, at least, the only way I see that you could read it is to reboot the machine under another OS which would not care for the ACL, like windows with ext3 driver.

Was that in response to me? I can't get libpam-keyring. It's not in the repos I have enabled, so I was asking which repos the author had or what repo it was in.
Thanks.

EDIT: Looking around, this looks like it only works for fiesty - I'm running edgy so I'll look around for this package and post back if I find it.

---

### Post by pohlipit on 2007-05-09
Can't you just un-install the keyring software somehow?

Cheers, 
P!

---

### Post by flintflake on 2007-05-17
When i try to copy/paste the info into the editor and save the .bin file, i get an error that reads:


Cannot save file
Unexpected error: file not found.

In the terminal window, I get this:
** (gedit:5997): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

What does this mean?

---

### Post by buffer on 2007-05-24
thanks for a method that works with Auto-login. 

Buffer
Ubuntu newbie

---

### Post by JBA2337 on 2008-04-16
To: jonlatane, or anybody!

I tried your method as described in your post, "HOWTO: Get rid of the keyring requests, including after suspend/resume and more". 

It did not work for me.

I noticed that when I installed libpam-keyring, I got the following results.

sudo aptitude install libpam-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

The above says "No Packages will be installed". I seearched for libpam-keyring, using the file search tool, and it found nothing on  my computer.

Everything else that you recommended seemed to work OK. But it appears that I did not install libpam-keyring.

Any other ideas?

I am tired of entering my keyring password every time I boot.

Thanks.

JBA2337

---

### Post by phil_elson on 2008-05-09
JBA2337 that normally means it is already installed.

Thanks for this...It was getting a real pain to have to enter my password all the time! 

I can confirm that it is working on Ubuntu 8.04

I had to change the code quite a bit for users using libpam-gnome-keyring instead of libpam-keyring.

My solution reaquires that you download the bin attached to this post: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247/comments/16](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247/comments/16)

put this in your ~/.bin/ folder and change the command in your pam-keyring-unlock to
```
echo <password> | /home/<username>/.bin/pam-keyring-tool --unlock --keyring=default -s
```

---


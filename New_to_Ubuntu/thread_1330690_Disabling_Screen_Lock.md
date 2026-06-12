---
title: "Disabling Screen Lock"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by zaivala on 2009-11-18
I posted this previously with a misspelling in the header, and got no replies...

I have my netbook set to automatically log me in at bootup... and it still asks for my password. (Unlike prior versions of Ubuntu, 9.10 does not allow you to install it withut a password, probably a good thing, but...) And every time I time out or shut off my screen, it requires a password all over again. 

I had this disabled on my desktop in 9.04 and earlier (not Netbook Remix) but can't find the location to do it in 9.10 UNR.

Any ideas?

---

### Post by nathan726 on 2009-11-18
Open a terminal (Applications->Accessories->Terminal) and run:```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```

---

### Post by zaivala on 2009-11-19
> **nathan726 said:**
> Open a terminal (Applications->Accessories->Terminal) and run:```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```

Thanks, hope that worked.  The first time was typo-filled and of course the command was not recognized... but on the subsequent tries, no message returned (which also means no error message).  I will now test it...

I hit the key to blank the screen.  It blanked.  I then hit the key to turn the screen back on (if you know Eees, you know there is a special key for this, top left).  It asked for a password.  Is there another command I need to enter?

Moss

---

### Post by nathan726 on 2009-11-19
If you want to automatically login, go to System -> Administration -> Login Screen.
Unlock the application and set it to "Log in automatically".

---

### Post by zaivala on 2009-11-19
> **nathan726 said:**
> If you want to automatically login, go to System -> Administration -> Login Screen.
Unlock the application and set it to "Log in automatically".

I've done that already, but I'll go check it again...

Yup, it says that, but it's not working like that.  Any chance Netbook Remix works differently than vanilla Ubuntu?  Works fine on my desktop.

Moss

---

### Post by nathan726 on 2009-11-19
It's odd that it doesn't work on UNR.

---

### Post by zaivala on 2009-11-19
Would this be considered a reportable bug?

---

### Post by nathan726 on 2009-11-19
I just found this: [http://www.ubuntuforums.org/showthread.php?p=8305378](http://www.ubuntuforums.org/showthread.php?p=8305378)
> Go to System>Administration>Users and Groups
Here you can select your username and click on properties.
Then there is a box to check that says > Don't ask for password on login

---

### Post by zaivala on 2009-11-19
> **nathan726 said:**
> I just found this: [http://www.ubuntuforums.org/showthread.php?p=8305378](http://www.ubuntuforums.org/showthread.php?p=8305378)

Rebooting to try that...  

Nice try, but no cigar.  I go to my User account on that screen, and the checkbox to click "Don't ask for password on login" is ghosted.

Moss

---

### Post by zaivala on 2009-11-19
I tried again after clicking a box at the bottom, "Click to Make Changes"... still no go, still ghosted.

---

### Post by nathan726 on 2009-11-19
It appears to be a bug: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396459](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396459)

I'll try and help you fix it...

Open a terminal and run:
```
cat /etc/pam.d/gdm
``` And post the results.

---

### Post by zaivala on 2009-11-19
Thanks.

zaivala@Whiteee:~$ sudo cat /etc/pam.d/gdm
[sudo] password for zaivala: 
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
zaivala@Whiteee:~$

---

### Post by nathan726 on 2009-11-19
Add a line (highlighted in red) to /etc/pam.d/gdm so that it looks like this:
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
[COLOR=Red]auth sufficient pam_listfile.so item=user sense=allow file=/etc/gdm/nopassusers.txt onerr=fail[/COLOR]
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
```And then run this code:
```
sudo echo $USER >> /etc/gdm/nopassusers.txt
```And then hopefully it will work [-o<

---

### Post by zaivala on 2009-11-22
OK, my PAM listing was the result of running a request... I have no clue whatsoever on how to add a line to a result, or what that would change.  Please inform.

---

### Post by nathan726 on 2009-11-23
You can open the PAM file by running this in the terminal:

```

sudo gedit /etc/pam.d/gdm

```Then you just follow the instructions from my earlier post and restart your pc.
It should enable you start your pc without being asked for a password.

---

### Post by zaivala on 2009-11-23
Using gedit as suggested in Msg #15, I edited the pam.d file as suggested in Msg #13.  I saved and exited gedit. (You didn't say to do this, but perhaps I'm not a total idiot).

I then ran the echo "nopassusers.txt" command as stated in #13... and got "Permission denied".  I entered the command verbatim, using cut and paste.  

Dumb questions:  The echo command did not reference the pam.d directory... should it have?  Should I have rebooted prior to running the second command?  Should I have substitutesd something for $USER?  What am I doing wrong?

Moss

---

### Post by zaivala on 2009-11-25
OK, the dumb questions have not been answered.  Anyone wanna tell me what I'm doing wrong, or what I have to do to do it right (preferred)?

---

### Post by nathan726 on 2009-11-29
You need to include the "sudo" command to give you permission:
```
sudo echo $USER >> /etc/gdm/nopassusers.txt
```Then restart your pc.

---

### Post by zaivala on 2009-11-29
> **nathan726 said:**
> You need to include the "sudo" command to give you permission:
```
sudo echo $USER >> /etc/gdm/nopassusers.txt
```Then restart your pc.

As I said, I used cut-and-paste, which included the sudo command.  Just to make sure I wasn't that stupid, I just tried it again.

zaivala@whiteee:~$ sudo echo $USER >> /etc/gdm/nopassusers.txt
bash: /etc/.gdm/nopassusers.txt: Permission denied
zaivala@whiteee:~$

The gdm file edited in the earlier example was at /etc/pam.d/gdm/nopassusers.txt; in the later suggestion, there was no /pam.d/ included.  Because I'm stoopid, I tried it WITH the /pam.d/ included... this time I got:

bash: /etc/pam.d/gdm/nopassusers.txt: Not a directory

So there is SOMETHING wrong here, and I don't know what it is, but the commands suggested, entered verbatim, do not work.

---

### Post by nathan726 on 2009-11-30
Hmm... I just tried the same command and I also get permission denied! :-k

Instead you can to do this - run this command:
```
sudo gedit /etc/gdm/nopassusers.txt
```Then type your username.
Save the file and reboot.

---

### Post by zaivala on 2009-11-30
Well, that command worked... I just typed in my username into the file and and saved it, then rebooted...

...and it's still requiring my password.  So whatever was accomplished, was not what we were trying to accomplish.

---

### Post by wbrogan on 2010-09-28
In screensaver preferences, just disable the screenlock checkbox.  I was struggling with that too.

---


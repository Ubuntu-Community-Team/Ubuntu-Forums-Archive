---
title: "Wireless / Keyring / Pam-Keyring and automatic login"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Markus72 on 2006-12-17
(Edgy)

Hi,

I installed gnome-network-manager and was able to access my WPA protected wlan. Fine.

Then, after every login, I've been asked to enter the keyring password in order to let gnm find the reviously given WPA passphrase. Not fine.

Then I found that pam-keyring thing, compiled and installed it and - wow no boring keyring window after logging in. Fine.

Since it's my HTPC I want the user to be logged in automatically. So I switched to automatic login. Due to that, I do not provide the logon password... and now the keyring manager prompts again for the password ... ARGH!

Any ideas how to fix it?

Thx
Markus

---

### Post by hornett on 2006-12-31
Go to System>Preference>Sessions

Make sure nm-applet is set **NOT** to start up automatically.

Log out and back in and ensure that it actually does not spawn itself (make sure it is disabled on every panel of the Sessions window).

Then, make a script containing the following:

```
#!/bin/bash
#launch useful stuff for gnome...

#first unlock the default keyring...
echo <YOUR_KEYRING_PASSWORD_HERE> | /usr/libexec/pam-keyring-tool -u -s

#then run nm-applet in the background...
nm-applet &

```

Right click it in Nautilus, and make sure it is executable. Then open the Sessions window again, and add your script to the Startup Programs tab.

Now, this is very insecure, since your keyring password is stored in plain text, but that doesn't matter to me since I use autologin and various other dubious things on this machine anyway.

When you next log in, the script will unlock the keyring with the password set in the script, then run nm-applet - no more entering your password repeatedly (3 times in my case!).

I'm not sure who told me about the pam-keyring-tool magic, so I don't want to take any credit. Thanks to whoever figured that gem out.

Hope to help!

Andy

---

### Post by pikespeakhiker on 2007-04-19
For Feisty the location of pam-keyring-tool has changed (at least on my installation).  The equivalent line in my shell script is:

```
echo <KEYRING-PASSWORD> | /usr/lib/libpam-keyring/pam-keyring-tool -u -s
```

Thanks to everyone who has helped me solve my automatic wireless network connection with automatic login!

---

### Post by jtsai256 on 2007-04-20
I would just like to reiterate that this method worked for me. If you have Feisty, be sure to follow the message above by pikespeakhiker.

Thanks! This was one of the most annoying issues I had with Ubuntu.

---

### Post by Scipio_Publius on 2007-04-27
I would be cool with just having the password I think for the default keyring

---

### Post by wmiddsr on 2007-07-08
I am a very, very newbie.

I recently d/l 'ed and installed  Fiesty Fawn desktop 7.04 and while enjoying the experience,
am not always able to understand the documentation or posts in ubuntu forums.

I am successfully connecting to internet wirelessly from my ubuntu Toshiba laptop.
I am unsuccessfully supplying password for the key-ring pop up thing, and end up
selecting deny, just to move on. After that I can connect wirelessly by providing
the WPA code, for some kind of setup form/dialog.

My questions:

   Why isn't the keyring thing taking my password -  I didn't forget it or mistype it.

   I am on a personal/1 user machine with login accounts for myself (wmiddsr), and guest
   and a root account which I havent needed to use yet.  I would like all 3 accounts
   to get the wireless connection automatically. Not sure how?

I would try the live help with Gaim - but don't know how yet (but will undoubdtedly learn soon.


   Finally ... WPA supplicant 
              Do I have it already?
              What is it for - I didnt understand what I read about it.

Thanks for any help you can give.

PS Also whats the best way to know when new posts appear here so I can come
     back and see them

---

### Post by DC@DR on 2007-07-09
For keeping track of the posts, you could subscribe to the thread you want to follow using the Thread Tools at the beginning of every threads....
About your wireless problem, I think you just need to pickup a password for the Gnome keyrings which in turn will hold the wireless password for you, so next time you won't have to bother entering the wireless pass again. Search the 4rums about "pam-keyring" and you will find out how to get the Gnome keyrings pass filled in automatically when signing in ...Keep searching here, I'm sure your problem has been solved somewhere in these forums. G'luck :-)

---

### Post by Balachmar on 2008-05-22
Hi,

I want my wifi connection to be opened at startup without entering the password. Because it is a htpc box.
And I used libpam-keyring for this.
However I cannot find that package in hardy anymore.
What should I use to do this, or how do I get this package?

---

### Post by taqkavar on 2008-05-24
To get rid of the keyring prompt after automatic login in hardy 8.04 you can: 

System > Preferences > Encryption and Keyrings 
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

Related bug report (kinda) : [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/108993](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/108993)

I have also followed the part of this tutorial where you edit the etc/pam.d/gdm file. not sure if this has to do anything with it, too lazy to revert the changes and reboot to find out.
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by Sleaka J on 2008-05-25
I can confirm that changing the keyring password to a blank password removes the popup upon startup where it asks for the password for the default keyring for nm-applet when you've setup an automatic logon.

---

### Post by amartz on 2008-05-29
System > Preferences > Encryption and Keyrings 
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.


Thank you! This worked perfectly!  I've been looking for this for quite some time.
Art

---

### Post by Patch Adams on 2008-06-01
How would I do this in Xubuntu 8.04. there is no system>preferences>encryption menu. I can log in automatically but I get asked for a wpa password then a keyring password.

thanks

---

### Post by SubGothius on 2008-07-12
> **Patch Adams said:**
> How would I do this in Xubuntu 8.04. there is no system>preferences>encryption menu.```
sudo aptitude update && sudo aptitude install seahorse
```That'll install a keyring encryption app and put its icon in your Applications > Settings menu. ;)

---

### Post by elgranjeff on 2008-07-16
> **SubGothius said:**
> ```
sudo aptitude update && sudo aptitude install seahorse
```That'll install a keyring encryption app and put its icon in your Applications > Settings menu. ;)

Thank you!  I've been dealing with this for a while, but have not put up enough effort to find a simple post like this one :P

---

### Post by quantumottle on 2008-07-22
This also worked for me, thank you. I must admit, it seems moronic to leave your passwords unencrypted, but after weeks of dead ends searching for other options I suppose we have little choice. Thank you for the workaround.

---


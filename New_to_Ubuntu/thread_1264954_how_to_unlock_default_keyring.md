---
title: "how to unlock default keyring"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-09-12
every time I log on I get a popup that says that the network manager applet wants access to the default key ring but is being blocked, this is preventing me from getting on the internet.
 
What password I'm I supposed to enter? I've tried both the WEP key and my root password, but neither work.

---

### Post by Commisar Jimp on 2009-09-12
Could I get some help with this? It'd be really nice to use the internet.

---

### Post by 3rdalbum on 2009-09-12
Your ordinary user password will unlock your user keyring.

---

### Post by kerry_s on 2009-09-13
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by mcduck on 2009-09-13
> **kerry_s said:**
> [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

That tutorial is outdated, and completely pointless when it comes to latest Ubuntu releases. Ubuntu already unlocks the keyring automatically if you use normal login (with a login pasword).

Still, there are couple of things to know:

The keyring password is set to same as login password, but if you change the login password at later time you need to change keyring password manually.

If you use automatic login, the keyring won't be unlocked automatically and therefore first time some program tries to use it you'll be prompted to type the password to unlock it. If you don't like to do that, you have to either enable the normal login again, or remove password from your keyring. Removing the keyring password is less secure, but if you are using automatic login you probably aren't too worried about security anyway.

Here's how to remove the keyring password:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

edit: If you are using 9.04 (or later), the setting is in different place. It's immediately in the main window, in the Passwords-tab, so no need to go to Edit/Preferences.. :)

---

### Post by Commisar Jimp on 2009-09-13
I went to the keyrings manager, and edit > preferences didn't have a passwords tab, but the main manager window tab did, so I opened it and it had passwords:login. I right clicked on it, the menu had both "unlock" and "change password" and I clicked both, but neither one did anything, is there a way to do it through the terminal?

---

### Post by Commisar Jimp on 2009-09-13
OK an update, I hit deny in the popup box asking for the password until it went away, then entered

nm-applet

In the terminal. At first it tried to get me to change the password in the password:login key, but when I don't know what that was, so I hit deny again, eventually I read

** (nm-applet:6612): DEBUG: applet_common_device_state_changed
** (nm-applet:6612): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:6612): DEBUG: applet_common_device_state_changed
** (nm-applet:6612): DEBUG: foo_client_state_changed_cb
** (nm-applet:6612): DEBUG: applet_common_device_state_changed
** (nm-applet:6612): DEBUG: applet_common_device_state_changed
** (nm-applet:6612): DEBUG: foo_client_state_changed_cb
 
and then my internet started working again, but now I've got to keep the terminal running all the time or my internet freeezes again

---

### Post by kerry_s on 2009-09-13
i think you should just start over.
right click nm-applet-> edit connections
select the wireless tab
click on the wireless name & delete it

that should set you back to scratch were you can enter your wep key & leave the key manager blank when it asks.

---

### Post by steelmachine on 2009-09-17
McDucks solution worked for me, but step 2 was a bit confusing. You just open the "Passwords and encryption keys"-manager like stated in step 1, then just click the tab named Password, then right click the "password" entry and choose "Change password". Enter your password and leave the "new password"-field blank. Save and restart computer to test. Wifi should now open it self without nagging about the password.

---

### Post by markusf21 on 2009-09-20
worked like a charm

Maybe I am missing something, but having to do this seems pointless to me. If I have auto login then obviously I am not concerned with physical security, I wonder if it would be possible to make the keyring blank by default if auto login is enabled during the install.

---

### Post by TopicMapper333 on 2009-10-01
> **kerry_s said:**
> [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

The advice given here doesn't work under 9.04.  It advises the installation of libpam-keyring, but there is no such package available for the distro.

---

### Post by TopicMapper333 on 2009-10-01
> **kerry_s said:**
> [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

As I already noted, this suggests the installation of a package that's nonexistent in 9.04, despite the fact that the title shown on the page says "Jaunty".  Editing /etc/pam.d/gdm as suggested by the article had no discernible effect, either.

> 
edit: If you are using 9.04 (or later), the setting is in different place. It's immediately in the main window, in the Passwords-tab, so no need to go to Edit/Preferences.. :)

Either I'm misreading this, or the advice it gives is for changing a WPA/WPA2 password, rather than for waiving the requirement that nm-applet asks for my password in order to access my default keyring.  By leaving the password field blank as the above quote suggests, all I accomplished was to require myself to re-enter my router's WPA password when NetworkManager (nm-applet) attempted to connect to the wireless router.  I'm still being required to re-enter my password every time I re-boot and log in (automatically), in order to gain wireless service.

I've read everything I can find about this problem.  It comes up in several threads in several fora.  Several people have complained about being nagged for passwords in exactly the same way.  Several have claimed that the problem can be fixed, but none of the answers they say have worked for them -- and that I have found -- appears to work under the 9.04 distro that I'm running.  What's the right answer -- the one that, unlike all of the ones I have found, actually works under 9.04?  

It seems to me that it would be logically consistent to make this an authorization option that can be set to "Yes" under System->Administration->Authorizations.  But I don't see it there.  Is it?

---

### Post by LukonLinux on 2009-10-07
Warning: I'm a Linux/Ubuntu Newbie

I had the same issue, and I think I have solved the problem - maybe this will help.

After you follow the directions in this thread for eliminating the keyring password, you will be asked for the WEP/WPA key, when you login next.  Go ahead and enter this -THEN, you will be asked to enter a keyring password to save stored passwords.  Leave this one blank, and when it prompts, tell it to go ahead and use unsecure keyring.  Mine has stopped nagging me, since I did this.  Of course all stored passwords are accessible to anyone who gets their hands on my laptop now...

Hope this helps...

:)

---


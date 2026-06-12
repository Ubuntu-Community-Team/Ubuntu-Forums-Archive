---
title: "upgraded from 9.04 to 9.10 and now It asks for Keyring password on everystartup"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-29
Hi
I have a wireless network connection and on every startup Karmic is asking for password. is there any way to make it not to ask the password and instead use an stored password or something? just like 9.04 which was not asking for passwords on every startup.


Content of the /home/legolas/.gnome2/keyrings is two files named default and login.keyring. inside the default file there is one word: login and nothing else.


I had this thread at: [http://ubuntuforums.org/showthread.php?t=1287801](http://ubuntuforums.org/showthread.php?t=1287801) but now it is closed. I thought I look for a solution here.
Thanks.

---

### Post by Ijtaba on 2009-10-29
Im guessing your network card is already configured...

Why not try a script like this guy did? I have no idea how it works, but could be helpful..

```
mapping wlan0

        script /path/to/wlan-scan.sh
        # Accesspoint,"ESSID",Encryption,Mode,Channel
        map 00:FE:FE:FE:00:00,"MY_NET",*,*,* wlan0-home
        map *,"COMPANY",on,Master,*          wlan0-office
        map *,*,off,Master,*                 wlan0-open

iface wlan0-home inet dhcp
        wireless-essid HOMENET
        wireless-mode managed
        wireless-enc FEFEFEFEFEFE

iface wlan0-office inet dhcp
        wireless-essid COMPANY
        wireless-mode managed
        wireless-enc s:Secret_password

# This is a fallback, selected for all unencrypted WLANs
iface wlan0-open inet dhcp
        wireless-essid ANY
        wireless-mode managed
```

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

under the automated wlan script

---

### Post by anewguy on 2009-10-29
A little clarification needed:

(1) is this at boot time, or at least the first time you try to connect to the net after a boot?

(2) does it ask for keyring password or is network manager asking for the network password?  For the first, I think it says something like enter password to unlock keyring or some such thing - it's been a LONG time.

If it's asking for the keyring password, then you probably need to reset it first.  I know it's on one of the menus, but I'm not running gnome right now (I'm playing around with KDE) so I'm not sure where it's at.

Normally, after an install, the first time that it asks for the keyring password you need to enter your default log in password, otherwise it will ask for it every time.

Dave :)

---

### Post by legolas_w on 2009-10-30
Hi
It asks for the password when I boot the computer and the network connection wants to establish.

The windows says that nm-applet wants to access the keyring and I should provide the password for it to get opened (I will type the exact message on next reboot)

If i disconnect the network and reconnect it will NOT ask for the password :).

Please let me know how to reset the password to fix the problem.


Thanks

---

### Post by anewguy on 2009-10-30
Okay, it's the keyring password then.   I'm pasting in the instructions from another thread to help you out:

 

 Re: how to unlock default keyring
Quote:
Originally Posted by kerry_s View Post
[http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/](http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/)
That tutorial is outdated, and completely pointless when it comes to latest Ubuntu releases. Ubuntu already unlocks the keyring automatically if you use normal login (with a login pasword).

Still, there are couple of things to know:

The keyring password is set to same as login password, but if you change the login password at later time you need to change keyring password manually.

If you use automatic login, the keyring won't be unlocked automatically and therefore first time some program tries to use it you'll be prompted to type the password to unlock it. If you don't like to do that, you have to either enable the normal login again, or remove password from your keyring. Removing the keyring password is less secure, but if you are using automatic login you probably aren't too worried about security anyway.

Here's how to remove the keyring password:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

edit: If you are using 9.04 (or later), the setting is in different place. It's immediately in the main window, in the Passwords-tab, so no need to go to Edit/Preferences..
__________________

That should do it - let us know if you need help, or if it works out for you!

Dave :)

---

### Post by Peter09 on 2009-10-30
If it is just for the network connection then go to the network icon, right click and select the appropriate network and then the edit tab. Tick the box that says 'available to all users' (or words to that effect). It will not then ask for a password to connect.

---

### Post by DedMoroz on 2009-10-30
> **anewguy said:**
> Okay, it's the keyring password then.   I'm pasting in the instructions from another thread to help you out:

 

 Re: how to unlock default keyring
Quote:
Originally Posted by kerry_s View Post
[http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/](http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/)
That tutorial is outdated, and completely pointless when it comes to latest Ubuntu releases. Ubuntu already unlocks the keyring automatically if you use normal login (with a login pasword).

Still, there are couple of things to know:

The keyring password is set to same as login password, but if you change the login password at later time you need to change keyring password manually.

If you use automatic login, the keyring won't be unlocked automatically and therefore first time some program tries to use it you'll be prompted to type the password to unlock it. If you don't like to do that, you have to either enable the normal login again, or remove password from your keyring. Removing the keyring password is less secure, but if you are using automatic login you probably aren't too worried about security anyway.

Here's how to remove the keyring password:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

edit: If you are using 9.04 (or later), the setting is in different place. It's immediately in the main window, in the Passwords-tab, so no need to go to Edit/Preferences..
__________________

That should do it - let us know if you need help, or if it works out for you!

Dave :)

That didnt work for me. Im having the same problem accessing UbuntuOne. Its trying to access the default keyring, but entering my password doesnt work. I even changed my login password via  your tips and still nothing. Hmm. Any other ideas? :) Thanks.

---

### Post by anewguy on 2009-10-30
You could try just deleting the keyring file altogether and then it would start from scratch, at which time just enter in your login password.  However, if the steps of clearing/resetting the keyring password didn't work, I'm not sure it would either.  You may want to do a web search on linux pam keyring password and see if any of the threads has anything that sounds like your problem.

Sorry I couldn't have been of more help!

Dave :)

---

### Post by legolas_w on 2009-11-03
I resolved the wireless connection password by checking the mentioned checkbox. 

Now I should say that this problem persist, for example when I open Empathy it asks for the keyring password again.

If this statement does not give you more details about my problem I will completely purge the keyring and install it again to see what will happen.

btw, what will I lose if I purge keyring and install it again?

Thanks.

---

### Post by bruno.braga on 2009-11-05
> **legolas_w said:**
> 
btw, what will I lose if I purge keyring and install it again?


You will just need to type again the passwords stored on the current keyring. It is not big deal, unless you forgot some passwords that are already stored there.

To delete: rm ~/.gnome2/keyrings/{your keyring}
or you can do from the GUI, as described on other posts here.

---


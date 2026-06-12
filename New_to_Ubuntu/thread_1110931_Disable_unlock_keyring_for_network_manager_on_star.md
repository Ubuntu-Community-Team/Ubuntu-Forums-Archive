---
title: "Disable unlock keyring for network manager on startup"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-30
Hi there,

I have set up a guest computer for our Bed and Breakfast running Ubuntu 8.10. The computer has two accounts, Administrator and Guest. It is set up so that Guest has no admin privileges, and will automatically log in when the computer is started. The user (person who is staying at our B&B) will be always changing and it would be inconvenient to tell them the password to login.

Unfortunately, when the computer starts I get this message:

> 
Unlock keyring

Enter password for default keyring to unlock

The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked


How can I allow the network manager applet to startup without having to enter in the password? Or can I add nm-applet to the default keyring somehow as trusted application?

Thankyou

---

### Post by lovinglinux on 2009-03-30
Unfortunately, this is a known problem related to automatic login.

I deleted the default keyring and created a new one without password. I still get the warning, but I ignore and close it. It will access the network anyway.

---

### Post by marshall.robert on 2009-03-30
The only way I got around this was to create a new user account (deleting the old one is optional, but recommended if you wish to keep the same username) and make sure I set everything up for automatic login then provide and empty keyring password when it first asks for one.

If you wish me to explain this in depth then just say.

---

### Post by diablo75 on 2009-03-30
Try this:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by mcduck on 2009-03-30
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by Craven Maven on 2009-06-11
McDuck, I tried to follow your instructions, in Jaunty Jackalope, but I can only get so far. In Preferences, I can't see any tab marked Password Keyrings. There are two marked Key Servers and Key Sharing, though. But nothing anywhere marked password, login or unlock

CM

---

### Post by mcduck on 2009-06-11
> **Craven Maven said:**
> McDuck, I tried to follow your instructions, in Jaunty Jackalope, but I can only get so far. In Preferences, I can't see any tab marked Password Keyrings. There are two marked Key Servers and Key Sharing, though. But nothing anywhere marked password, login or unlock

CM
The user interface for Seahorse ("Passwords and Encryption Keys", as it's listed in the menu) is slightly different than it was in previous versions.

In 9.04 you don't need to go to preferences, instead move to the Passwords-tab of the main program window, right-click the "Passwords:login"-keyring and select "Change Password" from the right-click menu.

---

### Post by benow on 2009-06-17
To get passwordless networkmanager login working with 9.04, I had to do something slightly different.
[LIST=1]
[*]Applications->Accessories->Passwords and Encryption Keys
[*]Select Passwords tab
[*]Right click on Passwords: login, choose Change Password
[*]Enter current password and *leave the new and confirm fields blank*
[/LIST]

---

### Post by n.hinton on 2009-07-31
> **benow said:**
> To get passwordless networkmanager login working with 9.04, I had to do something slightly different.
[LIST=1]
[*]Applications->Accessories->Passwords and Encryption Keys
[*]Select Passwords tab
[*]Right click on Passwords: login, choose Change Password
[*]Enter current password and *leave the new and confirm fields blank*
[/LIST]

is this wise, the following dialog is:

Store passwords unencrypted?

By choosing to use a blank password, your stored passwords will not be safely encrypted. They will be accessible by anyone with access to your files.

And I'm guessing here but won't that include your wireless encryption key!

---

### Post by n.hinton on 2009-08-01
[http://ubuntuforums.org/showthread.php?t=1228374&highlight=password+default+keyring](http://ubuntuforums.org/showthread.php?t=1228374&highlight=password+default+keyring)

---

### Post by W4l0ck on 2009-08-01
Set it to cache your password.

---

### Post by ricojonah on 2009-10-22
I could be mistaken, but setting your keyring to a blank password could leave your system ready-and-willing to give all of your actual passwords to anyone (roommate, family, friends) who has physical access to your system. All they'd have to do is power up your system and have a minimal knowledge of what they're doing.

This may be a better solution for anyone experiencing this problem--it worked for me in both Jaunty and Karmic:


1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This will allow any user account on your system to access the wireless network. If you're the only user on your system (or, as in my case, you *prefer* not having to type in your wireless net's password for every family member), then this may be a much more secure, equally simple approach. I hope this helps somebody else!

---

### Post by mcduck on 2009-10-22
> **ricojonah said:**
> I could be mistaken, but setting your keyring to a blank password could leave your system ready-and-willing to give all of your actual passwords to anyone (roommate, family, friends) who has physical access to your system. All they'd have to do is power up your system and have a minimal knowledge of what they're doing.

This may be a better solution for anyone experiencing this problem--it worked for me in both Jaunty and Karmic:


1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This will allow any user account on your system to access the wireless network. If you're the only user on your system (or, as in my case, you *prefer* not having to type in your wireless net's password for every family member), then this may be a much more secure, equally simple approach. I hope this helps somebody else!

True, but on the other hand removing the keyring password is only necessary when using automatic login, which already leaves not only your passwords but also *all your files* vulnerable to other people who have access to the same computer.

So based on that the people who might need to remove keyring password are not really that worried about their security anyway. :)

(If you use normal login with a password then there's be no need to remove the keyring password, as the keyring will get unlocked automatically at login time.)

---

### Post by gemisi on 2010-01-29
> **ricojonah said:**
> I could be mistaken, but setting your keyring to a blank password could leave your system ready-and-willing to give all of your actual passwords to anyone (roommate, family, friends) who has physical access to your system. All they'd have to do is power up your system and have a minimal knowledge of what they're doing.

This may be a better solution for anyone experiencing this problem--it worked for me in both Jaunty and Karmic:


1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This will allow any user account on your system to access the wireless network. If you're the only user on your system (or, as in my case, you *prefer* not having to type in your wireless net's password for every family member), then this may be a much more secure, equally simple approach. I hope this helps somebody else!

ThousandThanks  ;) Worked fine for me!

---

### Post by abhitux on 2010-01-29
> **ricojonah said:**
> I could be mistaken, but setting your keyring to a blank password could leave your system ready-and-willing to give all of your actual passwords to anyone (roommate, family, friends) who has physical access to your system. All they'd have to do is power up your system and have a minimal knowledge of what they're doing.

This may be a better solution for anyone experiencing this problem--it worked for me in both Jaunty and Karmic:


1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This method works fine for me in Karmic. Great idea; doesn't even compromise the security at all.Cheers :)

---

### Post by tdmsbn on 2010-02-04
> **ricojonah said:**
> I could be mistaken, but setting your keyring to a blank password could leave your system ready-and-willing to give all of your actual passwords to anyone (roommate, family, friends) who has physical access to your system. All they'd have to do is power up your system and have a minimal knowledge of what they're doing.

This may be a better solution for anyone experiencing this problem--it worked for me in both Jaunty and Karmic:


1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

This will allow any user account on your system to access the wireless network. If you're the only user on your system (or, as in my case, you *prefer* not having to type in your wireless net's password for every family member), then this may be a much more secure, equally simple approach. I hope this helps somebody else!

You're awesome man, major thanks. :popcorn:     I just want my computer to be usable by the other members of my family, but don't want them ending up doing ANYTHING that requires admin privileges. But establishing a network connection is something that i don't see as really requiring a password to use. major thanks man, just wish that this article was easier to find with Google searches. ^_^

---

### Post by Tinooz on 2010-05-13
Yes, that works.

---

### Post by eshm on 2010-06-18
I thought I would chime in and tell you that I've been having the same issues, and despite all the concerns about security, for someone like myself who is on a wired network connection with minimal threats to security **mcduck's posts [#5]("http://ubuntuforums.org/showpost.php?p=6982000&postcount=5") and [#7]("http://ubuntuforums.org/showpost.php?p=6982000&postcount=7")** worked like a charm for me, I'm running *Ubuntu 10.04*.

Thank you mcduck! =D>

---


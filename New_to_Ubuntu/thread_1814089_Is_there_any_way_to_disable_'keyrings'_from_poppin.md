---
title: "Is there any way to disable 'keyrings' from popping up?"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Sunfire0258 on 2011-07-28
[FONT="Arial"]Hi, I'm fairly new to Ubuntu; I've had it before but never really got the hang of it. Now I re-installed it on a different computer to try again.

I would like to know if/how I can disable my keyrings from coming up every time I download software and whatever else it may pop up for.[/FONT]

---

### Post by mcduck on 2011-07-29
Are you absolutely sure it's the *keyring* password request you see when downloading software? That should ask for your user password. ;)

What comes to the actual keyring, it's only unlocked once and doesn't ask you for password again until you log out. Furthermore, if you use a normal login it will be unlocked automatically for you at the same time, as long as your login password and keyring password are set to same. If you use automatic login, you should set the keyring password to empty one. That will allow programs to access the keyring without having to unlock it first, but on the other hand will store your passwords and keys in unencrypted format, which is of course less secure but doesn't make much of a  difference if you are already using automatic login anyway. ;)

The keyring password can be set, changed, or removed, using the "Passwords and Encryption Keys"-tool. Just right-click on the default keyring and select "Change Password".

edit: If it's the password confirmation for administrative tasks you wish to disable instead of the keyring password, sure, that's possible. And also really, *really* bad idea. Besides, you really shouldn't need to type that one very often. If you do, you are doing something wrong and should probably look for better ways to handle the admin tasks you do than try to make things a little bit easier at the cost of seriously crippling your system's security.

---

### Post by Sunfire0258 on 2011-07-29
Kiitos :)
I have all the passwords on my user account set to the same, I don't have it on auto sign-in because I'm not the only user in this computer. Normally when I'm in the software center it will only ask for my password on the first app I download, but sometimes it will ask me for it again after a few downloads. And as soon as I sign on to my account it asks me for my password again. If I remove a keyring won't it ask for me to re-enter it again once I do something to activate it?

---

### Post by mcduck on 2011-07-29
> **Sunfire0258 said:**
> Kiitos :)
I have all the passwords on my user account set to the same, I don't have it on auto sign-in because I'm not the only user in this computer. Normally when I'm in the software center it will only ask for my password on the first app I download, but sometimes it will ask me for it again after a few downloads. And as soon as I sign on to my account it asks me for my password again. If I remove a keyring won't it ask for me to re-enter it again once I do something to activate it?


Eipä kestä. :)

First, the thing is that there are two  separate passwords, a keyring password, and your login password. Apart from the mechanism used to unlock the keyring at login time the two have nothing to do with each other.

The keyring is used to store passwords, encryption keys and such things from various programs in a secure way. Gnome Keyring keeps the information in encrypted format when the keyring is locked, and you'll only ever need to unlock it once during a single session at desktop. You can't remove the keyring, that would break all programs that use it to store their information, but like I said you can set the keyring password to empty one to empty one which will store the data unencrypted but also removes the need to unlock the keyring. (so you wouldn't ever want to remove a keyring, or the Keyring Manager for the matter, only the *password*). And since you said you aren't suing automatic login, there's no reason for you to even do that.

And the login password is used to log in, and to verify administrative tasks. So this is the one you are asked when you install a program, edit a system file or do any other task that affects the whole system and all it's users. (you shouldn't need to enter this one too often, it has a 15 minutes timeout by default and won't ask you for the password again during that time. (And you can always use tricks like "sudo -i " and "gksudo nautilus" if you have some more complicated admin tasks to handle))

At this point I'm not sure which password you are actually talking about, since you keep mentioning the keyring, but all the task you talk about are the kind of ones that would ask for the login password. If you can clear which password you are having problems with then I might be able to help a bit more... :)

---


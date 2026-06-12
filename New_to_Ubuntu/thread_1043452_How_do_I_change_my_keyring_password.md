---
title: "How do I change my keyring password"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by tomsax on 2009-01-18
Does anyone know how to change the password for logging into the computer when I first turn it on.  Actually I would like to have no password prompt but the second best would be able to change it to a simpler password.

---

### Post by mjheagle8 on 2009-01-18
you can have no password by enabling automatic logon.

---

### Post by diablo75 on 2009-01-18
Open up your home folder and hit CTRL-H to reveal hidden files and folders.

Find the .gnome2 folder, and inside that is a folder called keyrings.  Open that up and delete whatever files you have in there.

This might not be the preferred method to some because this will also wipe out any passwords your keyring is currently holding (FTP accounts, evolution email, wireless network WPA/WEP security, etc) so you'll have to type them back in.

The next time it asks you to create a new default keyring, you do have the option of not typing in a new password and just leaving it blank.  Doing this will eliminate the need to enter a keyring password every time you want to connect to your wireless network or whatever other times it may have come up in the past.  That's just my preference.  Otherwise you can just type in a different keyring password of your choosing.

---

### Post by diablo75 on 2009-01-18
> **mjheagle8 said:**
> you can have no password by enabling automatic logon.

If you enable automatic login you'll have to type in a keyring password (if there is one).  But as mentioned above, if you erase your keyrings completely, and then recreate them with no password, you'll never be prompted to type it in again.  (I just figured this out a couple days ago and it's something I've been wanting to do for years).

---

### Post by tomsax on 2009-01-18
Thank you diablo, that worked a treat.  Just what I needed.  

I&#7743; hoping there are no security implications for not having a password but I have very little on my keyring anyway.

---

### Post by diablo75 on 2009-01-18
> **tomsax said:**
> Thank you diablo, that worked a treat.  Just what I needed.  

I&#7743; hoping there are no security implications for not having a password but I have very little on my keyring anyway.

Depends on where you live, I guess.  I probably wouldn't do something like this on a laptop.  I personally pass between two different secured wireless networks that require WPA passkeys to access, and those keys are stored in the keyring.  I prefer to keep the keyring on a laptop so if someone were to steal the laptop they'd never be able to gain access to those network without knowing the keyring password.  Further, I'd probably not enable automatic login on a laptop.  Might go so far as encrypting the hard drive at install and putting a password on the grub menu... heh heh, might be overkill, or it might not.  It really depends on how sensitive the information on the laptop is.  From a hackers perspective, you should never put anything sensitive on a laptop, no matter how secure you think it is.

But on a PC that's sitting in your own bedroom that can be secured with a locked door?  You probably wouldn't have to worry about anything unless you were robbed, or perhaps you want to restrict a childs accessing the internet to when you want them to.

---

### Post by thoror on 2011-03-24
I know this is an old thread, but it tops the search results in google, so I just wanted to provide another solution.
If you install the seahorse package in Xubuntu, you will be able to change the keyring password from the settings menu.
Details can be found [here]("http://www.geekyeric.com/?p=67").

---

### Post by LinuxQuint on 2012-12-06
> **thoror said:**
> I know this is an old thread, but it tops the search results in google, so I just wanted to provide another solution.
If you install the seahorse package in Xubuntu, you will be able to change the keyring password from the settings menu.
Details can be found [here]("http://www.geekyeric.com/?p=67").
that website is hacked.  

Moderator: ? remove the link? 

In Xubuntu

So, it's a year later.  I'm also trying to change my keyring password.  The Seahorse app says it's for gnome.  Will it work for Xubuntu?  The Seahorse reviews are pretty crappy, too.  Is there any other way to change the keyring password?  Or is the only reliable way to just delete the .gnome2/keyrings/  files and start over?  No inbuilt GUI?  how about a command line way?  I don't know how many passwords I have in keyring, and not sure I can re-locate them all.

---


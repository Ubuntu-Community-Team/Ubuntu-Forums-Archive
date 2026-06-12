---
title: "Can't change keyring password!!"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Mark Phelps on 2008-07-18
Just about the time I think I can finally leave Windows behind and go entirely to GNU/Linux, another real annoyance hits.  This time, it's the Gnome Keyring Manager.

I have a secure wireless network at home.  So, to connect, I click the network icon, select my network, enter the security stuff -- and then I get this popup for the keyring password.  I enter the password -- and it just keeps popping up.

So, I went into System --> Preferences --> Encryption and Keyrings. Click the Password Keyrings tab, click the "login automatically unlocked when user logs in." entry, click the Change Unlock Password button, and get this panel which wants the old password and the new password.

Problem is, it won't take my password!! I enter my password, the new one (twice) and I get "Couldn't change keyring password -- access denied".

I want to be able to save the security key so that I don't have to type it in every time -- but this keyring thing is stopping me.

So, is there some way to do this from a root terminal?

---

### Post by Mark Phelps on 2008-07-24
WOW -- 5 days and absolutely no responses!  Good thing I figured out a workaround by myself.

---

### Post by zorkerz on 2008-10-04
could you post your workaround? Im trying to change my default keyring password for my wireless access. Im using seahorse 2.24.0

thanks

---

### Post by linux2.6.24-19-generic on 2008-10-04
seahorse.

---

### Post by zorkerz on 2008-10-04
What do you mean?

---

### Post by linux2.6.24-19-generic on 2008-10-04
At some point you changed your system password.  Use the password that you originally installed the OS with.  This is my best guess.  

Sorry for the lame response of "seahorse" before.  I thought you were asking how to change the keyring password.

---

### Post by zorkerz on 2008-10-04
Yep I have seahorse its installed by default. Im using version 2.24.0 (this is the intrepid version). There appears to be a difference in the intrepid version it has less tabs I think than it used to. I think one of the missing tabs used to allow changing the keyring password.

---

### Post by zorkerz on 2008-10-04
oops my bad I have figured this out

go to applications->accessories->passwords and encryption keys (this opens seahorse)

then go to edit->preferences and the 'password keyrings' tab

the default keyring is normally the one wireless passwords are stored to. You can change its password and that of any other keyrings you have made here.

---

### Post by Axos on 2008-11-07
> **zorkerz said:**
> go to applications->accessories->passwords and encryption keys (this opens seahorse)

then go to edit->preferences and the 'password keyrings' tab

There is no menu bar in this applet. At least not the one I'm looking at in 8.10 (Intrepid Ibex). So there is no way to click "edit->preferences".

I've been Googling and Googling and Googling and cannot find a SANE (read: included with the base system installed from CD) way to change my keyring password. I ***KNOW*** the password. It currently matches my login password. But if I change my login password, the keyring password stays the same and I get prompted for it every time.

If the difficulty of changing the keyring password has something to do with "security", someone please tell me how secure a password YOU CAN'T CHANGE is.

---

### Post by Axos on 2008-11-07
Arrrgh. I was using "System -> Preferences -> Encryption and Keyrings" rather than "Applications -> Accessories -> Passwords and Encryption Keys". Duh. Doh. Etc. Sorry. Problem solved. I just need a brain transplant. Is that something I can do myself? Anyone got a spare brain they aren't using? I guess I'll go check ebay.

---

### Post by zorkerz on 2008-11-07
Ya thats happened to me as well. The names are not very explanatory and its unclear what they do or how they differ. A bug has been filed about it on launchpad [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/289516](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/289516) please any further comments upstream however at the bugzilla bug.

---

### Post by pete25r on 2008-12-22
[QUOTE=Mark Phelps;5415234]Just about the time I think I can finally leave Windows behind and go entirely to GNU/Linux, another real annoyance hits.  This time, it's the Gnome Keyring Manager.

Yeh me too...

Look what I found. I've done it but haven't rebooted to test it yet. A handful or better have tried it and say it works.

check it...
[http://ubuntuforums.org/showthread.php?p=2776815#post2776815](http://ubuntuforums.org/showthread.php?p=2776815#post2776815)

---


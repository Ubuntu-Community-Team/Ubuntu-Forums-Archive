---
title: "[SOLVED] default keyring?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by djbushido on 2008-12-23
When entering in the WEP key for my wireless internet, afterwards i was asked to give the password for the default keyring. I typed in my root password, but it came back saying that wasn't right. Confused, i re-typed to avoid errors, but it was still wrong. Any ideas?

---

### Post by Brain-free on 2008-12-23
Have you checked shutting down the PC and trying again?

For me, wireless has problems after say, I restart the PC. You might want to check it too.

---

### Post by anewguy on 2008-12-23
It sounds like it already had a password - did you set up wireless previously and something changed?

If worse comes to worse, just get rid of the old keyring file and it will ask you again next time and create a new keyring.  As long as pam is running (not sure, but I think it's been standard since at least 7.10) just use your regular logon password.  If you do, you won't get prompted for it again - perhaps you need to just try your regular logon password now?

dave :)

From another post on this same subject:

 November 17th, 2008    #4  
achase79 
5 Cups of Ubuntu

 

Join Date: Oct 2008
Location: Illinois, USA
Posts: 19 
Thanks: 0
Thanked 2 Times in 2 Posts 
  Re: Unlock Keyring??? 

--------------------------------------------------------------------------------

You will have to rebuild the keyring. in the home folder there should be a .keyring folder that is a hidden folder or in the .gnome* folder. If you rename it or delete it and restart it will have you rebuild it and you can set it to your user password.

---

### Post by djbushido on 2008-12-23
my root password is my regular, and it's not a problem with wireless, this is just where it's showing up at.
And what is this "pam"? My terminal said command not found...
where would i delete the keyring file?
I'm so confused...

---

### Post by jerome1232 on 2008-12-23
> **djbushido said:**
> my root password is my regular, and it's not a problem with wireless, this is just where it's showing up at.
And what is this "pam"? My terminal said command not found...
where would i delete the keyring file?
I'm so confused...

btw I think  your getting your passwords a bit mixed up, by default Ubuntu locks the root acount (It can't be logged into) and it has no password.

The place to delete your encryption keys and passwords would be under Applications-Accessories-Passwords and Encryption keys

---

### Post by Brain-free on 2008-12-23
For the latter, you can go to Applications ---> Accessories --> Passwords and Encryption Keys --> Passwords 

and right click on your key and then "Delete Key"

---

### Post by djbushido on 2008-12-23
there is no "key" (neo either) in this menu. I did create a keyring under preferences for default. Also, sorry for the confusion-by root password i meant my login/sudo password. I'll see if my new keyring works.

---

### Post by anewguy on 2008-12-23
You won't be able to just "execute" pam, however if you do a sudo ls -e to see all the processes running on your system you should just see pam there.  If not - just install it from synaptic package manager.

The easiest way to get around all this (I've been there myself in the past) is just to delete the keyring file itself.  Next time it will ask you to enter the stuff for your connection and then ask for a password again - use your regular logon password.  If you do that you *should* be set ;)

BTW - you should be able to see the folder and the file via the regular file explorer IF you go to view and let it show hidden files.

Dave :)

---

### Post by djbushido on 2008-12-23
okay, pam is not running. second: pam is not in synaptic (or anything with a like name having anything to do with security-i am using 8.10)
Will try deleting all keyrings to see if that works.

---

### Post by anewguy on 2008-12-23
How many keyrings do you have???

pam may be listed in synaptic as something like a keyring manager.

---

### Post by djbushido on 2008-12-24
pam wasn't listed in synaptic (or anything like it that I saw) as a keyring manager. I re-read through the posts and re-building the folder worked fine. Marking solved, and thank you guys for your help.

---


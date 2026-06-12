---
title: "Protect a folder with a password?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Jimleko211 on 2009-07-28
I was wondering if there was a way to block off a folder from someone who didn't know your password.  Like if you left your computer unattended and your sister or someone came poking around, they couldn't get into sensitive folders without your password.

---

### Post by credobyte on 2009-07-28
```
sudo chown -R root:root /secret_path

```I hope she does not know your root password ? :p

---

### Post by philcamlin on 2009-07-28
> **credobyte said:**
> ```
sudo chown -R root:root /secret_path

```I hope she does not know your root password ? :p
and how would you get it back to acess because that would change the permissions so you wouldent even be able to acess :popcorn:

---

### Post by credobyte on 2009-07-28
> **philcamlin said:**
> and how would you get it back to acess because that would change the permissions so you wouldent even be able to acess :popcorn:
```
gksudo nautilus /secret_folder
sudo chown -R user:user /secret_folder
```

Not that hard :p

---

### Post by Jimleko211 on 2009-07-28
Thanks.  Nah, she doesn't know my password.

---

### Post by philcamlin on 2009-07-28
> **credobyte said:**
> ```
gksudo nautilus /secret_folder
sudo chown -R user:user /secret_folder
```Not that hard :p

hehe nobody will hack my files again :)

---

### Post by nhasian on 2009-07-29
you may also want to look into [truecrypt]("http://www.truecrypt.org/")

you can create a virtual volume inside a password protected file.

---

### Post by ibuclaw on 2009-07-29
You could setup a [private directory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Setup%20Your%20Encrypted%20Private%20Directory"). But I think it automounts when you login.

My personal favourite way would just be to turn a USB stick into an encrypted filesystem. :)

Regards
Iain

---

### Post by abhiroopb on 2009-07-29
If it is low-level protection you want...then simply set the screen to lock and make a login password (if you need help doing this let me know and I'll provide more detailed descriptions).

---

### Post by mapes12 on 2009-07-29
I would do this via GUI and change the permissions like this:

Assuming the folder is in your /home/username directory.

1. Right click the folder
2. Select Properties
3. Select Permissions from the tab at the top
4. Change the permission for "Others" from "Access Files" to "None"

Then when someone else logs into their account they will not even be able to see the folder and even if they work out the path name via Terminal they will have a "Permission denied" output if they try any command to access the contents. You can do this with your entire /home/username folder if required. Only root can change permissions for /home though :D

EDIT: > Like if you left your computer unattendedThe above permissions solution will only work provided you log off before leaving your machine unattended.

---

### Post by The Cog on 2009-07-29
My favourite is this way:
1: Install package **encfs**
2: Create a file **/usr/local/bin.crypton** with these contents:
```
#!/bin/sh
encfs ~/.crypt ~/crypt

```
3: Create a file **/usr/local/bin.cryptoff** with these contents:
```
#!/bin/sh
fusermount -u ~/crypt

```
4: Make them executable: **sudo chmod +x /usr/local/bin/crypto***

Now when you run the command crypton it will ask you for a passphrase, then create a directory ~/crypt which you can put your secret stuff in. The command **cryptoff** makes the contents disappear. To see/edit the contents you must use the command crypton and re-enter the passphrase.

The actual data is held in enctypted form in ~/.crypt. The crypton command mounts this encrypted data much like mounting a network share - there are never any real contents in ~/.crypt if you were to examine the hard disk.

---

### Post by llamabr on 2009-07-29
At the risk of sounding pedantic, the linux permissions structure already does this.  When you're sitting in front of your computer, you should be logged in.  When you're not, you should log out.  You then set the permissions of things you don't want anyone to read at 700.

---

### Post by aysiu on 2009-07-29
Change the permissions on the folder to 700, and lock your screen or log out.

Or encrypt the folder using TrueCrypt.

Problem solved.

---

### Post by bodhi.zazen on 2009-07-29
> **llamabr said:**
> at the risk of sounding pedantic, the linux permissions structure already does this.  When you're sitting in front of your computer, you should be logged in.  When you're not, you should log out.  You then set the permissions of things you don't want anyone to read at 700.

+1

---

### Post by hubertofliege on 2010-07-17
I don't understand why this concept seems unusual or foreign.

I already set my computer to lock after five minutes of inactivity.  Even still, I may want to allow another person to use my account while still keeping a few files private.

---

### Post by bodhi.zazen on 2010-07-17
> **hubertofliege said:**
> I don't understand why this concept seems unusual or foreign.

I already set my computer to lock after five minutes of inactivity.  Even still, I may want to allow another person to use my account while still keeping a few files private.

I suggest you allow friends/family to use the guest account if you have data you wish private.

Otherwise you would need to use encryption.

---

### Post by Zorgoth on 2010-07-17
Just noting that

```

sudo chown root:root path_to_secret_folder

```

may not be enough.

If permissions aren't alreasy et like this, yo also need to say

```

sudo chmod 700 path_to_secret_folder

```

---

### Post by new__buntu on 2010-07-17
If all you're worried about is someone accidentally messing something up simply hiding the file by putting a '.' (apostrophes to denote a literal character) in front of it may be sufficient.

If you're worried about something a little more malicious I'd recommend the chown/chmod solution that others have mentioned. BTW, you don't technically have to chown to root. a "chmod 000" will lock everybody without sudo/root power out. It's also worth noting that unless your file is in a write-protected directory it can still be deleted, regardless of what permissions you have pertaining to the file itself.

---

### Post by linux18 on 2010-07-17
Just zip the folder. when you zip you have the option for password protection and using peazip you can encrypt the folder. linux supports mounting compressed files so the compression/decompression is virtually transparent. 
OT, I'm wishing for truly transparent compression for EXT5 from boot up to shutdown

---


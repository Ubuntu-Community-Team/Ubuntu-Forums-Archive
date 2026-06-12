---
title: "Access ubuntu9.10 encrypted home folder on HDD A while logged on to HDD B Ubuntu 10.4"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-12
How can I access my Ubuntu 9.10 encrypted home folder on hard drive A while logged on to Hard Drive B's Ubuntu 10.04?

---

### Post by ubunterooster on 2010-05-12
I think encryption is to prevent that from happening.

---

### Post by hanzj on 2010-05-12
but if i have the password for that user account on ubuntu 9.10 (since it is my account), why can't i "unlock" the 9.10 home folder?

---

### Post by jakupl on 2010-05-12
When you created the encrypted home folder, you were instructed in how that is done. Did you write down the password given to you at the time?

---

### Post by hanzj on 2010-05-12
jakupl, yes, i still know the password for the ubuntu 9.10 folder (same as my sudo access password)

---

### Post by jakupl on 2010-05-12
> **hanzj said:**
> jakupl, yes, i still know the password for the ubuntu 9.10 folder (same as my sudo access password)

No not that password. I think you should be given another password upon encrypting the partition.

---

### Post by hanzj on 2010-05-12
jakupl, 
no it gets automatically decrypted when I log on to ubuntu 9.10. the encryption is done  on-the-fly by ubuntu. I didn't use some other program, i don't think.

---

### Post by jakupl on 2010-05-12
This might help you. [http://www.linux-mag.com/cache/7568/1.html](http://www.linux-mag.com/cache/7568/1.html)

Take notice of this section:

```
$ sudo apt-get install ecryptfs-utils
$ ecryptfs-setup-private
Enter your login passphrase:
Enter your mount passphrase [leave blank to generate one]:
************************************************************************
YOU SHOULD RECORD THIS MOUNT PASSPHRASE AND STORE IN A SAFE LOCATION:
3770637d136fa485d22e36ab8c94afb1
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************
Done configuring.
Testing mount/write/umount/read...
Testing succeeded.
Logout, and log back in to begin using your encrypted directory.

```
However, as far as I know, you will probably have to wave goodbye to that partition if you can't logon.

Next time you encrypt something, don't do it in a rush.

---

### Post by hanzj on 2010-05-12
jakupl,
if i choose to boot from hard drive A (the hard drive with ubuntu 9.10), then I can easily access my 9.10 home folder. 

I guess I'm complicating things by wanting to access my ubuntu 9.10 folder while logged on to ubuntu 10.04 (on a different hard drive).

---

### Post by jakupl on 2010-05-12
oh wait i misunderstood.. so you can actually log in, then you might be able to somehow recover the password or something similar.

EDIT: yeah ok. wait.

---

### Post by jakupl on 2010-05-12
[here you go.]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Mount Passphrase")

---

### Post by ubunterooster on 2010-05-12
[B]Does this mean you can de-encrypt the home folder permanently, Jackupl?  :
[/B]

> 



**How to  Remove an Encrypted Private Directory Setup**

 Perhaps an Encrypted Private  Directory is not for you.  To remove this setup: 

[LIST=1]
[*]Ensure that  you have moved **all** relevant data out of your ~/Private  directory
[*]Unmount  your encrypted private directory
[LIST]
[*] $ ecryptfs-umount-private
[/LIST]
 
[*]Make ~/Private  writable again
[LIST]
[*] $ chmod 700 ~/Private
[/LIST]
 
[*]Remove  ~/Private, ~/.Private, ~/.ecryptfs (**Note: THIS IS VERY PERMANENT**)
[LIST]
[*] $ rm -rf ~/Private ~/.Private ~/.ecryptfs
[/LIST]
 
[*]Uninstall  the utilities
[LIST]
[*] $ sudo apt-get remove ecryptfs-utils libecryptfs0
[/LIST]
 
[/LIST]
 


---

### Post by jakupl on 2010-05-12
> **ubunterooster said:**
> [B]Does this mean you can de-encrypt the home folder permanently, Jackupl?  :
[/B]

Well... I'm no expert when it comes to this, so I dare not say.

---

### Post by hanzj on 2010-05-12
to do
>  ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase "login passphrase" do i need to log in to the hdd A (ubuntu 9.10) ?

and if i can do the command while logged on HDD B (ubuntu 10.04), i don't think the command will work, because it does not specify that the command is for HDD A.

---

### Post by ubunterooster on 2010-05-12
yes.

---

### Post by hanzj on 2010-05-14
I've recovered my mount passphrase.

When I try to go to ~/Private on Nautilus, it tells me that it can't find it.

UPDATE: However, there is ~/.Private folder.



  I learned  the difference between ~/Private and ~/.Private:
> 
After logging back in, all content of any files or folders you write in ~/Private will be encrypted when written to the disk, in the hidden directory ~/.Private. 



Question:
 Is ~/.Private the same as my /home/ folder?

---

### Post by ubunterooster on 2010-05-14
That _is_ what the above quote implies.

---


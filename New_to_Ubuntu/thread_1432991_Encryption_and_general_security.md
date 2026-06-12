---
title: "Encryption and general security"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by roton on 2010-03-18
Having been away from linux a long time I'm back and so far enjoying it. I recently installed the 64bit alternate 9.10 cd with encryption.
My questions are:

1) Is the encryption for the whole drive? It only asked about the home directory when I installed but I can see an lvm2 padlock icon on my whole hard drive when I login.

2) If only the home directory is encrypted then is it possible to retrieve data from the swap space?

The swap file/partition is the main thing concerning me. Is this cleared as part of the shutdown? If not how can we manually clear it to prevent otherwise encrypted data from being seen?

Doing "*sudo swapoff -a*" would only transfer stuff to physical memory, not clear it from swap.

Thanks in advance.

---

### Post by Paqman on 2010-03-18
If you chose an LVM whole disk encryption then that's what you've got.

> **roton said:**
> If not how can we manually clear it to prevent otherwise encrypted data from being seen?


Your can use one of the tools in secure-delete:
```
sudo swapoff -a
sudo sswap /dev/sdaX
sudo swapon -a
```

(Where X is a the correct number for your swap partition.)

---

### Post by diablo75 on 2010-03-18
There is an article at the front of the most recent issue of 2600 Magazine that describes a pretty clever way to hack the encryption used by Ubuntu Alternate installation.  

The flaw in this setup is the /boot partition; it can't be encrypted because it contains the little program that is responsible for decrypting the contents of the drive.  Hacking it is simply a matter of recompiling the source code of that program to do any number of things after a successful password has been entered.  The example used in the article had the password stored and then sent to another PC over a network connection and then replace the modified program with the original.   So someone could come along with a Live CD, access your /boot partition, replace a couple files, then you start it up, type in your password, that password is sent to someone else, the evidence is deleted automatically and you're none the wiser.

The solution it proposed to this little dilemma was that when you install the OS, put a USB flash drive in the computer and install the /boot partition onto that.  Just make a duplicate of it so if one goes bad you have a spare.

---

### Post by ibuclaw on 2010-03-18
> **roton said:**
> Having been away from linux a long time I'm back and so far enjoying it. I recently installed the 64bit alternate 9.10 cd with encryption.
My questions are:

1) Is the encryption for the whole drive? It only asked about the home directory when I installed but I can see an lvm2 padlock icon on my whole hard drive when I login.

2) If only the home directory is encrypted then is it possible to retrieve data from the swap space?

The swap file/partition is the main thing concerning me. Is this cleared as part of the shutdown? If not how can we manually clear it to prevent otherwise encrypted data from being seen?

Doing "*sudo swapoff -a*" would only transfer stuff to physical memory, not clear it from swap.

Thanks in advance.

If you've selected "Encrypt Home Directory" in the installer, this will also encrypt the swap partition too.

Regards
Iain

---

### Post by J V on 2010-03-18
Cool, didn't know that ibu...

Your home directory is encrypted (Thats where you should be putting your stuff anyway) but your main drive isn't (Makes it run apps faster), it uses wrapped pass-phrases, so when you change your password it will only change the warpped passphrase rather than re-encrypt the whole home directory...

btw ibu, seeing as you know so much about this, why can I only change password through about me? users and groups just doesn't do anything...

Also, does the password command automatically change the ecryptfs data or do you have to do that manually later?

---

### Post by roton on 2010-03-18
Thanks for the info guys. 
@ ibuclaw - thats great news 
@ diablo75 - are you saying the boot partition can never be encrypted for that reason? Doesn't TrueCrypt for Windows support whole drive encryption including boot partition? Maybe this will be implemented in the next release of TrueCrypt for Linux?

---

### Post by Paqman on 2010-03-19
> **ibuclaw said:**
> If you've selected "Encrypt Home Directory" in the installer, this will also encrypt the swap partition too.


Good to know, cheers!

---


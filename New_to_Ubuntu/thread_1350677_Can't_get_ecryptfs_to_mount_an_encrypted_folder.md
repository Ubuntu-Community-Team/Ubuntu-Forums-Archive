---
title: "Can't get ecryptfs to mount an encrypted folder"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-12-09
OK, so I have a folder of encrypted files (a backup from an encrypted home folder whose drive has KO'd).

Sensibly, I have the passphrase.

However, I just cannot get ecryptfs to mount the encrypted folder!

**What I have:**

[LIST]
[*]The backup of the original home folder on an external hard drive, which contains:
[LIST]
[*]*richard* (the user's directory). It contains only the four files put there by ecryptfs.
[*]*.ecryptfs*. This contains:
[LIST]
[*]Another *richard*, which in turn contains:
[LIST=1]
[*]another *.ecryptfs* with details of the encryption
[*]*.Private*, which contains all the encrypted files.
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]The original 32-character recovery passphrase as given to me by the initial Ubuntu installation.
[/LIST]

**What I've tried, and the results**

I ran this from the Live CD. In the code below, **bold** shows what I typed and [COLOR=Navy]blue[/COLOR] shows what the computer said.

```
**sudo mkdir /decrypt**   *# This is where I want to mount the decrypted folder*
**sudo mount -t ecryptfs /media/extdrive/originalhome/.ecryptfs/richard/.ecryptfs/.Private /decrypt**
[COLOR=Navy]
Passphrase:[/COLOR]      *# I entered the 32-character passphrase.*
[COLOR=Navy]
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]:[/COLOR] **1**
[COLOR=Navy]
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]:[/COLOR] **1**    *# I've also tried 2 here.*
[COLOR=Navy]
Enable plaintext passthrough (y/n) [n]:[/COLOR] **n**
[COLOR=Navy]
Enable filename encryption (y/n) [n]:[/COLOR] **y**
[COLOR=Navy]
Filename Encryption Key (FNEK) Signature [fc99b6c32f247b01]:[/COLOR]   *# This agrees with the value in Private.sig*.
[COLOR=Navy]
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=fc99b6c32f247b01
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=fc99b6c32f247b01
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? :[/COLOR] **yes**
[COLOR=Navy]
Would you like to append sig [fc99b6c32f247b01] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? :[/COLOR] **yes**
[COLOR=Navy]
Successfully appended new sig to user sig cache file
Mounted eCryptfs[/COLOR]
```At this point, it looks like it succeeded, right? However, when I list the contents of the mounted directory, I see that nothing has been decrypted...
```
**sudo ls /decrypt**
[COLOR=Navy]ECRYPTFS_FNEK_ENCRYPTED.FWaI3yUWaSUhh-SWZvp0N6w.7GdxIN8.sIdl0yIE-swMHEeb4wyUqqQsKU--
ECRYPTFS_FNEK_ENCRYPTED.FWaI3yUWaSUhh-SWZvp0N6w.7GdxIN8.sIdl2tuXMTF9wNDkiQLYeJYggE--
ECRYPTFS_FNEK_ENCRYPTED.FWaI3yUWaSUhh-SWZvp0N6w.7GdxIN8.sIdl3K2wiBV4gaXx-JHhfu3K6U--
[/COLOR]*# etc.*
```What am I doing wrong or missing out?

---

### Post by Paddy Landau on 2009-12-10
Ta da! I found the answer.

Check it out:
[Recovering Files from eCryptfs Encrypted Home]("http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/")

This should be in the official documentation.

---


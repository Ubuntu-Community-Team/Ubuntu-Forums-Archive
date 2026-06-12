---
title: "Access data from an encrypted home partition"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Falc7 on 2011-02-19
Hi
I had two installations of ubuntu (i forget why i did that) on how old laptop. Both of them had encrypted home partitions. Anyway that laptop broke, so i bought a new one. I have put the HDD of the old laptop into a caddy and attached it via USB to the new laptop. Now i want to remove the encrypted setup of the home folders (as i found access data in a encryped home folder to be almost impossible). 

I found this page
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#How](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How) to Remove an Encrypted Private Directory Setup
But i have a feeling this can only be done if you can boot into the hard drive (which i currently can't, when i select the laptop to boot from this HDD in the caddy, nothing happens at all)

I also tried this ```
I got it. I found a fix. Here's what you need to do:
i) Boot from the live cd.
ii) Mount your harddisk.
iii) Open terminal.
iv) Then, cd /whatever/it/shows/for/harddrive/in/the/navigation/bar/
v) After that, type this code: sudo unmount Name of Home folder
vi) Type this code: sudo chmod -R 777 Name of Home folder
vii) Enjoy.
```
But it didn't work either

---

### Post by blazemore on 2011-02-19
If you could do this, any malicious attacker or thief could access your data as well.

---

### Post by Falc7 on 2011-02-19
I know both the password on the ubuntu installation i am using, and the passwords on the ubuntu installations on the hard drive, that counts for nothing? Is there no way to get the data off? Could i boot from the hard drive perhaps?

---

### Post by thane1 on 2011-02-19
Check out this thread.  

[http://ubuntuforums.org/showthread.php?t=1580999&highlight=decrypt+encrypted+home+folder%3F](http://ubuntuforums.org/showthread.php?t=1580999&highlight=decrypt+encrypted+home+folder%3F)

I ran into so much agravation getting mine sorted out, that I eventually backed up my /home to another new, unencrypted /home partition and then reformatted the old, encrypted one (once I'd gotten access to the encrypted one of course.)  Also using the process in the link above, make sure, that you have first made the directory in your filesystem, that you are going to temporarily mount your encrypted /home onto.  Cheers.

---

### Post by Falc7 on 2011-02-19
okay cool i will try that out in the morning, it looks quite complicated though

I've noticed that if i sudo update-grub, then i grub finds all the ubuntu installations on the hard drive, but if i try to boot into them, i get the message 'no such partition exists'

---

### Post by Falc7 on 2011-02-23
That guy was really helpful, here are my results:
First section:
```
sudo -i
cd /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie 
ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private 
ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs 
ls /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 


ubuntu@ubuntu:~$ sudo -i 
root@ubuntu:~# cd /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie 
-bash: cd: /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie: No such file or directory 
root@ubuntu:~# cd /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie 
-bash: cd: /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie: No such file or directory 
root@ubuntu:~# cd /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v2j1nXAZJQOPawd.gs2NT9k-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v327.xrze4K0H1mrFzU.uZ--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v3WiGaWEaJIewcTkjaQUz-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v47MXTpt7Biu8nRIlp9CqUE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6ajWWF8wH7LFZMjiLNSaU--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6OH3XEoAfb5K3bX1o38f4U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6qVztfU0ngSF-u2jssOiuE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7A1sFEzhtkUL0isE9Iu-S--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7To6cOPG1H64ueEIfo62h--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v8tlaYMSbqIF.zWBxRTZIRk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vAqs9mgxirc2GGqRyb52P4--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBAG6cBym01o2gCDCpw0Yjk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vbB-.-BeGfZ5gbLx1hGVjOU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBcTMj.Oj7XV.ZZNhhgpECk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vbDG6c9-tEBmgj868h1ahkU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBqp3C6LKi-TKjIqJKexa2--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vc59eXvNirf7k4S2AN-wldU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCkZ1SaRQ.hvqtaZ-WuAfC--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCpGSS5LdqqbEDrFeZLuwIE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCVgfaEBJ47MSUeq5Q8o4KU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vD26Amot2dYya0LmaKrE2aE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vD7giVRn8Q22yNBs7WFYDYE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vDwTK3aj.TcLIWiqCHAR1bk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vEb2jH9AlPZ7qwi0d03FWPU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81veliRjXO7bNoyT-48NgWjsE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vFm1PeD8OeYmvbrGPMes9kU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vFXoPf9iz3.OS4sS8fSHl.--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vgqyttJAQViYm.PzpQsx2dU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vHGQKCITt9IgA2qQcoeu3qU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vIC7VazXhP5Lf8w4qZO.IVk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vIkFA8kvSG6E5pcpPIrAUdE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vilhVyJ58lN1OrI445XBUik-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vITyT732T1KrxZXawbnNWck-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81viv2r0RNVAoXKck4k0m-U-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vjmIoJd0-Bai.L55CJ7xagk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vjSDW.iLD7nXsplZOPa6GMk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vk-.scSu3b1-CXDAUG-fcoU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vkwP94Esb1GnPA345M3MtdE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vlOCr6KwEHB6jGYpCUkuPeE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vLzTNDCe.NE.80U9uSNcItk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vMLD5DX0vxJ-.Lvph444k5--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vN1UbShbVxGVUFis9zlzxQU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vnbqqhHd8mzlw1dFL9kQaTE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vOCNKCOCn5AML-2abm.xktU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vPhcq5Z3TFSn0sjVPn1BFYU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vpl34hdNX3RMyrnEPJb4OY--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vqdjLgR9.7lJHFvb1B6otVU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vQjI2OrS6NwyqgmTNmf259U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vQwHafV1cpzVjlZKWztnxf--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vR-49Qi-KC5FFD4w4jIQ-uk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vRiU7bug9B4rIPskVqHabH--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vt4RVev4DqePZwJMXAjCsa--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vT5-K6xNayw0fLmgAM-nCVE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuAosIC1J3nvCVXxtjUmk7--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v.ueWeMYdRdKR7J9ltIpjfU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuIHyffJYioVKcoWsvlNDO--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vumKEmK.gOiBepnP.tRED-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuWbIHJmmPPqyoOKEd1Tfr--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vwNuuavgFMYeIR3aEPYTawU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vWOu22vS3IoineBHSWwocI--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxbyRHKns2giOX5XqcOujgU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxgA7oV3M3kz.H07CYrBUUE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vXGBz3LsPrRTmV5UlZuI9mE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vXgee1PhBA42-FH0ZITsO9U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vyJa6yo.0JXmZY0rn1cCgNU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vZodbRlw.EniW0jpEiuNKN--- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7cpf3KMmlzBkqzDW7zDx7J47VB8vexdNcz1.KudYVaU- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7cpf3KMmlzBkqzDW7zDx7K99WewYIBeB05WtZmLIvzY- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vC7LPMmgx6L.-PZWMNQdhfiF7lWP7o9.qRbbdk0l0tNI- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vdqQewYLGv7hKPqZmEZqt04hEe0Ufc2AZuZL12ZdraoA- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vfuBhBIkN9glCCttOXkvvVOiVIarlmkmAzdlGPBstjgE- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vN4sL4cAmS115MtoZReUW4i5tqmlQAPpKqbTZbSnIwGQ- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vOL5-U47E1RCD5oO5YGA4OoK9RCD3YqzwAbYg7tjYzDs- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vSQe4PuPdGuu-wmGAAhhDKzRdnt88aZhIEwjU9ud8Tpc- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vvzNYTXxL69vfstBu1eziSFDPXYM8vx12onsKzBecwkE- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vx96HxKr8PyWBn3FtfIj0D3o6OuRNZ6xfldlqyWZXUV2- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxLj3AQL80BsaW.SRkS505ZDIZ.jsaEJ-qDuhcYbwzfg- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vYU0rfZziu9uesAXHiPJLp6jdjo-H2lxBnq4YqmNbhCE- 
ECRYPTFS_FNEK_ENCRYPTED.FYb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vMjUvTUYHvv1XbJ-CDdUmeRF1rzWc.fagTlsdfA-nuhqLolkMtrv0n9aNkP7a5JQV 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs 
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 
```

```
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ecryptfs-unwrap-passphrase /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
Passphrase: 
06199949a6a5dfbfa8bfa626078ee5ab 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 


root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [375e8d8580bb4051] into the user session keyring 
Inserted auth tok with sig [c2941b98f4f7b9c6] into the user session keyring 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 

```

```
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ecryptfs-unwrap-passphrase /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
Passphrase: 
06199949a6a5dfbfa8bfa626078ee5ab 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 


root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [375e8d8580bb4051] into the user session keyring 
Inserted auth tok with sig [c2941b98f4f7b9c6] into the user session keyring 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 

mount -t ecryptfs /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private/ /mnt/Private



root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# mkdir /mnt/Private 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# mount -t ecryptfs /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private/ /mnt/Private 
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded) 
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded) 
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded) 
Selection [aes]: 
Select key bytes: 
 1) 16 
 2) 32 
 3) 24 
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y 
Filename Encryption Key (FNEK) Signature [375e8d8580bb4051]: c2941b98f4f7b9c6 
Attempting to mount with the following options: 
  ecryptfs_unlink_sigs 
  ecryptfs_fnek_sig=c2941b98f4f7b9c6 
  ecryptfs_key_bytes=16 
  ecryptfs_cipher=aes 
  ecryptfs_sig=375e8d8580bb4051 
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt], 
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong. 

Would you like to proceed with the mount (yes/no)? : yes 
Would you like to append sig [375e8d8580bb4051] to 
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no 
Not adding sig to user sig cache file; continuing with mount. 
Mounted eCryptfs 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 

```

I then started nautilus as root, but i still cant access the data there :(

---

### Post by thane1 on 2011-02-23
Just a thought...  Did you try to access your new mounted location or did you try to access /home?

---

### Post by Falc7 on 2011-02-24
I started nautilus, then went into the mounted partition named 9af3021e-32c8-4bd4-9c10-2a79cd16f383, then went into home, Jamie, and clicked on the icon that says 'access your private data' the screen flickered, but nothing else happened

---

### Post by KIAaze on 2011-02-25
I got your message. Sorry for the late reply. I didn't have time before. ;)

I read through your terminal output and it looks very good.
At the end (after the "Mounted eCryptfs" line), your data should be readable in "/mnt/Private".

You can check it first with:
```
ls /mnt/Private
```

Or open it in nautilus directly with:
```
nautilus /mnt/Private
```

If you still don't see you data, try:
```
df -h
```
It should list the mounted partitions like this for example:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G   12G  7,4G  61% /
none                  1,9G  328K  1,9G   1% /dev
none                  2,0G  2,9M  2,0G   1% /dev/shm
none                  2,0G  404K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
/dev/sda5             224G  199G   14G  94% /home
/home/kiaaze/.Private   224G  199G   14G  94% /home/kiaaze/Private
/dev/sdc1             466G  216G  250G  47% /media/Expansion_Drive_500GB

```

On the left are the devices and the path to their right is their mount point.
ex: /dev/sdc1 is mounted at /media/Expansion_Drive_500GB
/home/kiaaze/.Private is mounted at /home/kiaaze/Private

In your case, you should look for the mount point of "/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private/".

---

### Post by Falc7 on 2011-02-26
I see this:
[http://i.imgur.com/wmSgS.png](http://i.imgur.com/wmSgS.png)
Perhaps its a problem with encrypted file names?

Here is what i did
Part 1:
```
ubuntu@ubuntu:~$ mount -t ecryptfs /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private/ /mnt/Private 
mount: only root can do that 
ubuntu@ubuntu:~$ sudo -i 
root@ubuntu:~# cd /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v2j1nXAZJQOPawd.gs2NT9k-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v327.xrze4K0H1mrFzU.uZ--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v3WiGaWEaJIewcTkjaQUz-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v47MXTpt7Biu8nRIlp9CqUE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6ajWWF8wH7LFZMjiLNSaU--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6OH3XEoAfb5K3bX1o38f4U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v6qVztfU0ngSF-u2jssOiuE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7A1sFEzhtkUL0isE9Iu-S--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7To6cOPG1H64ueEIfo62h--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v8tlaYMSbqIF.zWBxRTZIRk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vAqs9mgxirc2GGqRyb52P4--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBAG6cBym01o2gCDCpw0Yjk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vbB-.-BeGfZ5gbLx1hGVjOU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBcTMj.Oj7XV.ZZNhhgpECk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vbDG6c9-tEBmgj868h1ahkU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vBqp3C6LKi-TKjIqJKexa2--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vc59eXvNirf7k4S2AN-wldU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCkZ1SaRQ.hvqtaZ-WuAfC--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCpGSS5LdqqbEDrFeZLuwIE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vCVgfaEBJ47MSUeq5Q8o4KU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vD26Amot2dYya0LmaKrE2aE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vD7giVRn8Q22yNBs7WFYDYE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vDwTK3aj.TcLIWiqCHAR1bk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vEb2jH9AlPZ7qwi0d03FWPU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81veliRjXO7bNoyT-48NgWjsE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vFm1PeD8OeYmvbrGPMes9kU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vFXoPf9iz3.OS4sS8fSHl.--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vgqyttJAQViYm.PzpQsx2dU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vHGQKCITt9IgA2qQcoeu3qU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vIC7VazXhP5Lf8w4qZO.IVk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vIkFA8kvSG6E5pcpPIrAUdE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vilhVyJ58lN1OrI445XBUik-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vITyT732T1KrxZXawbnNWck-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81viv2r0RNVAoXKck4k0m-U-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vjmIoJd0-Bai.L55CJ7xagk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vjSDW.iLD7nXsplZOPa6GMk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vk-.scSu3b1-CXDAUG-fcoU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vkwP94Esb1GnPA345M3MtdE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vlOCr6KwEHB6jGYpCUkuPeE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vLzTNDCe.NE.80U9uSNcItk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vMLD5DX0vxJ-.Lvph444k5--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vN1UbShbVxGVUFis9zlzxQU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vnbqqhHd8mzlw1dFL9kQaTE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vOCNKCOCn5AML-2abm.xktU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vPhcq5Z3TFSn0sjVPn1BFYU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vpl34hdNX3RMyrnEPJb4OY--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vqdjLgR9.7lJHFvb1B6otVU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vQjI2OrS6NwyqgmTNmf259U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vQwHafV1cpzVjlZKWztnxf--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vR-49Qi-KC5FFD4w4jIQ-uk-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vRiU7bug9B4rIPskVqHabH--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vt4RVev4DqePZwJMXAjCsa--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vT5-K6xNayw0fLmgAM-nCVE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuAosIC1J3nvCVXxtjUmk7--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v.ueWeMYdRdKR7J9ltIpjfU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuIHyffJYioVKcoWsvlNDO--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vumKEmK.gOiBepnP.tRED-U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vuWbIHJmmPPqyoOKEd1Tfr--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vwNuuavgFMYeIR3aEPYTawU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vWOu22vS3IoineBHSWwocI--- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxbyRHKns2giOX5XqcOujgU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxgA7oV3M3kz.H07CYrBUUE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vXGBz3LsPrRTmV5UlZuI9mE-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vXgee1PhBA42-FH0ZITsO9U-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vyJa6yo.0JXmZY0rn1cCgNU-- 
ECRYPTFS_FNEK_ENCRYPTED.FWb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vZodbRlw.EniW0jpEiuNKN--- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7cpf3KMmlzBkqzDW7zDx7J47VB8vexdNcz1.KudYVaU- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81v7cpf3KMmlzBkqzDW7zDx7K99WewYIBeB05WtZmLIvzY- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vC7LPMmgx6L.-PZWMNQdhfiF7lWP7o9.qRbbdk0l0tNI- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vdqQewYLGv7hKPqZmEZqt04hEe0Ufc2AZuZL12ZdraoA- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vfuBhBIkN9glCCttOXkvvVOiVIarlmkmAzdlGPBstjgE- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vN4sL4cAmS115MtoZReUW4i5tqmlQAPpKqbTZbSnIwGQ- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vOL5-U47E1RCD5oO5YGA4OoK9RCD3YqzwAbYg7tjYzDs- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vSQe4PuPdGuu-wmGAAhhDKzRdnt88aZhIEwjU9ud8Tpc- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vvzNYTXxL69vfstBu1eziSFDPXYM8vx12onsKzBecwkE- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vx96HxKr8PyWBn3FtfIj0D3o6OuRNZ6xfldlqyWZXUV2- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vxLj3AQL80BsaW.SRkS505ZDIZ.jsaEJ-qDuhcYbwzfg- 
ECRYPTFS_FNEK_ENCRYPTED.FXb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vYU0rfZziu9uesAXHiPJLp6jdjo-H2lxBnq4YqmNbhCE- 
ECRYPTFS_FNEK_ENCRYPTED.FYb0Z.iMxDStlUQhgjzQghabz4CM2ub9C81vMjUvTUYHvv1XbJ-CDdUmeRF1rzWc.fagTlsdfA-nuhqLolkMtrv0n9aNkP7a5JQV 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls -A /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs 
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ls /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/wrapped-passphrase 
```

Part 2:
```
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [a48cb073836a00c4] into the user session keyring 
Inserted auth tok with sig [ed55c8c40f15336f] into the user session keyring 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# ^C 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# /mnt/Private 
-bash: /mnt/Private: is a directory 
```

Part 3:
```
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# mount -t ecryptfs /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private/ /mnt/Private 
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded) 
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded) 
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded) 
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded) 
Selection [aes]: 
Select key bytes: 
 1) 16 
 2) 32 
 3) 24 
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y 
Filename Encryption Key (FNEK) Signature [a48cb073836a00c4]: ed55c8c40f15336f 
Attempting to mount with the following options: 
  ecryptfs_unlink_sigs 
  ecryptfs_fnek_sig=ed55c8c40f15336f 
  ecryptfs_key_bytes=16 
  ecryptfs_cipher=aes 
  ecryptfs_sig=a48cb073836a00c4 
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt], 
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong. 

Would you like to proceed with the mount (yes/no)? : yes 
Would you like to append sig [a48cb073836a00c4] to 
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no 
Not adding sig to user sig cache file; continuing with mount. 
Mounted eCryptfs 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# nautilus /mnt/Private 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 
```

Part 4:
```
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# df -h 
Filesystem            Size  Used Avail Use% Mounted on 
aufs                  1.5G   32M  1.5G   3% / 
none                  1.5G  360K  1.5G   1% /dev 
/dev/sdb1             963M  716M  247M  75% /cdrom 
/dev/loop0            661M  661M     0 100% /rofs 
none                  1.5G  128K  1.5G   1% /dev/shm 
tmpfs                 1.5G   96K  1.5G   1% /tmp 
none                  1.5G   92K  1.5G   1% /var/run 
none                  1.5G     0  1.5G   0% /var/lock 
/dev/sdc4             8.5G  2.0G  6.1G  25% /media/7e6f724f-9725-4607-a08b-5f4a02fb356b 
/dev/sdc6             125G   60G   59G  51% /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383 
/dev/sdc5              94G   60G   30G  67% /media/d14d9f09-2775-4222-8333-aae1d49bb7e0 
/dev/sdc2              63G   42G   21G  67% /media/0A9C61789C615EE7 
/dev/sda3              98G   23G   76G  23% /media/OS 
/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private 
                      125G   60G   59G  51% /mnt/Private 
/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.Private 
                      125G   60G   59G  51% /mnt/Private 
root@ubuntu:/media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie# 
```

---

### Post by KIAaze on 2011-02-26
> Perhaps its a problem with encrypted file names?
It looks like it, yes.
You could try playing with the options during the prompt.

However, I noticed another strange thing: Your "FNEK" numbers are not the same as before!
My guess is that you entered the wrong passphrase.

In your previous post, you had:
```
Inserted auth tok with sig [375e8d8580bb4051] into the user session keyring 
Inserted auth tok with sig [c2941b98f4f7b9c6] into the user session keyring 

```

This time, you had:
```
Inserted auth tok with sig [a48cb073836a00c4] into the user session keyring 
Inserted auth tok with sig [ed55c8c40f15336f] into the user session keyring 

```

(*)

Try the FNEK command again with 06199949a6a5dfbfa8bfa626078ee5ab as passphrase (which you got from the unwrap command):
```
ecryptfs-add-passphrase --fnek
```

In fact you should get the same numbers as in .ecryptfs/Private.sig.
Check it with:
```
cat /media/9af3021e-32c8-4bd4-9c10-2a79cd16f383/home/.ecryptfs/jamie/.ecryptfs/Private.sig

```

Then retry mounting with the correct FNEK numbers. :)

(*) Apparently those values get generated by ecryptfs-add-passphrase from the entered passphrase, which can be anything.
The fact that I get 375e8d8580bb4051/c2941b98f4f7b9c6 with your passphrase 06199949a6a5dfbfa8bfa626078ee5ab on my own PC suggests that those are the correct FNEK values.

edit:
I played around a bit and it seems you can mount the encrypted partition with any passphrase (and the corresponding FNEK set). It will just be unreadable unless you use the correct passphrase+FNEK keys.

---

### Post by Spyderkid on 2011-02-26
Do you have the passphrase it gave you when you created the user? (you should have) you need it to unlock it.

---

### Post by bodhi.zazen on 2011-02-26
I have always done it this way :

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Short%20advanced%20way)

with a chroot.

---

### Post by Falc7 on 2011-02-27
Thanks so much guys! Its great to have all my data back!:)

---


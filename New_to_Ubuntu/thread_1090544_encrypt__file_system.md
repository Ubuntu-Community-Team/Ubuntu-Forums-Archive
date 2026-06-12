---
title: "encrypt / file system"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by hammad1337 on 2009-03-08
I have been using ubuntu since 2 years now...recently, i came across the need to encrypt my file system as someone with a live cd came and accessed some personal files in my hd.

I want to avoid this from happening again.

Can I encrypt my / file sytem, including my home directory, but excluding the other partitions mounted in /media/ directory?

Also, I want to do this without re-installing, if possible.

Please reply asap with procedure to encrypt so i can close this security loophole once and for all.

---

### Post by hexanol on 2009-03-08
I personally don't know much about encrypted filesystem (heard of them, that's all) but right now you could go in your BIOS and put a password there. After that, if your HD is your first boot device, it's going to be impossible to boot to another media without the password.

Also, since I guess you use grub as a bootloader, you would also want to put a [password there]("http://www.gnu.org/software/grub/manual/grub.html#password").

---

### Post by Paqman on 2009-03-08
> **hammad1337 said:**
> 
Also, I want to do this without re-installing, if possible.


You'll have to reinstall i'm afraid. I believe full-disk encryption is an option if you install using the Alternate CD. You'll also have to do your partitioning manually to achieve the exact setup that you want, but it shouldn't be overly difficult to do.

---

### Post by hammad1337 on 2009-03-08
I have plenty of space on my hard-disk.

Would it be possible to create an encrypted empty partition and transfer the whole linux "/" as an exact image to the encrypted fs?

What tools would be needed for that?

Also, a BIOS password is not ultimately safe as the HD can be taken out and connected to another PC, same is the case with grub password. But thanks for the suggestions. :)

---

### Post by hexanol on 2009-03-08
Indeed, but it might be better than nothing depending on your "environment".

---

### Post by hyper_ch on 2009-03-08
> **Paqman said:**
> You'll have to reinstall i'm afraid. 

There are ways around it but it's complicated and you can easily break something.

Easiest way is to do full disk-encryption during an installation from the alternate or server cd.

As for other subdirectories in /media --> if they reside on an own partition you don't need to encrypt that. dm-crypt will however only encrypt full partitions.

---

### Post by hammad1337 on 2009-03-08
I m willing to spend time and effort to encrypt my install. If only you point me in the right direction.

Naming dm-crypt as a program to encrypt partitions, is a good first step, thanks for that. :)

---

### Post by hyper_ch on 2009-03-08
there was an article in the C't that gives you the procedure on how to accomplish that in debian. But it's german only.

---

### Post by hammad1337 on 2009-05-03
Can the following method be applied to folders in an NTFS patition as well?
> 
How To: use encrypted directories with ENCFS and FUSE

There is many options out there to encrypt datas on a hard drive. You could either encrypt a whole partition using kernel filesystem or simply encrypt specifics directories on your hard disk.

encfs along with fuse can accomplish this.

This how-to will show how you can easily encrypt a directory on your filesystem.

the tools we are going to use here are:

* fuse

* encfs

encfs allow encrypting virtual filesystem, virtual because you are not going to encrypt a whole partition but simply use a native filesystem such as ext3, reiserfs... A good point is that you do not have to create a new filesystem and define a specific size, but will be able to use as much room left in the existing filesystem you are going to encrypt the directory on.

Now, let install the required packages:

$sudo apt-get install fuse-utils encfs

You need to make sure that your user belong to the fuse group:

$groups

if you see fuse in the response, it is all ok, otherwise, add your normal user to fuse group:

$sudo adduser myuser fuse

Also, the fuse kernel module need to be loaded:

$sudo modprobe fuse

If you want this module to be automatically loaded at boot time, you need to had it to /etc/modules .
Now assume that you want an encrypted directory named /home/myuser/encrypted, the first thing we need to do is to create a virtual mount point: /home/myuser/.encrypted, and the directory it is going to mount on:

$mkdir /home/myuser/.encrypted
$mkdir /home/myuser/encrypted

now, simply mount the filesystem using encfs. If the filesystem is already created, it is only going to prompt for the passphrase decrypting the filesystem, otherwise it will ask you question for creating the filesystem, simply typing ENTER will do a standard configuration which should suit most people.

Well, now mount your filesystem and start editing files.

$encfs /home/myuser/.encrypted /home/myuser/encrypted
$echo "test" > /home/myuser/encrypted/test.txt
$echo "test2" > /home/myuser/encrypted/test2.txt

as you can see, test.txt and test2.txt are created and readable in /home/myuser/encrypted. Now, unmount your encrypted filesystem:

$fusermount -u /home/myuser/encrypted

check the content of /home/myuser/encrypted:

$ls /home/myuser/encrypted

Empty! All the files are in /home/myuser/.encrypted:

$ls /home/myuser/.encrypted

Filenames are encrypted and if their content is not human readable . Now, mount the encrypted directory back:

$encfs /home/myuser/.encrypted /home/myuser/encrypted

Supply the password you defined when creating the filesystem and check the content of /home/myuser/encrypted:

$ls /home/myuser/encrypted
test.txt test2.txt

Your files are back .

Conclusion: This is a pretty simple file encryption, it has the advantage of not being applied to a whole partition so you do not have to create and initialize an encrypted partition, but instead, you are only going to create a directory where you will write your sensitive datas.


---

### Post by nhasian on 2009-05-03
theres three options I can think of.

1) encrypted private directory is probably your easiest solution: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

2) Truecrypt [http://www.truecrypt.org/](http://www.truecrypt.org/)  this is what i use for my /data partition. but you dont have to make a special partition if you dont want to.  you can just encrypt a file and mount it like a disk.  

3) fresh install from Ubuntu AlternateCD, partition the hard disk with LVM Disk Encryption

---


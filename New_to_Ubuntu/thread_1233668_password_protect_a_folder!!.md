---
title: "password protect a folder!!"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by bobigeorge on 2009-08-06
Someone please suggest how to password protect a particular folder in Ubuntu 9.04

---

### Post by super kim on 2009-08-07
you could set the read privileges to only the root user, or just use the encryption.
or set up a new user and then you'll need that password to open the folder.

check this thred

[http://ubuntuforums.org/showthread.php?t=1225684&highlight=password+folder](http://ubuntuforums.org/showthread.php?t=1225684&highlight=password+folder)

---

### Post by rsiddharth on 2009-08-07
Check this link : [http://books.google.com/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide#v=onepage&q=&f=false) 

Head directly to the 123rd page of the book , The information given there may be useful . you don't have to scroll all the way down , just type '123' in the box beside "Contents" and hit enter and your there .

you can also try Truecrypt  , I was using it in Windows to encrypt my personal files .

---

### Post by super kim on 2009-08-07
> **rsiddharth said:**
> Check this link : [http://books.google.com/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide#v=onepage&q=&f=false) 

Head directly to the 123rd page of the book , The information given there may be useful . you don't have to scroll all the way down , just type '123' in the box beside "Contents" and hit enter and your there .


encryption is the safest way, the only issue i have with it is that when you encrypt it takes a long time depending on the size of the file/folder and when you make a change to the folder contents you have to go through the compression/encryption process again, even if you only change one file. its a bit of a bummer but it is the safest way to secure your sensitive files.
if you only want to stop girlfriends finding your porn you could just make the folder hidden or put it in an obscure location. but the link i put on my first post shows you a simple way to set a folder to only open with the root password.

---

### Post by amac777 on 2009-08-07
I use ENCFS to encrypt directories on the fly and it's totally transparent to the user as long as you have mounted the encrypted directory. I found this tutorial:

[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

Also, if you don't like the command line, I have not used it, but there is also a GUI tool which lets you work with ENCFS without using the command line. It's called 'cryptkeeper'.

---

### Post by Ubun2 Us3r on 2009-08-07
you should probably use the encryption that comes with Ubuntu, or get Truecrypt, where you can create an encrypted container and move files into it
You can get true crypt at [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

---

### Post by rsiddharth on 2009-08-07
> **super kim said:**
> encryption is the safest way, the only issue i have with it is that when you encrypt it takes a long time depending on the size of the file/folder and when you make a change to the folder contents you have to go through the compression/encryption process again, even if you only change one file. its a bit of a bummer but it is the safest way to secure your sensitive files.
if you only want to stop girlfriends finding your porn you could just make the folder hidden or put it in an obscure location. but the link i put on my first post shows you a simple way to set a folder to only open with the root password.

I am unanimous with what you have told , since PGP encryption gives you an awesome 2048-bit encryption which is very difficult to crack . One more advantage of using this encryption is that you got to have the " keys " installed in your computer to access the encrypted files - if someone illicitly steals your encrypted file,they will require the "keys " before they would even try cracking !!.

---

### Post by niteshifter on 2009-08-07
> **rsiddharth said:**
> I am unanimous with what you have told , since PGP encryption gives you an awesome 2048-bit encryption which is very difficult to crack . One more advantage of using this encryption is that you got to have the " keys " installed in your computer to access the encrypted files - if someone illicitly steals your encrypted file,they will require the "keys " before they would even try cracking !!.

Whoa there! 2048 bit (or larger) is for Public Key Infrastruce (PKI) uses. When used as an encryption engine you are doing something very different than PKI. As of gnupg 1.4.6 you have available:
3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH
Which offer symmetric keys up to 256 bits (impossible to crack).

The package "seahorse" is a GUI frontend for gnupg and supports file/folder encryption within Nautilus.

Truecrypt is another excellent choice and provides "two factor authentication" - password and keyfile(s).

---

### Post by super kim on 2009-08-07
Ok we can all agree that encryption is the safest way to protect your folders/files.

the OP asked how he could quickly set a password to a folder, and has not specified what level of protection he requires.
i will assume that the OP doesn't need the security of encryption in this case.

open a terminal from applications, accessories. then type...
```
sudo chown -R root:root /passworded_folder
```change 'passworded_folder" to the folder you want to "protect" so i might do "sudo chown -R root:root /home/superkim/Pictures" this sets the access to the root not the user, if you wait a few minutes (if you just entered your root password it will remain open for a few minutes)

to open the folder again you will need to do this
```
gksudo nautilus /passworded_folder
sudo chown -R user:user /passworded_folder
```you can even make a launcher to run that! so once it's set up you only need to click it and enter your root password to access the folder :) you would need to 'lock' it again afterwards.

if your folders contents really is something sensitive like accounts etc then you really should be using encryption already, and if they are really important sensitive files encrypt them back them up then upload them to a free on-line storage site, my friend used to back up all his stuff onto 2 cd's and then he had a fire in his house he lost his hard drive and all the cd back ups too. so you never can be too carefull, however i would make sure your files are encrypted before uploading them.

---

### Post by kpkeerthi on 2009-08-07
[http://tuxtweaks.com/2009/03/create-an-encrypted-folder-in-ubuntu-with-cryptkeeper/]("http://tuxtweaks.com/2009/03/create-an-encrypted-folder-in-ubuntu-with-cryptkeeper/")

---

### Post by scorp123 on 2009-08-07
> **bobigeorge said:**
> Someone please suggest how to password protect a particular folder in Ubuntu 9.04

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by scorp123 on 2009-08-07
> **super kim said:**
>  the OP asked how he could quickly set a password to a folder, and has not specified what level of protection he requires. True. Just to mention ACL's then.

[https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)

[http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

[http://tlug.dnho.net/node/171](http://tlug.dnho.net/node/171)

---

### Post by raven on 2009-08-18
I have a how to issue with cryptkeeper/encfs
          
after all is done and I have an encrypted folder with my files in it


 my question is:
how can I remove this data and not be encrypted anymore ?
 

limitations:
1-encrypted folder is 220GB
2-free space is 10GB


 


 thanks

---

### Post by amac777 on 2009-08-18
Raven, if I understand your question, if you don't want to store the data in encrypted form anymore, it's as simple as mounting your encrypted directory using cryptkeeper (so you can see the files), and then copying them to another (regular) directory on your hardrive. The files will no longer be encrypted in the regular directory.

Once you confirm the files are safe in their new directory, just delete the encrypted directory.

---

### Post by joshuntu on 2009-08-21
hi, i used super kims response to "lock" a folder and now i cant open it again using the camand given, it says that it can't find the folder, i want to delete the folder but it now say i am not allowed, how can i delete or unlock the folder?  i used                    sudo chown -R root:root /passworded_folder
to lock it but when i try and run 

               gksudo nautilus /passworded_folder
  sudo chown -R user:user /passworded_folder


it says it cant find the folder, it could be that i do not know how to type the location in the terminal, it is a folder on my desktop and i am typing gksudo nautilus/home/josh/desktop/foldername 

 help please, thankyou


josh

---

### Post by amac777 on 2009-08-21
On my computer, the Desktop folder has a capital "D". Try:


```
gksudo nautilus/home/josh/Desktop/foldername
```

---

### Post by j.bell730 on 2009-08-21
> **amac777 said:**
> On my computer, the Desktop folder has a capital "D". Try:


```
gksudo nautilus/home/josh/Desktop/foldername
```

Also, put a space between between command and directory:
```
gksudo nautilus /home/josh/Desktop/foldername
```

---

### Post by asn_knight on 2010-05-05
> **super kim said:**
> Ok we can all agree that encryption is the safest way to protect your folders/files.

the OP asked how he could quickly set a password to a folder, and has not specified what level of protection he requires.
i will assume that the OP doesn't need the security of encryption in this case.

open a terminal from applications, accessories. then type...
```
sudo chown -R root:root /passworded_folder
```change 'passworded_folder" to the folder you want to "protect" so i might do "sudo chown -R root:root /home/superkim/Pictures" this sets the access to the root not the user, if you wait a few minutes (if you just entered your root password it will remain open for a few minutes)

to open the folder again you will need to do this
```
gksudo nautilus /passworded_folder
sudo chown -R user:user /passworded_folder
```you can even make a launcher to run that! so once it's set up you only need to click it and enter your root password to access the folder :) you would need to 'lock' it again afterwards.

if your folders contents really is something sensitive like accounts etc then you really should be using encryption already, and if they are really important sensitive files encrypt them back them up then upload them to a free on-line storage site, my friend used to back up all his stuff onto 2 cd's and then he had a fire in his house he lost his hard drive and all the cd back ups too. so you never can be too carefull, however i would make sure your files are encrypted before uploading them.

1)Does this method even refrain from opening the folder from other OS like Windows?

2)How do I make a launcher like that.?

---

### Post by hubertofliege on 2010-07-17
I'd appreciate if someone would explain some of this to me as if I were a child.  I'm finding this all very confusing.  Specific questions:

I would like a folder which, when I double click on it in Nautilus, will ask me for a password, and which will not allow any other means of accessing these files (such as through another program) without entering a password.  Is such a feature built into Ubuntu 10.4?  If not, is there a widely used package which I can download?  Please remember that I'm looking for simplicity.

How much encryption do I need?  I am looking to hide personal thoughts, private financial information, confidential scientific data, and possibly intimate pictures.  I want them to be easily accessible, like a normal folder, however only to me and when I wish to open them so that they cannot be accessed at work or at a repair shop or by me, accidentally.  

I have tried right clicking, then clicking "Encrypt".  I am then asked to choose recipients, and I don't know what this means.  I selected the only option available, "Ubuntu Archive Automatic Filing Key" and then clicked okay.  I was then asked to choose a file format, such as .zip or .tar.  When I double clicked on the new encrypted file, it just opened in an archive reader.  This does not seem like what I am looking for.

I tried following the steps suggested by super kim:
sudo chown -R root:root /passworded_folder
This changed the icon on my folder, but when I double click on it it opens regularly.  I can't see what has changed.

I've seen mentions of TrueCrypt, which sounds promising, however I'd rather not download a new program if there is a simple way to do this within Ubuntu's file system.

I've also seen mention of ACLs, however the information is too technical for me to follow.  This following link has been somewhat helpful, but is also too dense for me:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Please remember that if you give me a command line that will do what I'd like, I won't feel comfortable entering it unless I have an idea what it does, and I won't know what it does unless it is explained in plain English.

Thank you all, btw, for helping.  I'm sorry that I find all of this a bit outside my reach right now.

---

### Post by snip3r8 on 2010-07-17
Why not just compress the file and put a password on the archive?

---

### Post by hubertofliege on 2010-07-19
Thats an option.  However, the point is not just to complete a task, its to learn how to do it right.  I have plenty of workaround options (hide the folders, give them obscure names and locations, change the file extensions so that they can't open unless I add a letter back in, keep them on a separate hard drive, or in a different log in account, download free encryption software), but I'd like to learn the BEST way to do something, if possible.  Its a learning opportunity.

---

### Post by bodhi.zazen on 2010-07-19
> **hubertofliege said:**
> Thats an option.  However, the point is not just to complete a task, its to learn how to do it right.  I have plenty of workaround options (hide the folders, give them obscure names and locations, change the file extensions so that they can't open unless I add a letter back in, keep them on a separate hard drive, or in a different log in account, download free encryption software), but I'd like to learn the BEST way to do something, if possible.  Its a learning opportunity.

This is a FAQ.

The "unix" way is to use permissions and to give each user a unique account. If you wish to share a computer with friends, have them use the guest account.

You then set permissions on your home directory to 700 and files to 600.

QED - all files in your home directory are password protected.

If you need something beyond this, use encryption. If you want a graphical interface, look at cryptkeeper.

---


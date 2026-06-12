---
title: "How to Password protect a folder in ubuntu/mint?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by dihan91 on 2010-08-15
**I am using mint 9 isadora. thanks to linux. my question is, how can i create restriction on accessing a folder in ubuntu/mint? how can I set up a password? like every time anyone wants to open that folder, a password will be needed.**

---

### Post by mike555 on 2010-08-15
In ubuntu I had to install "seahorse-plugins"

---

### Post by ironic.demise on 2010-08-15
> **dihan91 said:**
> **I am using mint 9 isadora. thanks to linux. my question is, how can i create restriction on accessing a folder in ubuntu/mint? how can I set up a password? like every time anyone wants to open that folder, a password will be needed.**

Multiple users and chmod/chown?

In terminal
```
sudo chmod 700 "folder"
sudo chown "user" "folder"
```

Then nobody can access your folder unless logged in as you or through the terminal if they know your password.

(If you don't log out of your account you can always change who owns the folder to another user and just log into the folder as the other account)

For more security you could try scramdisk for linux, it encrypts and password protects files and folders as far as I know...

---

### Post by dihan91 on 2010-08-16
> **mike555 said:**
> In ubuntu I had to install "seahorse-plugins"


what is the sea horse plugin? can u help me learn about it?

---

### Post by TracyO on 2010-10-20
Hi,

Did you ever get this figured out?  I now have the same question.  I attempted to Encrypt the folder, but I can still access all of the files inside without needing a password.

Thanks,
Tracy

---

### Post by ironic.demise on 2010-10-21
> **TracyO said:**
> Hi,

Did you ever get this figured out?  I now have the same question.  I attempted to Encrypt the folder, but I can still access all of the files inside without needing a password.

Thanks,
Tracy

Try accessing it from another PC or user account?
If you are using the built-in Ubuntu encryption it unencrypts it if you log in.

---

### Post by mike555 on 2010-10-21
[http://live.gnome.org/Seahorse](http://live.gnome.org/Seahorse)

---

### Post by ironic.demise on 2010-10-21
> **mike555 said:**
> [http://live.gnome.org/Seahorse](http://live.gnome.org/Seahorse)
 Isn't SeaHorse just a "manager for passwords and keyrings"?
I'm not too sure but SeaHorse seems like it's just a frontend for some of the built-in encryption services, or does it actually produce the encryption process itself?

---

### Post by uRock on 2010-10-21
Changing the permissions as listed earlier is one way to prevent others from seeing the folder from another account. There is also the Private Folder which is an encrypted folder. To create the private folder go here, [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by sgosnell on 2010-10-21
If you really want to protect files, something like Truecrypt is probably a better way to go.  Changing the owner won't protect the files at all, because it's easy to boot from a USB drive and have complete access to everything on the internal drive.  Ecryptfs is another way to do it, but for just individual files or folders, Truecrypt works as well, and is easier to implement.  Just don't forget the password you set on the crypt, because without it there is no way to recover anything.

---

### Post by Legeril on 2010-10-21
I great tip, can anyone explain the details behind these commands?

```
sudo chmod 700 "folder"
sudo chown "user" "folder"
```

ITT people hiding porn :o

---

### Post by ironic.demise on 2010-10-21
> **Legeril said:**
> I great tip, can anyone explain the details behind these commands?

```
sudo chmod 700 "folder"
sudo chown "user" "folder"
```

ITT people hiding porn :o

sudo means "run as superuser/admin"
chmod means "change mode(think?)"
chown means "change owner"

if you own a file you can do what you like with it, which is why root owns most system files and the user doesn't

"mode" determines who can access the file
  User, Group, Other is what the 7, then 0, then 0 stand for.
 7 means read, write and execute whilst 0 mean NO read, write and execute.
You can do something similar with 
```
chmod u +rwx; chmod go -rwx
```
where u stands for user (owner) and go stands for group, other.

a similar but a bit more complicated "ch" command is chattr, type "man chattr" into terminal.


for that point, typing "man chmod" will give you the manual for chmod too.
(press "q" to leave the window)

---

### Post by Legeril on 2010-10-21
> **ironic.demise said:**
> sudo means "run as superuser/admin"
chmod means "change mode(think?)"
chown means "change owner"

if you own a file you can do what you like with it, which is why root owns most system files and the user doesn't

"mode" determines who can access the file
  User, Group, Other is what the 7, then 0, then 0 stand for.
 7 means read, write and execute whilst 0 mean NO read, write and execute.
You can do something similar with 
```
chmod u +rwx; chmod go -rwx
```where u stands for user (owner) and go stands for group, other.

a similar but a bit more complicated "ch" command is chattr, type "man chattr" into terminal.


for that point, typing "man chmod" will give you the manual for chmod too.
(press "q" to leave the window)

thank you thats a really great explaination, I'm assuming you need to be in the directory to access the "folder" or you will need "../folder"?

---

### Post by ironic.demise on 2010-10-21
> **Legeril said:**
> thank you thats a really great explaination, I'm assuming you need to be in the directory to access the "folder" or you will need "../folder"?

It works on files or folders, if you are IN the directory with the file/folder you just chmod -R 700 EXAMPLEDIRECTORY

if you are below the file or folder you can use:
If you are for example in /home/username/pictures you can
chmod -R 700 photos/camera_album
if you are in /home/username/videos but want to change pictures you can
chmod -R 700 /home/username/pictures

I hope that makes sense (You can replace /home/username with "~/" which is a shortcut to /home/username)

-R means recursive, which means it will apply the chmod to the directory and EVERYTHING in it.

---

### Post by ArgusVision on 2010-10-21
If you simply want to restrict access, setting the file permissions as stated earlier is an easy way to handle it. If you are looking to encrypt a "folder" you might try truecrypt. 

Go to the TrueCrypt website. [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
-     There you can download the Trucrypt installer. Be sure to scroll down and select the proper linux tar.gz (Probably 32-bit) Save the file to your machine. You should be able to run it by clicking on it in the "downloads" box, or go to Your home directory > Downloads and double click to run it from there. You will need to select "Run in Terminal", then it will present you with a dialog box that will walk you through the install.
-     After Truecrypt is setup, you should see it in Applications > Accessories > Truecrypt. From here you can configure a file to mount as a "TrueCrypt Volume". (When you're done it will mount to media, like a thumbdrive.) Create an empty file in your home folder. (name it EncryptThis for example)
-     To create this volume, highlight a slot number (at the top), then click "Create Volume" the Wizard will walk you through. You'll probably be best selecting the default values for the first two options.
-     In the Volume Location screen, enter file name you created above (EncryptThis). (DO NOT point to a file you want to keep. It will ERASE it and replace it.) Click NEXT
-     The Defaults on the next page (AES) and RIPEMD-160 are good choices.
Click NEXT. 
-     Enter a Size that will suit your needs (2 GB for example). The drop down on the right will let you select GB by the way. Click NEXT
-     Enter a good strong password. They suggest 20 characters, but you can use less if you want. Click NEXT
-     In this window you select the file system type. If you plan on using this "volume" on any OS other than Linux use FAT. Also keep in mind that not all linux distros/releases can see ext4 either.
-     In the "Volume Format" window, move your mouse around, the more the better. Then click Format. It will warn you again that it will REPLACE the file. Click OK.  Then EXIT.
-     Back in your TrueCrypt window, click on "Select File" and navigate to the file you made earlier. Click "Mount". Enter the password you created for this volume. And click "OK". It should mount to /media/truecrypt1 . Now when you go to "Places" (top panel), you should see TrueCrypt1. Now you can open it and place any file that you want, just like a thumb drive.
-     I'm pretty sure you can use the "Auto Mount" button to have the "volume" auto mount each time you log in, but I haven't tested it yet.

-     Hope This helps. Sorry it's so long, but I wanted to be detailed.

---

### Post by MooPi on 2010-10-21
Bcrypt has always worked well for me. Small command line that is also cross platform compatible with Windows.

---

### Post by TracyO on 2010-10-24
Hmmm... let me explain why I want a password-protected folder, and I'd be up for suggestions on what's the best way to achieve this.  I'm definitely no expert in encryption, so I have no way of knowing which method is most suitable.

Basically, I'm the only user on my computer, and I want to make sure that even if I'm logged in, no one can access the folder that has all of my assorted private information without having a password.   

Thanks!
Tracy

---

### Post by ArgusVision on 2010-10-25
Well, restricting permissions wouldn't quite do if someone were to manage to get on your pc as you. I'm not sure about the "personal folder" mentioned earlier, as I haven't tried it. Truecrypt requires the folder be decrypted and mounted, and can have a separate password for the encryption process.(I know I do...) So, to use a truecyrpt volume they would not only have to get on your pc as you, but have to know your encryption password, and your sudo password to mount the volume.

---

### Post by sTpny on 2012-05-28
Easiest way is to compress the folder and require a password to open the compressed file. Not all compression types support passwords.. zip does though, and another I can't remember.  Once encrypted and compressed, you can brouse the contents just by clicking it and entering the password... no extraction needed. Its easy to do and to use, and your folder is protected from prying eyes.  Remember to delete the original, and don't forget to empty your trash afterwards.   Cheers, and good luck.   .. hope its still relevant... :)

---

### Post by codingman on 2012-05-28
> **ironic.demise said:**
> sudo means "run as superuser/admin"
chmod means "change mode(think?)"
chown means "change owner"

if you own a file you can do what you like with it, which is why root owns most system files and the user doesn't

"mode" determines who can access the file
  User, Group, Other is what the 7, then 0, then 0 stand for.
 7 means read, write and execute whilst 0 mean NO read, write and execute.
You can do something similar with 
```
chmod u +rwx; chmod go -rwx
```
where u stands for user (owner) and go stands for group, other.

a similar but a bit more complicated "ch" command is chattr, type "man chattr" into terminal.


for that point, typing "man chmod" will give you the manual for chmod too.
(press "q" to leave the window)

You got that one right.

---

### Post by overdrank on 2012-05-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


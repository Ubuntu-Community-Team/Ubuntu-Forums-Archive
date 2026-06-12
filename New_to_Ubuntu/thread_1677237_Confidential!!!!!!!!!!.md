---
title: "Confidential!!!!!!!!!!"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-28
i am a btech student living in hostel along with some 200 friends.
i have a laptop which 2 or 3 of my friends very often borrow when they have to play games or watch movies.i have dual boot ubuntu10.10 with windows.i work on ubuntu and so have some confidential files which i want to hide from them...ofcourse its too confidential even to tell them...so can anyone please tell is there any way in ubuntu so  that i can hide those confidential folders?// please help:KS:KS:KS:KS

---

### Post by bapoumba on 2011-01-28
> **neo_aryan said:**
> i am a btech student living in hostel along with some 200 friends.
i have a laptop which 2 or 3 of my friends very often borrow when they have to play games or watch movies.i have dual boot ubuntu10.10 with windows.i work on ubuntu and so have some confidential files which i want to hide from them...ofcourse its too confidential even to tell them...so can anyone please tell is there any way in ubuntu so  that i can hide those confidential folders?// please help:KS:KS:KS:KS

1- Do not let people borrow your equipment ;)
2- Rename the files with a dot (.) as first character, they will be hidden from browsing (weak)
3- Encrypt

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by oldos2er on 2011-01-28
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by Frogs Hair on 2011-01-28
Store on a removable device or take a look at this. [http://www.webupd8.org/2011/01/how-to-really-hide-folders-in-ubuntu.html](http://www.webupd8.org/2011/01/how-to-really-hide-folders-in-ubuntu.html)

---

### Post by [Snc] on 2011-01-28
You could take a look at TrueCrypt, it might seem a bit of a hassle, but is worth the time, since it is powerful encryption and multi OS, so if you keep your "encrypted file" on the windows partition, you can access it from Ubuntu and Windows with TrueCrypt.

---

### Post by sydbat on 2011-01-28
Create limited users for your friends? Then they shouldn't be able to see or access your /home.

Oh, and this...
> **bapoumba said:**
> 1- Do not let people borrow your equipment ;)

---

### Post by Bucky Ball on 2011-01-28
> **Frogs Hair said:**
> Store on a removable device ...

Possibly two if it's that precious. Easy. But also, in some ways, easier to find!

---

### Post by ubudog on 2011-01-28
If it's super confidential, store it in your mind, or on an SD card that you can snap in an instant.

---

### Post by vivek.pandey on 2011-01-28
> **Bucky Ball said:**
> Possibly two if it's that precious. Easy. But also, in some ways, easier to find!

i would rather prefer to have my documents stored on my lapi then on a hard disk..

---

### Post by Bucky Ball on 2011-01-28
> **neo_aryan said:**
> i would rather prefer to have my documents stored on my lapi then on a hard disk..

If it's stored on your laptop it is on a hard disk (unless you have SD, of course). I'm thinking two 4Gb USB thumb drives. You can then keep one in your pocket and the other in a safe! ;)

---

### Post by vivek.pandey on 2011-01-28
> **Bucky Ball said:**
> If it's stored on your laptop it is on a hard disk (unless you have SD, of course). I'm thinking two 4Gb USB thumb drives. You can then keep one in your pocket and the other in a safe! ;)

thanx for your answer
by hard disk i meant external hard disk!!!sorry i was bit ambigous
but i will still stick to the point that i dont wanna it 2 be in any external storage device but rather in my laptop also the size of that folder is around 20gb

---

### Post by vivek.pandey on 2011-01-28
> **oldos2er said:**
> [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

i probably did everything correct 
Installed ecryptfs-utils
 sudo apt-get install ecryptfs-utils 
Setup my private directory
 ecryptfs-setup-private 
Entered my login password, and  choose  generate one.
Recorded both pass phrases in a safe location!!! 
Logedout, and Loged back in 
then typed ~/Private on terminal
i got a folder in my home directory by name Private but it is not at all encrypted..a double click and it shows all contents

so please tell what i did wrong:confused::confused:

---

### Post by oldos2er on 2011-01-28
I don't think you did anything wrong. According to the 'Caveats' section of [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) "By design, data is not kept private to privileged users while the user is logged in." If I were you I would create another user with limited permissions, and let your friends use that, after you log your user out. It would be simple to test Encrypted Private Directory from another user's account, in any case.

---

### Post by vivek.pandey on 2011-01-28
k i created a new user with limited privileges but i am facing a new problem whenever i am switching off my laptop instead of power off i am getting the login screen of the second user(the new one i have created).what the problem might be?

---

### Post by jd2012 on 2011-01-28
> **neo_aryan said:**
> i have dual boot ubuntu10.10 with windows.i work on ubuntu and so have some confidential files which i want to hide from them...


Why cant you just simply let them use the Windows OS? 

If I were in your shoes?

1.) Install the games/applications they INSIST on using in Ubuntu, on Windows. 
2.) Password protect your Ubuntu install via account password (Duh) :lolflag:

And say "Here have fun" (with windows)

Again if you insist on pleasing your friends, install a second version of Linux on the 
machine for them to use all on their own, updated with the apps/games they prefer.

Additionally if they insist on using YOUR install of ubuntu (with the confidential files) perhaps thats the reason why they want to use the pc in the first place ;)

---

### Post by NickJones on 2011-01-28
If you want to keep your documents private, try using Google Docs, stored on the cloud and with SSL encryption you're pretty set.
If you want to just hide your porn collection, use TrueCrypt, it's easy to use, it's got a loveley GUI.

---

### Post by idi0tf0wl on 2011-01-28
Guys, seriously...

Just change the ownership of the files to root:```
chown -R root TOPSECRETFOLDER
```
Unless they know your password, this is all but fail-safe (id est, they will have no way of even opening the containing folder). Then when you need access to the files just ```
gksudo nautilus
``` and go from there. Or be super-cool and rename the main folder with an initial '.' and do what you need to all within a terminal (of course, you could use any combination of these techniques, including making the folder invisible, 'cd'ing into the hidden directory and 'gksudo nautilus'ing from there).

Why did everyone try to make this so much more difficult than it actually is?

---

### Post by ubuntu27 on 2011-01-28
The best _simple_ **encryption** utility that will do its job is [Cryptkeeper]("http://tom.noflag.org.uk/cryptkeeper.html").

It creates a hidden encrypted folder that only you can access when you enter your password. Your friends will never even see that your files exist!

Here are some links on how to use Cryptkeeper:

[http://abhver.blogspot.com/2008/09/private-on-ubuntu-cryptkeeper.html](http://abhver.blogspot.com/2008/09/private-on-ubuntu-cryptkeeper.html)

[http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html](http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html)

---

### Post by vivek.pandey on 2011-01-28
> **idi0tf0wl said:**
> Guys, seriously...


 Or be super-cool and rename the main folder with an initial '.' and do what you need to all within a terminal 

i tried this and found that the folder has dissapeared how to recover it?

---

### Post by jd2012 on 2011-01-28
Ctrl + H  Usually does the trick.

---

### Post by vivek.pandey on 2011-01-28
> **idi0tf0wl said:**
> Guys, seriously...


 Or be super-cool and rename the main folder with an initial '.' and do what you need to all within a terminal 

i tried this and found that the folder has dissapeared how to recover it?

---

### Post by idi0tf0wl on 2011-01-29
> **neo_aryan said:**
> i tried this and found that the folder has dissapeared how to recover it?

Are you familiar at all with your terminal? Say you moved everything into a folder on your Desktop and called the folder ".TOPSECRETFOLDER". This folder will no longer show up in the GUI and can be most easily "seen" with```
ls -a ~/Desktop
```

ls means "list" (as in files and folders) and the -a flag means "all". Running this should show, among whatever else is on your desktop, a folder named ".TOPSECRETFOLDER". Use the command ```
nautilus ~/Desktop/.TOPSECRETFOLDER
```to open Nautilus (your file manager) in that directory. From there you should be able to do what you want.

The only part of this process that changes is if you took my first bit of advice and changed all the files to root ownership, you will need to first start off by logging in as root, and then replace the ~ part with /home/username/, where username is (you guessed it) your username, como así:```
sudo su
nautilus /home/username/Desktop/.TOPSECRETFOLDER
```
Cheers!

---

### Post by vivek.pandey on 2011-01-29
> **idi0tf0wl said:**
> 

ls means "list" (as in files and folders) and the -a flag means "all". Running this should show, among whatever else is on your desktop, a folder named ".TOPSECRETFOLDER". Use the command ```
nautilus ~/Desktop/.TOPSECRETFOLDER
```to open Nautilus (your file manager) in that directory. From there you should be able to do what you want.


 thanx for your help as far as familarity with terminal is considered i know basic commands like ls cat etc but not complex ones
but thanx for your help its working great!!!!!!!:guitar:

---

### Post by vivek.pandey on 2011-01-29
1 more doubt..i have dual boot with windows along with ubuntu.say i wanna do the same with one of my folders in main(the partition in which windows is installed) what might be the nautilus command?

---


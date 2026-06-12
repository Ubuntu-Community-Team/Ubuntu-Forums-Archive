---
title: "How on earth did my home directory get encrypted?"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by tachyonical on 2011-07-07
Sorry for being such a noob. I'm hoping someone will help me understand what I did wrong here.

[LIST=1]
[*]I installed Ubuntu server on an old computer, because I want to learn about Linux and I want to learn about servers.
[*]When I installed, Ubuntu asked me to press a bunch of keys to determine what kind of keyboard I have. It correctly identified that I have a Swedish keyboard.
[*]When I first booted into Ubuntu, it apparently had discarded the information that I have a Swedish keyboard and thought I had an American one.
[*]I googled, and found that I could change the keyboard with *loadkeys*. I also found that I could change the password with *passwd*. I changed the password to fit the new keyboard (I had originally meant the password *ranch()* but it had registered as *ranch*(* since the layout was wrong).
[*]I worked halfway through the [Unix Mages]("http://www.unixmages.com/") book to learn the command line, then shut down for the night.
[*]When I booted back up I found that the keyboard had reset to American. I googled some more and found that I could change it permanently with *dpkg-config keyboard-configuration*, and it worked.
[*]**Weird stuff #1**: I went to home to continue Unix Mages, but shock and horror! Instead of my mage files, it had two files called Access-your-private-data.desktop and readme.txt.
[*]I googled and apparently this happens after encrypting your directory with ecryptfs. But I hadn't even heard of ecryptfs, so why was my home directory encrypted?
[*]I followed the instructions in readme.txt and typed *ecryptfs-mount-private.* It asked for a passphrase.  I tried typing *ranch()*, now that my keyboard had been successfully changed, but it didn't work.
[*]**Weird stuff #2: **As a last resort, I tried typing *ranch*(, *even though I was now in a Swedish keyboard and that password had been changed. It worked! Huh? Either it wanted my old password or it changed my keyboard layout just for that one password prompt. It told me "Your directory has been mounted."
[*]**Weird stuff #3:** Well, it told me that my directory has been mounted, but when I use my newly learned *ls, *it still just lists Access-your-private-data.desktop and readme.txt. The files I made yesterday are still not listed there. :(
[/LIST]
Can anyone help me understand what is going on? I can't understand why this has happened. Thank you for taking the time to read this!

---

### Post by jtarin on 2011-07-07
Maybe [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") will help you sort through some things.

---

### Post by tachyonical on 2011-07-07
Thank you for replying! I read through that page and it looks like this was the part that was applicable to my issue:

**How to Remove an Encrypted Private Directory Setup**

 Perhaps an Encrypted Private Directory is not for you.  To remove this setup: 

[LIST=1]
[*]Ensure that you have moved **all** relevant data out of your ~/Private directory
[*]Unmount your encrypted private directory
[LIST]
[*] $ ecryptfs-umount-private
[/LIST]
 
[*]Make ~/Private writable again
[LIST]
[*] $ chmod 700 ~/Private
[/LIST]
 
[*]Remove ~/Private, ~/.Private, ~/.ecryptfs (**Note: THIS IS VERY PERMANENT**)
[LIST]
[*] $ rm -rf ~/Private ~/.Private ~/.ecryptfs
[/LIST]
 
[*]Uninstall the utilities
[LIST]
[*] $ sudo apt-get remove ecryptfs-utils libecryptfs0
[/LIST]
 
[/LIST]

The ~/Private directory didn't exist, so I skipped to Step #5. I guess it works, but I still don't know how to get at the files I made yesterday. I guess they got deleted at some point, but I have no clue how or why. I'm pretty scared of Linux now if I can just inadvertently ruin everything and then delete all the files just by going through a newbie tutorial and learning ls, cd, pwd, and such. It seems like I need a CS degree or something before I can even touch a Linux system if I'll just mess everything up so easily. :???:

---

### Post by jtarin on 2011-07-07
Just ask before you do something your not sure of. It's not a problem here. That ecryptfs has been a little problematic on my install too. [Here's]("http://linuxcommand.org/learning_the_shell.php") a good primer on the command line. The terminal command "man ecryptfs" will give you more info on this.

---

### Post by tachyonical on 2011-07-07
All I did was go through a beginner's tutorial for the command line, use *passwd *to change the password, and use *dpkg-config keyboard-configuration *to get a Swedish keyboard. Just by doing those very basic things I managed to break the system and delete all the home directory files. Scary. :(

---


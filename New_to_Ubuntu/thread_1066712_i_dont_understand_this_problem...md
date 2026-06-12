---
title: "i dont understand this problem.."
date: 2009-02-11
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-02-11
what does this mean i dont understand :s

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FBFailed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by skymera on 2009-02-11
It looks like apt-get is trying to load packages from CD rom.

Do:

System > Administration > Software Sources

Check your update list, untick the CD rom box and also check third parties.
Close and click "Reload"

---

### Post by lil_kid1333 on 2009-02-11
Hi Skymera i did what you said and now i got this..

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FB

on the third party software theirs a launchpad box ticked do i untick it?

---

### Post by skymera on 2009-02-11
If you don't need it you could untick it.

You're missing the GPG key which basically verifies the source.

Uticking the box will stop the error, or you could find the GPG key on Launchpad.

(I would look, however college has blocked access to Launchpad =X )

---

### Post by lil_kid1333 on 2009-02-11
How do I get the key?? I unticked it and the problem stopped but I guess I want it (don't know for what lol xD )

---

### Post by sisco311 on 2009-02-11
> **lil_kid1333 said:**
> Hi Skymera i did what you said and now i got this..

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FB

on the third party software theirs a launchpad box ticked do i untick it?

Download launchpad-update-final.zip from [http://ubuntuforums.org/showpost.php?p=6638010&postcount=42]("http://ubuntuforums.org/showpost.php?p=6638010&postcount=42").

Extract the archive in your home directory and run it from a terminal:
```
sudo ~/launchpad-update intrepid
```

---

### Post by lil_kid1333 on 2009-02-11
leo@chick3ns-pc:~$ sudo ~/launchpad-update intrepid
sudo: /home/leo/launchpad-update: command not found

I extracted it on my desktop and that came up :s

edit: nevermind i think i got it

---

### Post by skymera on 2009-02-11
Not sure where to get the key. Didn't think Launchpad repositories needed a key.

I believe you need this

```
 sudo ~/Desktop/launchpad-update intrepid 
```

Thats if its on your desktop

---

### Post by lil_kid1333 on 2009-02-11
ok I think I got it this came up

leo@chick3ns-pc:~$ sudo ~/launchpad-update intrepid
Release: intrepid
Please Wait...
OK

thats all I got. It didn't even tell me "congrats succesfully installed" or anything like that >_<

---

### Post by skymera on 2009-02-11
now run

```
 sudo apt-get update 
```

The error should be gone,

---

### Post by lil_kid1333 on 2009-02-11
leo@chick3ns-pc:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done

That came up and no error so everything fine right??

---

### Post by skymera on 2009-02-11
Yes, that's fine now.

horray

---

### Post by lil_kid1333 on 2009-02-11
yey!!! :D Thanks dudes :'D

---

### Post by blade1950 on 2009-04-22
Worked for me too. Thanks Skymera. What's even better is that a newB, I actually understand what you just had us do. Thanks again.

---


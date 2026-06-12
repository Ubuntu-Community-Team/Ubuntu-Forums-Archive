---
title: "Error message"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Campey on 2009-01-17
Hi I am very new to Ubuntu, and in no way am I computer buff so any answers will have to be given in very clear steps.  I have recently put Ubuntu 8.10 on as my OS.  The problem I have is when I try to reload Synaptic Package Manager I get this error message:-

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263 

Hat does it mean and how can I correct it?

Thanks
Paul

---

### Post by taurus on 2009-01-17
It just means you need to install a key for the new wine repo.

Applications -> Accessories -> Terminal
```

wget -q http://wine.budgetdedicated.com/apt/58403026387EE263.gpg -O- | sudo apt-key add -

```

---

### Post by linux_tech on 2009-01-17
In terminal try typing:
```
sudo apt-get update
```

---

### Post by Campey on 2009-01-18
Hi Tourus.

Thanks for your reply.
I followed your advice and got a screen showing:-

campey@campey-laptop:~$ 

Do I type in the line you showed in your reply at $ and press Enter?  Sorry if I appear thick but I have never used this sort of command.  

Thanks Paul

---

### Post by Elfy on 2009-01-18
yes that's right - I would be inclined to paste it if I wasn't sure.

It will want your password - it will not show as you type it, that is normal.

---

### Post by Campey on 2009-01-18
[B]Hi Forestpixie & tourus

I did as you said and this is what I got:-[/B]

campey@campey-laptop:~$ wget -q [http://wine.budgetdedicated.com/apt/58403026387EE263.gpg](http://wine.budgetdedicated.com/apt/58403026387EE263.gpg) -O- | sudo apt-key add -
[sudo] password for campey: 
gpg: no valid OpenPGP data found.
campey@campey-laptop:~$ 

**So I put it in again, I did as Forest pixie suggested and copied & pasted tourus's line.  I the same result:-**

gpg: no valid OpenPGP data found.

[B]So I put put in Linux_tech line from the second post:-
[/B]
sudo apt-get update

This resulted in this:-

campey@campey-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Get: 2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_GB            
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB [1135B]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB [8049B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB [46.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Get: 6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB [27.0kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB [1135B]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB [8049B]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB [46.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Get: 11 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages [1097B]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 167kB in 0s (229kB/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
campey@campey-laptop:~$

[B]The first lot looks like updates.  The last two lines appears to invite me to correct the error by running apt-get update and this will correct the problem. But how do I run apt-update.

What do I do?

Paul[/B]

---

### Post by Elfy on 2009-01-18
I just did it ok with 

```
 wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by Michael.Godawski on 2009-01-18
+1 to forestpixie

works for me too. :)

By the way how did you install wine?

---

### Post by Campey on 2009-01-18
Thanks to you all

It has now worked.  I have no idea why it worked this time and not when I did it the first time.  

In answer to Michael.  I didn't install Wine myself,  Got someone at Computer Support, a local independent computer shop to do it.  

Thanks again for your help

Paul

---


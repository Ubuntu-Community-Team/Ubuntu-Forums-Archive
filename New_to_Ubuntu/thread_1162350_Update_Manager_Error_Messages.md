---
title: "Update Manager Error Messages"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mikodo on 2009-05-17
Hello Everyone,

I have been getting messages similar to below when I use Update Manager.

Today I tried to enter in a 3rd Party PGP Public Key Block for updates with LottaNZB following a thread that I started last nite, that explained in detail how to do it. Now with that, I get even more warnings, when I run updates in Update Manager.

I presently disabled Firestarter, thinking it may involved, but I still get the messages below.

Can anyone tell me what to do?  

Thanks
----------------------------------------------------------------------------

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
---------------------------------------------------------------------------

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B735DB0E93A5BC72Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/http://ppa.launchpad.net/lottanzb/ppa/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/http://ppa.launchpad.net/lottanzb/ppa/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Michael.Godawski on 2009-05-17
Have you tried to un-select the CD as an installation source? (in Administration > Software Sources)

---

### Post by mikodo on 2009-05-17
no, I will try and respond

---

### Post by mikodo on 2009-05-17
Hello,

I un-selected the CD source and deleted. When I ran Update I got a similar message, just with less iformation

.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B735DB0E93A5BC72Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/http://ppa.launchpad.net/lottanzb/ppa/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/http://ppa.launchpad.net/lottanzb/ppa/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Oh,,, Thank you for responding and your post

---

### Post by binbash on 2009-05-17
you need to import the public key for this error : 

.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B735DB0E93A5BC72Failed to fetch [http://ppa.launchpad.net/lottanzb/pp...86/Packages.gz](http://ppa.launchpad.net/lottanzb/pp...86/Packages.gz) 404 Not Found

---

### Post by mikodo on 2009-05-17
Thank you for your post,

I am at a loss though, I thought I had already imported the key for LottaNZB; Or, is something I  need ot set to allow Launchpad to facilitate downloads of LottaNZB?

mikodo

---

### Post by drs305 on 2009-05-17
You are getting 404 error messages for the last three for the following reasons:
The first (second link posted), the deb-src folder doesn't exist on the  server.
The second repeats the address twice in the same line. Highlight the link and you will see [http://.](http://.).. repeated.
The third address doesn't exist either.

If you click on the address and then keep cutting off the last part of the address you will finally get to one that works. For the above cases, you can get to "http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/". If you add any of the remainder of the addresses you link to you will get an error.

Edit your sources.list to remove or modify these entries:
```

gksudo gedit /etc/apt/sources.list

```
If you aren't sure what to edit, just post the file here and we can help.

---

### Post by mikodo on 2009-05-17
no, I am not sure what to do, or what to edit. Following is a copying of what you had written for code in Terminal

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main

---

### Post by drs305 on 2009-05-17
From gedit, what you posted, change the last two lines:
> 
[COLOR="DarkRed"]deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main[/COLOR]


To a single line which reads:
> 
[noparse]deb http://ppa.launchpad.net/lottanzb/ppa/ubuntu hardy main [/noparse]

That should solve the error messages regarding the lottanzb repository. Then save the file and
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mikodo on 2009-05-17
From gedit, what you posted, change the last two lines:
Quote:
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main deb-src [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
To a single line which reads:
Quote:
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
That should solve the error messages regarding the lottanzb repository. Then save the file and
Code:

sudo apt-get update && sudo apt-get upgrade

Thank you,

To be sure I understand your instructions so as to follow properly do I?
Go to Terminal
Run the gedit as before
delete the last 2 lines
add: deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main

Then how do I save the file? By hitting enter, then enter in the last code and hit enter again?


Code

[sudo apt-get update && sudo apt-get upgrade]

---

### Post by drs305 on 2009-05-17
In gedit you go to the top menu, and file, save. As long as you opened the file with "gksudo gedit /etc/apt/sources.list" it should let you save the file.

To run the next set of commands, open a terminal (Applications, Accessories, Terminal) and run the commands. It's best to copy the commands to prevent errors. Or you can just run the updates as you did when you got the errors initially.

---

### Post by mikodo on 2009-05-17
This is what reads now in terminal after (hopefully) following your instructions: (Is this what I want to see?)

****************-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_CA                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release               
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 308B in 1s (279B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B735DB0E93A5BC72
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*****************-desktop:~$

---

### Post by drs305 on 2009-05-17
You have corrected the sources.list errors. Sorry, I thought you had been given the instructions on how to import the public key for the other message.

To import the public key for the ppa repositories (short method):
```

gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72

```

Longer method, if the above doesn't work:
```

gpg --keyserver keyserver.ubuntu.com --recv B735DB0E93A5BC72 
[noparse]gpg --export --armor B735DB0E93A5BC72  | sudo apt-key add -[/noparse]
sudo apt-get update

```

---

### Post by mikodo on 2009-05-17
[QUOTE=drs305;7298686]You have corrected the sources.list errors. Sorry, I thought you had been given the instructions on how to import the public key for the other message.

To import the public key for the ppa repositories (short method):
```

gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72

```

Longer method, if the above doesn't work:
```

gpg --keyserver keyserver.ubuntu.com --recv B735DB0E93A5BC72 
gpg --export –armor B735DB0E93A5BC72  | sudo apt-key add -
sudo apt-get updat

```[/QUOTE;;

I tried them both. The first did not seem to work:
-------------------------------------------------------------------------

mikodo@mikodo-desktop:~$ gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72
gpg: requesting key 93A5BC72 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
**************-desktop:~$ 

 So, I copied the whole second code into a new terninal and recieved:
---------------------------------------------------------------------------
***************-desktop:~$ gpg --keyserver keyserver.ubuntu.com --recv B735DB0E93A5BC72 
gpg: requesting key 93A5BC72 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
*****************-desktop:~$ gpg --export –armor 60D11217247D1CFF | sudo apt-key add -
[sudo] password for mikodo: gpg: WARNING: nothing exported



It did not work either, sorry

---

### Post by drs305 on 2009-05-17
I just tried these commands and they worked for me. For some reason you were unable to connect. Copy the first line into a terminal and press ENTER:

```
gpg --keyserver keyserver.ubuntu.com --recv B735DB0E93A5BC72
```

Enter the second line and hit ENTER:
```
[noparse]gpg --export --armor B735DB0E93A5BC72  | sudo apt-key add -[/noparse]

```

Finally, enter the third line and ENTER:
```
sudo apt-get update
```

 Just copy the commands from this post using CTRL-C. To paste them into a terminal, you must use CTRL-SHIFT-V.

[COLOR="DarkRed"]**Added:** Make sure your editor keeps the "--" before *export* and *armor* and that they aren't changed into a single long dash.[/COLOR]

---

### Post by mikodo on 2009-05-17
mikodo@mikodo-desktop:~$ gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72
gpg: requesting key 93A5BC72 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
mikodo@mikodo-desktop:~$ gpg --export --armor B735DB0E93A5BC72  | sudo apt-key add -
[sudo] password for mikodo: gpg: WARNING: nothing exported

mikodo@mikodo-desktop:~$ sudo apt-get update
[sudo] password for mikodo: 

I just copied and entered each one into terminal by pressing enter as Ctrl c didn't seem to work

---

### Post by drs305 on 2009-05-17
One final suggestion from me. Since you cannot seem to connect to pgp net:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B735DB0E93A5BC72

```

---

### Post by mikodo on 2009-05-17
> **drs305 said:**
> One final suggestion from me. Since you cannot seem to connect to pgp net:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B735DB0E93A5BC72

```


*************-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B735DB0E93A5BC72
[sudo] password for mikodo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com B735DB0E93A5BC72
gpg: requesting key 93A5BC72 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
mikodo@mikodo-desktop:~$ 


When I was setting up Firestarter following Keir Thomas's Book "Beginning Ubuntu", he suggested disabling Ping. Could this be the problem as that is what I did.

Any way, thank you so very much for the expertise, time and effort, put into this by yourself. I will start again from scratch and see if something you told me in your excellent directions was missed by me.


mikodo

---

### Post by mikodo on 2009-05-18
Well, I tried the following code again:```
gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72
```
With Firestarter off, waited a while with nothing happening, then hit enter and received the first WARNING remark.

I tried it again with Firestarter off, and did nothing for a long time, and eventually it came back with the second reading, which I believe means the key has now been installed. 

If this does mean it is installed, will I always have to have my Firestarter off, to receive updates????  Who knows.

If anyone familiar with code reads this, please let me know if the public key is installed, and what I should do with Firestarter to allow upgrading as it becomes available.
----------------------------------------------------------------------------

******************-desktop:~$ gpg --export --armor B735DB0E93A5BC72  | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
mikodo@mikodo-desktop:~$ 

--------------------------------------------------------------------------

******************-desktop:~$ gpg --keyserver subkeys.pgp.net --recv B735DB0E93A5BC72
gpg: requesting key 93A5BC72 from hkp server subkeys.pgp.net
gpg: key 93A5BC72: public key "Launchpad PPA for LottaNZB Development Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

---------------------------------------------------------------------------

My only guess to what the problem was, is that I was too impatient, and should have let the code sit in terminal until it was able to connect with the LottaNZB server.

Here are the results from the Update Manager:
--------------------------------------------------------------------------

Failed to fetch [http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/Release](http://ppa.launchpad.net/lottanzb/ppa/ubuntu/dists/hardy/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---------------------------------------------------------------------------

I hope this means a problem with LottaNZB's Server, not my configuration.

KUDOS, TO drs305, FOR HIS PATIENCE WITH ME..

mikodo


--------------------------------------------------------------------------

---


---
title: "How do I install Java on edubuntu?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Imortify on 2009-11-09
I have been having problems trying to install java, I did manage to extract the .bin i downloaded from the java website. It isn't showing as installed though when I go java -version. When I try to detect java through the website it also says its not installed. Have I missed a step? I am relatively new to linux and don't understand how it all works.

---

### Post by Aemaeth on 2009-11-09
try this instead it will install several restricted packages and make your life easier

open a terminal

applications > accessories > terminal

then type

# sudo apt-get install ubuntu-restricted-extras

you will have to enter your root password and then voila you should now have java installed...

---

### Post by MelDJ on 2009-11-09
you must install the ubuntu-restricted-extras package. See: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Imortify on 2009-11-09
I also tried the method explained at [http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html) but when I got to the apt-get update stage it failed while downloading.

---

### Post by MelDJ on 2009-11-09
whats the error?

---

### Post by Imortify on 2009-11-09
@[I]try this instead it will install several restricted packages and make your life easier

open a terminal

applications > accessories > terminal

then type

# sudo apt-get install ubuntu-restricted-extras

you will have to enter your root password and then voila you should now have java installed...[/I]     

I tried this but it wanted to install off the cd rom drive which we don't have, we also dont have the CD for it.

@*you must install the ubuntu-restricted-extras package. See: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)*

After attempting to add the repository for Medibuntu I got:
failed: Connection timed out.
Retrying.

Was that what I was meant to do?

@*whats the error?*
It attempted to connect to the server and timed out followed by a long series of failed to fetch messages and then:
W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


To me it sounds like a firewall or something is blocking it but I have no idea how to deal with that on edubuntu.

---

### Post by MelDJ on 2009-11-09
are using another package manager (synaptic, software centre)? close them first then only install

---

### Post by Imortify on 2009-11-10
@[I]whats the error?
[/I]I tried restarting the pc and performing the command sudo apt-get update again and it still failed but at the bottom of the failed to fetch messages it had:
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems



I also tried to download java plugins for firefox by going into the java website and using the do I have java? verification to trigger the install missing plugins option. I tried installing all 4 of these plugins but again I got failed to fetch plugins.

I was a happy windows user but having to use ubuntu just makes me want to toss this thing in the trash. I cant believe how frustrating this operating system is to use to perform such basic tasks.

---

### Post by MelDJ on 2009-11-10
could you post the whole output of sudo apt-get update and not just the 2 bottom lines?

---

### Post by Imortify on 2009-11-10
administrator@ubuntu:~$ sudo apt-get update
[sudo] password for administrator: 
Ign cdrom://Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1) hardy/main Translation-en_US
Ign cdrom://Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1) hardy/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
  Could not connect to 172.31.232.250:3128 (172.31.232.250), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                            
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US                 
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US           
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Translation-en_US             
  Unable to connect to 172.31.232.250 3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Translation-en_US           
  Unable to connect to 172.31.232.250 3128:
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
  Could not connect to 172.31.232.250:3128 (172.31.232.250), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
  Unable to connect to 172.31.232.250 3128:
Reading package lists... Done                                                  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 172.31.232.250:3128 (172.31.232.250), connection timed out

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 172.31.232.250:3128 (172.31.232.250), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 172.31.232.250 3128:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by MelDJ on 2009-11-10
this may or may not work.
 i guess this is server related. try changing your software server by going to system-administration-software sources. then change the software server.

---

### Post by Imortify on 2009-11-10
I tried searching for the best server but it came up with no suitable download server was found and to check my internet connection.. well there is nothing wrong with my connection, so I don't understand. It didn't seem to matter which server I picked either.

---

### Post by MelDJ on 2009-11-12
probably your network has a problem it is highly unlikely that all the servers are down at the same time

---


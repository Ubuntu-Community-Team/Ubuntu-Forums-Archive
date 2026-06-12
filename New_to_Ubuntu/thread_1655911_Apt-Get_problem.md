---
title: "Apt-Get problem"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Myglaren on 2010-12-30
Season's greetings Ubuntuers!

For the past few weeks I have had a problem with the computer slowing down considerably and have discovered the cause to be apt-get running continuously after the computer has been running an hour or so.

I appreciate that apt-get is woken up periodically to check for updates and in the past has always done so with no problems arising but now it appears to have gone slightly haywire.
I get a red triangle on the upper taskbar that informs me that my updates are out of synch and a month old but rebooting and running the update manager generally reveals no new updates.
If I try to run update manager without rebooting it fails as apt-get is running and can't be shut down.

It uses between 64-99% of CPU cycles. :shock:

I have tried to kill it but it refuses to die:  "Apt-Get cannot be terminated. Permission refused" or something very similar.
The only way out seems to be to reboot - a bit too Windows for my liking.

I am sure one of you wise people, if not more, will have an answer to this.

Since Ubuntu was released I think that this is the only real difficulty I have experienced that wasn't of my own making.

---

### Post by snowpine on 2010-12-30
Since you seem to be having a little trouble with the applet, let's try updating directly from the command line. Open a terminal (Applications->Accessories->Terminal), copy and paste the commands below, and then copy & paste the output back here so we can take a look for you:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Another thing you can try is to start the Update Manager and change the options so that it does not automatically check for updates, that way you can update manually when you choose.

---

### Post by Myglaren on 2010-12-30
Thanks for the response [b]snowpine[/url]
Updates work OK from the update manager BUT only when the system has recently been rebooted.  Once apt-get starts it won't work.
The triangle reappeared and I clicked on it.  This time it started update manager that said:

[IMG]http://img.photobucket.com/albums/v407/myglaren/Screenshot-1-6.png[/IMG]



> myglaren@Anamorphosee:~$ sudo ap-get update
[sudo] password for myglaren: 
sudo: ap-get: command not found
myglaren@Anamorphosee:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release.gpg [198B]        
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release [31.4kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [1,797B]
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/main i386 Packages [36.5kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [608B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/universe i386 Packages [17.1kB]
Media Change: Please insert the disc labelled                                                                                                                
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive ‘/cdrom/’ and press enter
^C
myglaren@Anamorphosee:~$ 


myglaren@Anamorphosee:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
myglaren@Anamorphosee:~$ ^C
myglaren@Anamorphosee:~$ 

What I would really like is to be able to kill apt-get in these circumstances without the need to reboot.

---

### Post by gmargo on 2010-12-30
> 
Media Change: Please insert the disc labelled                                                                                                                  
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive ‘/cdrom/’ and press enter
You should disable the cdrom in your repository sources.

---

### Post by snowpine on 2010-12-30
> **gmargo said:**
> You should disable the cdrom in your repository sources.

+1

This is under System->Administration->Software Sources.

Once it is disabled, it will force your system to search for updates on the internet instead of the install CD.

---

### Post by Myglaren on 2010-12-30
It generally doesn't ask for the install CD, only when running apt-get from the command line

Oddly enough it has run since doing that without apt-get popping up and slowing things down.

I had done that previously without any improvement but ran it again to collect the data above.

---

### Post by Myglaren on 2010-12-30
There was no Software Sources in the Administration menu but have disabled it in Synaptic.

---

### Post by Myglaren on 2010-12-31
Well, fingers crossed but that seems to have cured it! :)

Machine has been running for several hours and been left idling for a lot of that time and the problem has not reappeared.
Thanks for your assistance

---


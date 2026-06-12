---
title: "upgrade to 11.04 keeps stopping"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by willyconkz on 2011-04-30
Upgrade from update manager fetches and calculates etc. then on file download hangs at file 1369 of 1369. I have tried a dozen times as I suspected server busy but now I have tried alternative server (Aus instead of main), with same result. Hangs at that point and then fails.  Where else can I get that last file or is it some other fault?

---

### Post by willyconkz on 2011-04-30
So, no-one knows anything that might help?
That's a shame.

---

### Post by cdoebbler on 2011-04-30
Similar problem can't seem to update 11.04.

$ Sudo apt-get update

...gets these errors:

fb1@FB-110:~$ sudo apt-get update
[sudo] password for fb1: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                      
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty InRelease                     
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg [489 B]          
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates InRelease                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [23.2 kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages [781 B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                    
Get:6 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:7 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [2,808 B]         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release                                 
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release                                 
  
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release                         
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release                         
  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [14 B]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [14 B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [11.0 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [4,970 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_US                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Fetched 44.1 kB in 1min 1s (712 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by C.C.C.P. on 2011-04-30
Can you post the error message?

---

### Post by willyconkz on 2011-04-30
[I]Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.[/I]


This time it said file 1354 of 1354.
The connection is up, has been all the time and every time. The 'about ubuntu' menu says it is 11.04 installed.
It takes ten or fifteen minutes to go round this circle every time as it recalculates.

---

### Post by willyconkz on 2011-05-01
pretty useless forum then?

---

### Post by willyconkz on 2011-05-01
tried twice more in last hour, using main server and then for a change using update manager selected 'best server'
same ****, sticks on downloading file 1354 of 1354 then aborts
thats it then, back to windows if I can't get help, shame.

---

### Post by willyconkz on 2011-05-02
waste of ******* time then, last try, twice, once to aus server as got desktop prompt to upgrade, same error and again to main server, same error. 

'about' still says natty which it is not.
thanks for all the ******* help NOT
no wonder people give up on this OS

---

### Post by willyconkz on 2011-05-02
jape@jape:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_AU          
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                              
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_AU    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_AU 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_AU 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_AU    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_AU      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_AU 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages
Reading package lists... Done
jape@jape:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jape@jape:~$ sudo apt-get ******
E: Invalid operation ******
jape@jape:~$

---

### Post by beew on 2011-05-02
Why don't you just do a fresh install? It will take only about 20 minutes and save you a lot of troubles afterwards.

I never do upgrades and it is even more pointless to try to trouble shoot a blotched upgrade (unless you're a developer)while you can solve all the problems in 20 minutes with a fresh install.

---

### Post by willyconkz on 2011-05-02
Thanks. 
I don't know how to do that! I guess I could google for natty narwhal then download it. Trouble is I am a pensioner with only wireless BB and don't want to use up more downloads, this has cost me a gigabyte so far and very expensive for me. This **** just shouldn't happen in this day and age.

Would I lose all my changes and folders and programmes I have downloaded if I do a fresh install, it would be like a new OS I suppose?

---

### Post by willyconkz on 2011-05-02
This is definitely an Ubuntu fault, just tried downloading the install as suggested direct from Ubuntu, same thing - starts the download, then nothing despite waiting five to ten minutes. Yet I have downloaded other stuff yesterday and today with no problems including a large GPS map upgrade and programme and music files and used dropbox, all at over 200 kBs which is fast for round here on wireless BB.

---

### Post by beew on 2011-05-02
Hi,

Here is a step by step guide.
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

Now you need to have a working computer and internet connection to download and create a live usb/Cd. Since you are posting on the forum I assume you do have access to these.  The guide assumes the reader uses Windows so it recommends a windows tool to create the live usb in step #2. If you use a Linux machine you can use unetbootin (or the startup disk creator if it is Ubuntu)

In step#4 I suggest use option2 (advanced or manual option)  to create a 3 partition set up. First set aside about 15-20g as your boot partition (mount point /) then a /home partition of whatever size you need to store all your data and settings (mount point /home) Both of these should be formatted as ext4. Finally a swap partition with size about 1.5x ram.

The advantage of a separate /home partition is that next time when you do a fresh install you can keep all your data and settings by using the same partition as /home but without formatting(choose advanced option  and use the same three partition setup but overwriting only the /  partition)

Unfortunately you would have to reinstall all your programs, this may not be a bad thing because upgrade may create conflicts and mess them up or install stuffs you don't want (say you have already OpenOffice upgrade will upgrade OOO and install LibreOffice because it is the default in 11.04 but you need only one) This process would probably take another 20 minutes at most unless you have many third party applications which you have to install manually, but they wouldn't have survived an upgrading anyway.

So in all it may take you about 40 minutes or less to do a fresh install and restore all your programs but it would take  2 hours or more to upgrade not counting the time for customization (which would not survive an upgrade) It will take longer if you have bad internet connections and many things can go wrong during and after upgrade.

As for your data you should always backup your important files before upgrading. I hope you have. I think  the update-manager popup should be disabled by default because it  encourages impulsive upgrading without proper research and backup. It is  dangerous to inexeprienced users.

---

### Post by beew on 2011-05-02
> **willyconkz said:**
> This is definitely an Ubuntu fault, just tried downloading the install as suggested direct from Ubuntu, same thing - starts the download, then nothing despite waiting five to ten minutes. Yet I have downloaded other stuff yesterday and today with no problems including a large GPS map upgrade and programme and music files and used dropbox, all at over 200 kBs which is fast for round here on wireless BB.
 
Try to use a torrent client or use downthemall from firefox, that way you can resume at a later time. The server is probably busy or down, it happens.

---

### Post by willyconkz on 2011-05-02
Well it has been three days trying and lots of wasted megabytes! I have had similar problems with Ubuntu upgrades before so I am very disappointed. I have since changed machines/OS/internet service provider and still get the same problems. It is definitely a fault if the OS says it is already 11.04 but the upgrade keeps coming up and it is certainly NOT yet 11.04.

Thank you for taking the time to explain another way how to do it. The Ubuntu server is still not responding. I shall try a 'torrent' later on a friends machine, they are not allowed on this one. This is so time wasting and frustrating and I am really unhappy to still get such faults after a year or more. I emailed all my hobby and work lists about this and found ALL the people that got Ubuntu after I suggested to get Ubuntu a couple of years back have since gone back to Win and even paid for Win7 because it is *easier*. I may have to follow them if this attempt doesn't work. Time is too valuable to waste like this for many working people. I have a bit of time more then them but cannot take the lead in this because of faults and problems and incompatibilities with devices.
I don't use OO as it always froze and locked up, yet Abiword works fine, no problems ever. I do have all my pics and music and docs backed up, thanks, but would have to download* lots* of software I have gathered over time which is bloody annoying!
Again thanks.

---


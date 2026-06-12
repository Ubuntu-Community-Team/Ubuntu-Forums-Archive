---
title: "Problem with Synaptic Package manager and Update Manager"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by highflie on 2011-06-08
Hi all,

I use Lucid Lynx on my Laptop and I have been impressed by the OS. But now I have run into a problem.

When I was using my laptop, it shut down suddenly and during restart it said there were errors in /tmp folder which was fixed during Boot. 

However, when I opened Update Manager, there was an error saying

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package      information.

Please report this bug against the 'update-manager' package and  include the following error message:

'E:Encountered a section with no Package: header, E: Problem with  MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.' 
[/B]

Then I opened Synaptic Package manager, where I saw this message

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
[/B]

When I typed the command in the terminal, I got this message

[B]lalit@lalit:~$ sudo dpkg --configure -a
[sudo] password for lalit: 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 5:
 missing package name [/B]

What exactly is the problem here and what should I do to resolve it?

Thanks in Advance.

---

### Post by jtarin on 2011-06-08
```
sudo dpkg --clear-avail
```  ```
sudo apt-get update
```

---

### Post by highflie on 2011-06-08
Thank you for your reply! I typed the above commands but the problem still persists. This is the result from the Terminal

[B]lalit@lalit:~$ sudo dpkg --clear -avail
[sudo] password for lalit: 
dpkg: unknown option --clear

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
lalit@lalit:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release.gpg                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release                         
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages                     
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,218B]                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources                      
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [764B]                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Sources               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Sources             
Fetched 5,071B in 16s (309B/s)                                                 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/B]

When I opened the Update Manager and the Synaptic Package Manager, the same error message as given in my previous post was displayed.

---

### Post by Rubi1200 on 2011-06-08
Hi,

please try these commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Let us know if this resolves the issue.

---

### Post by jtarin on 2011-06-08
There should be a backup of the file in question.[Read this]("http://askubuntu.com/questions/29722/how-do-i-fix-a-corrupted-var-lib-dpkg-status") on how to check and manipulate.

---

### Post by highflie on 2011-06-14
Hey,
I am sorry for the late reply! 
@Rubi: This was what I got:

[B]
lalit@lalit:/media/Learn/IISc/Hole Cutting/1$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for lalit: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
lalit@lalit:/media/Learn/IISc/Hole Cutting/1$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]         
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg [189B]                    
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.4kB]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN   
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Get:8 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Get:9 [http://dl.google.com](http://dl.google.com) stable Release [1,351B]                             
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release [57.2kB]                     
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get:12 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Get:15 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,211B]                      
Get:16 [http://dl.google.com](http://dl.google.com) stable/main Packages [766B]                        
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages [502kB]        
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B] 
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources [194kB]         
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]  
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages [203kB]    
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources [74.8kB]    
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB] 
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources [5,061B]  
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Packages [194kB]       
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Packages [14B]   
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Sources [58.5kB]       
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Sources [14B]    
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Packages [71.5kB]  
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Sources [21.3kB]   
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Packages [4,555B]
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Sources [1,745B] 
Fetched 12.5MB in 58s (212kB/s)                                                
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/B]

The problem still persists :(

---

### Post by Rubi1200 on 2011-06-14
Did you run the command suggested from the error message?

I would start there:

```
sudo dpkg --configure -a

sudo apt-get update
```

---

### Post by highflie on 2011-06-14
Yes, that was the first thing I did. As I had mentioned in my first post on this thread I got the following error

[B]

lalit@lalit:/$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 5:
 missing package name

[/B]

---

### Post by Rubi1200 on 2011-06-15
Did you check the information in the link jtarin provided?

---

### Post by ExileAmongYou on 2011-06-15
I just noticed that when you ran this command:
```
sudo dpkg --clear-avail
```
you accidentally put a space between --clear and -avail where there should not have been one. Might be worth trying that again?

---

### Post by michael_j on 2011-06-15
error messages - any idea what's happening?

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Rubi1200 on 2011-06-15
> **michael_j said:**
> error messages - any idea what's happening?

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
Hi and welcome to the forums :-)

This is not really the same problem and the staff do not like it when people hijack threads. In future, please start your own thread to deal with problems. You are also more likely to get a response if you do.

That said,

open a terminal and run these commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

This should fix the issue. If it does not, then please start a new thread outlining the problem and the steps you took to try and resolve it.

Thanks.

---


---
title: "Ubuntu Software Center Error"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by PizzaLover101 on 2011-06-22
Trying to install software from the Ubuntu Software Center, I keep getting the same error:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

Being new to ubuntu, I don't know what to do. Any help?
Thanks!

---

### Post by iclestu on 2011-06-22
> **PizzaLover101 said:**
> Trying to install software from the Ubuntu Software Center, I keep getting the same error:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

Being new to ubuntu, I don't know what to do. Any help?
Thanks!

try 

```
sudo dpkg --configure -a
```

then

```
sudo apt-get install -f
```

---

### Post by sanderd17 on 2011-06-22
can you fire up a terminal and execute
```

sudo apt-get update
sudo apt-get upgrade

```

If you get any errors, show them here (and please use CODE tags for your post, click on the # sign in edit mode)

---

### Post by PizzaLover101 on 2011-06-22
That seemed to work, thank you!

---

### Post by benjaminblaqk on 2011-10-08
when I try this, I get a message saying dpkg status database is locked by another process. Any idea how to fix that?

---

### Post by sanderd17 on 2011-10-08
> **benjaminblaqk said:**
> when I try this, I get a message saying dpkg status database is locked by another process. Any idea how to fix that?

The way that always works: reboot.

Most of the times, a logout is enough, or even killing some processes.

---

### Post by dking98 on 2011-12-14
I get this error:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 248, in _process_transaction
    self.commit_packages(trans, *trans.packages)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 308, in commit_packages
    self._check_obsoleted_dependencies(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 632, in _check_obsoleted_dependencies
    self._resolve_depends(trans, resolver)
NameError: global name 'resolver' is not defined

I tried the fixes you gave but it did not help! i did not get any errors in terminal! How should i fix this?

---

### Post by sanderd17 on 2011-12-14
> **dking98 said:**
> I get this error:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 248, in _process_transaction
    self.commit_packages(trans, *trans.packages)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 308, in commit_packages
    self._check_obsoleted_dependencies(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 632, in _check_obsoleted_dependencies
    self._resolve_depends(trans, resolver)
NameError: global name 'resolver' is not defined

I tried the fixes you gave but it did not help! i did not get any errors in terminal! How should i fix this?

You did try a reboot after that right?

Can I see the output of all those commands? Even if they don't contain errors.

---

### Post by naman1 on 2012-03-13
Hello SANDERD17.

I am **getting the same problem** as described by PizzaLover101.

while I am installing updates using Update Center, I am getting

+++++==========+++++
     ERROR-Description
+++++==========+++++
An handleable error occurred

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:Method  has died unexpectedly!, E:Sub-process  returned an error code (100), E:Method /usr/lib/apt/methods/ did not start correctly

+++++==========+++++
END of  ERROR-Description
+++++==========+++++
[COLOR=Red][B][FONT=Book Antiqua]
After that I have run commands:[/FONT][/B][/COLOR]
[COLOR=Blue]_(1st command)_[/COLOR]

naman@naman:~/Desktop$** sudo apt-get update**
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                                                                                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                                                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                                                                                          
Ign [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge InRelease                                                                                                             
Ign [http://download.webmin.com](http://download.webmin.com) sarge InRelease                                                                                                                                   
Hit [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge Release.gpg                                                                                                 
Ign [http://live.debian.net](http://live.debian.net) etch InRelease                                                                                                                                        
Hit [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge Release                                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                                                                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                                                                                                          
Ign [http://live.debian.net](http://live.debian.net) etch Release.gpg                                                                                                                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]                                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                                                                       
Hit [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge/contrib amd64 Packages                                                                                                
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                                                                                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                                                                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                                                                                        
Ign [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge/contrib TranslationIndex                                                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages                                                                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex                                                                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                                                                                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [39.8 kB]                                                                                                                
Ign [http://live.debian.net](http://live.debian.net) etch Release                                                                                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                                                                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                                                                         
Ign [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge/contrib Translation-en_US                                                                                             
Ign [http://live.debian.net](http://live.debian.net) etch/main TranslationIndex                                                                                                                            
Ign [http://webmin.mirror.somersettechsolutions.co.uk](http://webmin.mirror.somersettechsolutions.co.uk) sarge/contrib Translation-en                                                                                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                                                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US                                                                                                                 
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty InRelease                                                                                                                                
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates InRelease                                                                                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                                                                                   
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty Release.gpg                                                                                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [92.2 kB]                                                    
Get:4 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates Release.gpg [198 B]                                                                                     
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty Release                                                                                                                      
Get:5 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates Release [39.8 kB]                                                                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US                                                                                                
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en                                                                                                   
Err [http://live.debian.net](http://live.debian.net) etch/main amd64 Packages                                                                                           
  404  Not Found
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release                                                                                                                                     
Ign [http://live.debian.net](http://live.debian.net) etch/main Translation-en_US                                                                                                                           
Ign [http://live.debian.net](http://live.debian.net) etch/main Translation-en                                                                                                                              
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib amd64 Packages                                                                                                                      
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib TranslationIndex                                                                                                                    
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/main Sources                                                                                                                              
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/restricted Sources                                                                                                                        
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/universe Sources                                                                                                                          
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/multiverse Sources                                                                                                                        
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/main amd64 Packages                                                                                                                       
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/restricted amd64 Packages                                                                                                                 
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/universe amd64 Packages                                                                                                                   
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/multiverse amd64 Packages                                                                                                                 
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/main TranslationIndex                                                                                                                     
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/multiverse TranslationIndex                                                                                                               
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/restricted TranslationIndex                                                                                                               
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/universe TranslationIndex                                                                                                                 
Get:6 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/main Sources [154 kB]                                                                                                           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]                                                                                                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [21.9 kB]                                                                                                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [1,628 B]                                                                                                     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [280 kB]                                                                                                    
Get:11 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/restricted Sources [753 B]                                                                                                     
Get:12 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/universe Sources [41.4 kB]                                                                                                     
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US                                                                                                                   
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en                                                                                                                      
Get:13 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/multiverse Sources [3,107 B]                                                                                                   
Get:14 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/main amd64 Packages [438 kB]                                                                                                   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]                                                                                                
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [76.5 kB]                                                                                               
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [3,524 B]                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                                                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                                                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                                                                                                          
Get:18 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/restricted amd64 Packages [838 B]                                                                                              
Get:19 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/universe amd64 Packages [139 kB]                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US                                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en                                                                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                                                                            
Get:20 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [6,368 B]                                                                                            
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/main TranslationIndex                                                                                                             
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                                                                                                       
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/restricted TranslationIndex                                                                                                       
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/universe TranslationIndex                                                                                                         
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/main Translation-en_US                                                                                                                    
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/main Translation-en                                                                                                                       
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/multiverse Translation-en_US                                                                                                              
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/multiverse Translation-en                                                                                                                 
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/restricted Translation-en_US                                                                                                              
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/restricted Translation-en                                                                                                                 
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/universe Translation-en_US                                                                                                                
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty/universe Translation-en                                                                                                                   
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/main Translation-en_US                                                                                                            
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/main Translation-en                                                                                                               
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/multiverse Translation-en_US                                                                                                      
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/multiverse Translation-en                                                                                                         
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/restricted Translation-en_US                                                                                                      
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/restricted Translation-en                                                                                                         
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 1,339 kB in 53s (25.2 kB/s)
[COLOR=Blue][B] W: Failed to fetch [http://live.debian.net/debian/dists/etch/main/binary-amd64/Packages](http://live.debian.net/debian/dists/etch/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.[/B][/COLOR][COLOR=Blue] [/COLOR]naman@naman:~/Desktop$ \


_[COLOR=Blue](2nd Command)[/COLOR]_
naman@naman:~/Desktop$ [COLOR=SeaGreen]**sudo apt-get upgrade **[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data-partner apport apt apt-transport-https apt-utils aptdaemon ca-certificates flashplugin-installer gwibber language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libmysqlclient16 light-themes mobile-broadband-provider-info
  multiarch-support mysql-common python-httplib2 python-launchpadlib python-pam software-center tzdata ubuntu-docs ubuntu-sso-client ubuntuone-control-panel
[B][COLOR=Blue]31 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly[/COLOR][/B]
naman@naman:~/Desktop$ 


And then again I tried to install using UPDATE CENTER.
but still getting same errors.

what is the problem ??

---

### Post by sanderd17 on 2012-03-13
How did you get debian lines in your sources?

Go the the software sources in the software center, and remove everything that isn't "natty". So all the debian (sarge and etch) lines and all the maverick lines (you are using natty right?).

Then try those commands again (and give the output).

When your aptdeamon or apt is already from debian, and not from Ubuntu, there is a chance you will have to recompile the whole thing to get it working. This would be more work than just re-installing Ubuntu. So I can guarantee nothing that it will work.

---

### Post by naman1 on 2012-03-26
Hello Sanderd,

can you tell me, **how can I remove** "_other lines from software center_" ?

---

### Post by sanderd17 on 2012-03-26
By going to the software center -> edit (I think) -> Software sources

---

### Post by naman1 on 2012-05-23
Hello [sanderd17]("http://ubuntuforums.org/member.php?u=742644")

How can I remove  everything that isn't "natty" from the
' software center ' ?

---

### Post by naman1 on 2012-05-23
Hey [sanderd17]("http://ubuntuforums.org/member.php?u=742644")

I have gone through the
" software center -> edit (I think) -> Software sources "

but I do not know.. which lines I should remove.

there are 5 TABS.

Ubuntu Software
Other Software
Updates
Authentication
Statistics

from above 5,
I know that I have to remove from these 3, but exactly do not know from which 3 ?
(1)Ubuntu Software
(2)Other Software
(3)Updates

would you tell me how can I remove " non-natty " lines ?

---


---
title: "Public keys"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-01-02
I have been reading about public key errors and trying to fix them by advise from this web site,
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/](http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)
 but I can't seem to make this work, I followed the directions and still get tons of errors can you tell me what I am doing wrong? This seems so dumb if keys are needed why isn't an option put in to get them? Without all this hassle. I am putting below the terminal output, thanks
```
gn cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/mcmcanulty@Gateway:~$ sudo apt-get update
Iain Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Hit http://download.virtualbox.org karmic Release                              
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:2 http://dl.google.com testing Release.gpg [189B]                          
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://dl.google.com testing/non-free Translation-en_US                    
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Get:3 http://dl.google.com stable Release [2,540B]                             
Hit http://archive.canonical.com jaunty Release.gpg                            
Get:4 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://archive.getdeb.net karmic-getdeb Release.gpg                        
Ign http://archive.getdeb.net karmic-getdeb/apps Translation-en_US             
Ign http://deb.playonlinux.com karmic Release.gpg                              
Ign http://deb.playonlinux.com karmic/main Translation-en_US                   
Hit http://archive.canonical.com karmic Release                                
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://wine.budgetdedicated.com karmic Release.gpg                         
Ign http://wine.budgetdedicated.com karmic/main Translation-en_US              
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Get:5 http://dl.google.com testing Release [2,513B]                            
Hit http://us.archive.ubuntu.com jaunty-backports Release.gpg                  
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:6 http://dl.google.com stable/main Packages [867B]                         
Hit http://archive.canonical.com jaunty Release                                
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US       
Get:7 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:8 http://deb.playonlinux.com karmic Release [1,723B]                       
Ign http://wine.budgetdedicated.com karmic Release                             
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://archive.getdeb.net karmic-getdeb Release                            
Get:9 http://dl.google.com stable/non-free Packages [1,010B]                   
Hit http://packages.medibuntu.org karmic Release                               
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://deb.playonlinux.com karmic/main Packages                            
Ign http://wine.budgetdedicated.com karmic/main Packages                       
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://us.archive.ubuntu.com jaunty-backports Release                      
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Get:10 http://dl.google.com testing/non-free Packages [793B]                   
Hit http://archive.canonical.com jaunty/partner Sources                        
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://archive.getdeb.net karmic-getdeb/apps Packages                      
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Ign http://deb.playonlinux.com karmic/main Packages                            
Ign http://wine.budgetdedicated.com karmic/main Packages                       
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Get:11 http://ppa.launchpad.net karmic Release [66.0kB]                        
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://deb.playonlinux.com karmic/main Packages                            
Err http://wine.budgetdedicated.com karmic/main Packages                       
  404  Not Found
Ign http://ppa.launchpad.net karmic Release                          
Ign http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Get:12 http://ppa.launchpad.net karmic Release [66.0kB]             
Hit http://ppa.launchpad.net karmic Release    
Ign http://ppa.launchpad.net karmic Release                            
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources     
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Hit http://us.archive.ubuntu.com jaunty-backports/main Packages     
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-backports/universe Packages
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Hit http://us.archive.ubuntu.com jaunty-backports/main Sources      
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-backports/universe Sources
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
Fetched 8,718B in 1s (4,554B/s)
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
cmcanulty@Gateway:~$ 
```

---

### Post by cmcanulty on 2010-01-02
Then I tried this method
[http://indlovu.wordpress.com/2009/07/02/better-ppa-fixkey-method/](http://indlovu.wordpress.com/2009/07/02/better-ppa-fixkey-method/)
and still I get the same errors
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Elfy on 2010-01-02
First have you added the script and run it? Your terminal ouput doesn's how it.

I've successfully done it with this information - [http://ubuntuforums.org/showpost.php?p=6626153&postcount=4](http://ubuntuforums.org/showpost.php?p=6626153&postcount=4)

So for the first NO_PUBKEY 5A16033A9A6FE242
```
gpg --keyserver keyserver.ubuntu.com --recv 9A6FE242
gpg --export --armor 9A6FE242 | sudo apt-key add -
```

Replace with 3A258030 for the second.

---

### Post by cmcanulty on 2010-01-02
I saved the script under /usr/bin/fixkey, then I made it executable, but I am not sure how to run it and I am not sure what numbers to fill in for each key, I was just copying the key numbers that appear in the error from when I try to update I have no idea where the following code comes from or how I am supposed to l know what code to type in the terminal as that was never explained for example where did this come from in the thread you referenced, thanks 
gpg --keyserver keyserver.ubuntu.com --recv 8670a035
Now I tried all the code in your referenced thread and still get the same error messages, this is really frustrating I hope I am not messing up the system by all these failed attempts

---

### Post by Elfy on 2010-01-02
Run it with ```
fixkey
```

Not working for me either ... as luanchpad-update from /usr/local/bin

But that said in Karmic you can 

```
sudo add-apt-repository ppa:nameofppa
```

which will do all you need to.

---

### Post by cmcanulty on 2010-01-02
still getting these errors
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/nameofppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by cmcanulty on 2010-01-02
Here is the terminal output and I did run fixkey before nothing I try seems to fix this I can post a copy of /etc/apt/sources.list if that would help I still am not sure of what to enter for a key, is it the number that comes up on the update error or something else?
> ```
cmcanulty@Gateway:~$ fixkey
[CODE]please input your key
 5A16033A9A6FE242GPG
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg &#8211;recv-keys &#8211;keyserver keyserver.ubuntu.com 5A16033A9A6FE242GPG
usage: gpg [options] [filename]
cmcanulty@Gateway:~$ fixkey
please input your key
8F66051A3A258030
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg &#8211;recv-keys &#8211;keyserver keyserver.ubuntu.com 8F66051A3A258030
usage: gpg [options] [filename]
cmcanulty@Gateway:~$ sudo add-apt-repository ppa:launchpad.net karmic
Error: need a repository as argument
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 

```
[/CODE]

---

### Post by slakkie on 2010-01-06
```

function add-key() {
    keyserver=keyserver.ubuntu.com
    [ -z "$1" ] && echo "Key missing" 1>&2 && return 1
    sudo apt-key adv --keyserver $keyserver --recv-keys $1
}

```

Although I like to use the following keyserver: wwwkeys.eu.pgp.net

Now you can do add-key KEYID and done.

---

### Post by cmcanulty on 2010-01-06
I guess I'm just dumb but where is the key I add? I did your code and got this
```
cmcanulty@Gateway:~$ function add-key() {
>     keyserver=keyserver.ubuntu.com
>     sudo apt-key adv --keyserver $keyserver --recv-keys $1
> }
cmcanulty@Gateway:~$ add-key
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 

```
At the website [http://wwwkeys.eu.pgp.net/](http://wwwkeys.eu.pgp.net/) I am not sure what to put in I tried ubuntu karmic and got this but not sure what part is the key
pub  1024D/7FE233FB 2009-11-08 ydioma2005 (FireGPG su firefox 3.5 su ubuntu 9.10 Karmic Koala) <ydioma2005@gmail.com>

pub  1024R/2D615F5D 2009-09-25 Launchpad vdrdevel-ubuntu-karmic

---

### Post by slakkie on 2010-01-06
> **cmcanulty said:**
> I guess I'm just dumb but where is the key I add? I did your code and got this
```
cmcanulty@Gateway:~$ function add-key() {
>     keyserver=keyserver.ubuntu.com
>     sudo apt-key adv --keyserver $keyserver --recv-keys $1
> }
cmcanulty@Gateway:~$ add-key
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 

```

add-key KEYID, eg add-key 47389257198fjkfshjk

i've updated the function with a small help.

---

### Post by cmcanulty on 2010-01-06
OK but the question is because I need several keys where do you get the key number? I tried the one you gave above and still get the no key errors
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/nameofppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nameofppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by slakkie on 2010-01-06
You see the message:

<blaat>: NO_PUBKEY 8F66051A3A258030

That last bit is the KEYID: 8F66051A3A258030

---

### Post by cmcanulty on 2010-01-06
OK I had tried that first but had included the letters at end of key number so that is solved.Thanks very much, this is one of the few things that seems very complicated and I have no clue of where the code I typed in came from .I am still getting a long error message about missing things can someone explain this error? I can't find that on the software list and am unsure whether I download it somewhere or what
Failed to fetch [http://ppa.launchpad.net/nameofppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nameofppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)

---

### Post by mc4man on 2010-01-06
What's the point of trying to add keys for 404 addresses

I'd just delete those sources and if some of what they did provide is still wanted then add the proper karmic sources

(System -> Admin. -> software sources -> third party, and or edit your sources.list

Ex.
wine - referenced [here]("http://www.winehq.org/download/deb")
```
ppa:ubuntu-wine/ppa
```

amule - [here]("https://launchpad.net/~amule-releases/+archive/ppa")
```
ppa:amule-releases/ppa
```

chmsee - available in synaptic, no ppa needed, if one even exists anymore

nameofppa - that's here (in other words, nowhere

---

### Post by cmcanulty on 2010-01-07
Thanks, I guess the problem is I don't understand the process. I looked all through my sources and couldn't find the one with an error message. Also I am unsure- do I check or uncheck the sources that say disabled on upgrade to karmic, ie, is a check disable yes or is check disable no. ? That is like a double negative.  I just don't  want to disable the wrong things and then not get security updates.thank you for your patience on this.

---

### Post by slakkie on 2010-01-07
Have a look in /etc/apt/sources.list.d, you will most probably find some files in that directory.

---

### Post by mc4man on 2010-01-07
Well look at the 2 screens from System -> Admin..->  Software Sources -> Other Software.
screen one shows some ppa's, I'm going to disable 1 (wine) by just unchecking it, the other one I'll remove by highlighting it (chromium) and then clicking 'remove'
I then click close and 'reload' in the pop up that follows.

screen 2 shows result, the wine ppa is disabled, the  chromium ppa is gone 

You could also  post the results of these 2 commands

```
ls /etc/apt/sources.list.d/*.list
```

```
cat /etc/apt/sources.list
```

---

### Post by cmcanulty on 2010-01-08
Ok here is the output, is there a tutorial for this? I have searched quite a bit with no luck. I am maintaining 8 Ubuntus at our library and so try to understand all the processes, this is the most difficult so far to me. I need to avoid error signals at library or people get worried
```
cmcanulty@Gateway:~$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/ailurus.list
/etc/apt/sources.list.d/amule.list
/etc/apt/sources.list.d/chmsee.list
/etc/apt/sources.list.d/chromium.list
/etc/apt/sources.list.d/getdeb.net.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google.list
/etc/apt/sources.list.d/google-stable.list
/etc/apt/sources.list.d/google-unstable.list
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/mscore-ubuntu-mscore-stable-karmic.list
/etc/apt/sources.list.d/nameofppa-ppa-karmic.list
/etc/apt/sources.list.d/pdfmod.list
/etc/apt/sources.list.d/playonlinux.list
/etc/apt/sources.list.d/scrawl-ppa-karmic.list
/etc/apt/sources.list.d/ubun-student-ppa-karmic.list
/etc/apt/sources.list.d/ubuntu-boot-ppa-karmic.list
/etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-karmic.list
/etc/apt/sources.list.d/ubuntu-x.list
/etc/apt/sources.list.d/winehq.list
/etc/apt/sources.list.d/wine.list
cmcanulty@Gateway:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's

## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/arzajac/ppa/ubuntu karmic main
deb http://packages.medibuntu.org/ karmic free non-free

deb http://packages.medibuntu.org/ karmic free non-free
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
cmcanulty@Gateway:~$ 
```

---

### Post by plucky on 2010-01-08
> Failed to fetch [http://ppa.launchpad.net/amule-relea...86/Packages.gz](http://ppa.launchpad.net/amule-relea...86/Packages.gz) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/chmsee/jaun...86/Packages.gz](http://ppa.launchpad.net/chmsee/jaun...86/Packages.gz) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/nameofppa/p...86/Packages.gz](http://ppa.launchpad.net/nameofppa/p...86/Packages.gz) 404 Not Found

```
/etc/apt/sources.list.d/amule.list
/etc/apt/sources.list.d/chmsee.list
/etc/apt/sources.list.d/nameofppa-ppa-karmic.list

```

Those three do not have karmic repositories,that is why you are getting the 404 Not found errors.Delete the .list files in /etc/apt/sources.list.d/ directory and see if that fixes your problem.

You can use "sudo rm" command but be careful as this command is dangerous if you don't know what you are doing. Or use ```
gksudo nautilus
``` and navigate your way to /etc/apt/sources.list.d/ and delete those list files.


You also have two of this line in your sources.list ```
deb http://packages.medibuntu.org/ karmic free non-free
``` either delete one of the lines or put a # in front of one of the lines.Or go into **Software Sources** and un-tick one of the Medibuntu boxes.


Good Luck

---

### Post by cmcanulty on 2010-01-08
Wow, that worked thanks very much. I guess I am not sure why Ubuntu doesn't have the repositories ready when it releases a new version. This seems quite complicated. I have to do this process for 8 computers. For each do I just look at what repository had an error and then eliminate that source? Will this cause the computers to not update those applications?

---

### Post by plucky on 2010-01-08
> I guess I am not sure why Ubuntu doesn't have the repositories ready when it releases a new version.

The PPA repository is not maintained by Canonical and they do not take responsibility for the packages they contain.The PPA's are maintained by individuals and teams to provide updates to software packages for the different releases.Sometimes the packages aren't updated for later releases.

> For each do I just look at what repository had an error and then eliminate that source?

The PPA's will only get updated if there is a reason to update such as a new release.Sometimes the updates will come out in the Canonical repositories and there is no need for the PPA.Thus the source can be removed.

> Will this cause the computers to not update those applications? 

The applications will get updated if they are updated in the Canonical repositories.

I have to ask why you need so many PPA's for applications that will be updated in the Canonical repositories when there is a new Ubuntu release? 

Especially as you are maintaining 8 computers.

You should use the Canonical repositories whenever possible and only use the PPA to get the latest version when having the latest version fixes a specific problem with the release version or the software is not in the Canonical repository.

Good Luck

---

### Post by cmcanulty on 2010-01-08
Thank you, now I understand. I didn't know the ppas weren't necessary to include when I do the upgrades.

---


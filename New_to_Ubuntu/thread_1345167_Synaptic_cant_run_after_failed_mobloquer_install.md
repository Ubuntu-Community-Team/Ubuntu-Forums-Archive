---
title: "Synaptic cant run after failed mobloquer install"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by THXTom on 2009-12-03
[FONT=Waree]Says unable to get exclusive lock, some other app is running like apt-get [/FONT][FONT=Waree]or aptitude[/FONT][FONT=Waree] is running.[/FONT]
                             
 [FONT=Waree]This happened after I did this:[/FONT]
 ***First, add some repositories, edit your sources.list file. From a terminal:***
  ***Code:***
  ***gksu gedit /etc/apt/sources.list***
  ***Add this to the end of the file:***
  ***Code:***
  [I][B]deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main[/B][/I]
 (I substituted the above for karmic kola instead of hardy)
  ***Save and close gedit, back to the terminal, add the gpg key for the moblock repository and update apt***
  ***Code:***
  [I][B]gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
sudo apt-get update[/B][/I]
  ***now install the packages***
  ***Code:***
  [I][B]sudo aptitude install moblock
sudo aptitude install mobloquer[/B][/I]
   [FONT=Waree]how do I shut down something that I cant find if it is running...looked in Sys monitor-don't see apt-get or aptitude running.[/FONT]
  [FONT=Waree]Anyway all I wanted to do is install mobloquer....cant even find Add/Remove progys on menu bar, accessories, etc...[/FONT]
  

  [FONT=Waree]Sigh[/FONT]
  

  [FONT=Waree]Thanks in advance for any help on getting Synaptic back[/FONT]
  

  [FONT=Waree]Later, T[/FONT]

---

### Post by THXTom on 2009-12-03
[FONT=Waree]Tried this:[/FONT]
 [FONT=Waree]***thomas@thomas-desktop:~$ apt-get update ***[/FONT]
 [FONT=Waree]***E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied) ***[/FONT]
 [FONT=Waree]***E: Unable to lock the list directory ***[/FONT]
 [FONT=Waree]***thomas@thomas-desktop:~$  ***[/FONT]
 [FONT=Waree]And this:[/FONT]
 [FONT=Waree]***sudo gedit /etc/apt/sources.list ***[/FONT]
 [FONT=Waree]***#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ intrepid main restricted ***[/FONT]
 [FONT=Waree]***#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted ***[/FONT]
 [FONT=Waree]***# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to ***[/FONT]
 [FONT=Waree]***# newer versions of the distribution. ***[/FONT]
 
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted ***[/FONT]
 
 [FONT=Waree]***## Major bug fix updates produced after the final release of the ***[/FONT]
 [FONT=Waree]***## distribution. ***[/FONT]
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted ***[/FONT]
 
 [FONT=Waree]***## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ***[/FONT]
 [FONT=Waree]***## team. Also, please note that software in universe WILL NOT receive any ***[/FONT]
 [FONT=Waree]***## review or updates from the Ubuntu security team. ***[/FONT]
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe ***[/FONT]
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe ***[/FONT]
 
 [FONT=Waree]***## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ***[/FONT]
 [FONT=Waree]***## team, and may not be under a free licence. Please satisfy yourself as to  ***[/FONT]
 [FONT=Waree]***## your rights to use the software. Also, please note that software in  ***[/FONT]
 [FONT=Waree]***## multiverse WILL NOT receive any review or updates from the Ubuntu ***[/FONT]
 [FONT=Waree]***## security team. ***[/FONT]
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse ***[/FONT]
 [FONT=Waree]***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse ***[/FONT]
 [FONT=Waree]***deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse ***[/FONT]
 
 [FONT=Waree]***## Uncomment the following two lines to add software from the 'backports' ***[/FONT]
 [FONT=Waree]***## repository. ***[/FONT]
 [FONT=Waree]***## N.B. software from this repository may not have been tested as ***[/FONT]
 [FONT=Waree]***## extensively as that contained in the main release, although it includes ***[/FONT]
 [FONT=Waree]***## newer versions of some applications which may provide useful features. ***[/FONT]
 [FONT=Waree]***## Also, please note that software in backports WILL NOT receive any review ***[/FONT]
 [FONT=Waree]***## or updates from the Ubuntu security team. ***[/FONT]
 [FONT=Waree]***# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse ***[/FONT]
 [FONT=Waree]***# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse ***[/FONT]
 
 [FONT=Waree]***## Uncomment the following two lines to add software from Canonical's ***[/FONT]
 [FONT=Waree]***## 'partner' repository. ***[/FONT]
 [FONT=Waree]***## This software is not part of Ubuntu, but is offered by Canonical and the ***[/FONT]
 [FONT=Waree]***## respective vendors as a service to Ubuntu users. ***[/FONT]
 [FONT=Waree]***# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner ***[/FONT]
 [FONT=Waree]***# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner ***[/FONT]
 
 [FONT=Waree]d***eb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted ***[/FONT]
 [FONT=Waree]***deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted ***[/FONT]
 [FONT=Waree]***deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe ***[/FONT]
 [FONT=Waree]***deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe ***[/FONT]
 [FONT=Waree]***deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse ***[/FONT]
 [FONT=Waree]***deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse ***[/FONT]
 [FONT=Waree]***deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main ***[/FONT]
 [FONT=Waree][I][B]deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main

[/B][/I]And this:
[I][B]thomas@thomas-desktop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
thomas@thomas-desktop:~$ 
[/B][/I]Tried this:[I][B]
thomas@thomas-desktop:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/B][/I]

[/FONT]

---

### Post by THXTom on 2009-12-03
[I][B]E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory[/B][/I]

How to get permission to unlock?
thanks

---

### Post by THXTom on 2009-12-03
Well, this worked:
thomas@thomas-desktop:~[FONT=Arial][I][B]$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                         
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources                                                          
Fetched 308B in 8s (36B/s)                                                                                                  
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
thomas@thomas-desktop:~$ sudo dpkg --configure -a
Setting up blockcontrol (1.6.9-1~karmic) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up p7zip (9.04~dfsg.1-1) ...
Errors were encountered while processing:
 blockcontrol

[/B][/I]Synaptic is working again....

I'll work on installing blockcontrol another day....
[/FONT]

---

### Post by jre on 2009-12-04
First off, when you post logfiles/code or so on, do that in CODE tags instead of making them bold. You find the CODE tags in the advanced editing mode: #


So you found out about **sudo** on your own.
Further you now have the correct sources.list entry for karmic:
```
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
```

Now add the corresponding gpg key for the ppa:
```
gpg --keyserver keyserver.ubuntu.com --recv **9C0042C8**
gpg --export --armor **9C0042C8** | sudo apt-key add -
```

Now about your real problem. Either do it the windows way and reboot, or check running processes with
```
ps aux | grep apt
ps aux | grep dpkg
```

---

### Post by THXTom on 2009-12-10
Thanks for the help, how to and info, will work on this soon.

                                  Code:
 ```
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main In the above example, do you "run" the 1st line, then second line?

```Later, T

---

### Post by jre on 2009-12-10
Again, THXTom, **please use the CODE tags**! You find them in the Advanced Editing Mode (click on #)


Now, no you don't run that code, you add those 2 lines to /etc/apt/sources.list. Then your package manager (synaptic/apt/aptitude/apt-get) knows about the repository and is able to download the packages automatically. The "deb"line is important for you, the deb-src line is optional. But that's all explained e.g. on [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by THXTom on 2009-12-13
Well jre, Mobloquer is in,
 Apps>internet>Mobloquer....
 

 Click on Mo, get a box saying:
 
```
&#8220;/var/log/moblock.log&#8221; could not be found in default path. Please specify a different path.
 
```I'm getting there....

It is fun learning new OS, thanks for your help.

found blockcontrol..nothing in folder, I'll keep digging.

---

### Post by THXTom on 2009-12-13
1 other thing for my enlightenment.

Now you mentioned this earlier, 

```
ps aux ! grep apt, ps aux ! grep dpkg
```

Is the terminal command above 4 separate commands, or one after the other?

Or 1 line each, with the symbol between them? I used an exclamation because I cant enter that symbol if it's needed.

Bear with me, I'm still reading the pocket guide. 

Thanks, T

---

### Post by harrisonk on 2009-12-13
[SIZE=4]Four separate commands would look like:

```
sudo apt-get remove audacity && sudo apt-get install mysql-server && sudo apt-get update && sudo apt-get upgrade
```

I don't know what your code is.

Harrisonk
[/SIZE]

---

### Post by THXTom on 2009-12-13
```
   ps aux | grep apt
ps aux | grep dpkg
```The above is what I'm asking about.

---

### Post by THXTom on 2009-12-13
could it be here?

---

### Post by harrisonk on 2009-12-13
[SIZE=4]The question marks confused me there:D.

Now I understand.

I do believe that those up and down lines split the commands.

Harrisonk
[/SIZE]

---

### Post by THXTom on 2009-12-13
> **harrisonk said:**
> [SIZE=4][SIZE=3]The question marks confused me there:D.

Now I understand.

I do believe that those up and down lines split the commands.[/SIZE]  


[/SIZE]

Yeah how do you type 'em in? I thought ```
&& 
```did that

---

### Post by THXTom on 2009-12-13
nvm, I put my glasses on, turned on the lights, and found it....



|

---

### Post by lidex on 2009-12-13
Just to clarify:
```
ps aux | grep apt
``` is one command
```
ps aux | grep dpkg
``` is one command

Pipe symbol "|" is the key below backspace on my keyboard (en_us, QWERTY) which also contains "\" or "backslash". 
Use shift key first.

---

### Post by lifesmaelstrom on 2009-12-13
The | character is called a pipe. It "pipes" the output of one thing to the input of another.

The command
```
ps aux | grep apt
```
starts the program ps with the arguments a, u, and x. Ps lists the currently running processes on your system. This list is then "piped" to grep. 

Grep searches every line for a the sequence "apt" and returns a list of those lines. As there is no pipe telling where this list should go, it is displayed.

I don't quite understand what you're trying to accomplish with mobloquer. Are you just trying to remove it?

---

### Post by THXTom on 2009-12-13
Click on Mo, get a box saying:
 
```
&#8220;/var/log/moblock.log&#8221; could not be found in default path. Please specify a different path.
 
```

I finally got it installed, but get the above when I try to run it.

Thanks for the reply s.

---

### Post by jre on 2009-12-14
Thanks for using the code tags now :-)

I assume all previous questions have been answered. But to make sure that moblock, blockcontrol and mobloquer are installed correctly now, [B]I recommend that you do
```
sudo dpkg-reconfigure --force moblock blockcontrol mobloquer
```[/B]
This repeats the last steps of the installation. Since you had problems here previously, it might be that the applications are not installed correctly yet.


> **THXTom said:**
> Click on Mo, get a box saying:
 
```
“/var/log/moblock.log” could not be found in default path. Please specify a different path.
 
```

I finally got it installed, but get the above when I try to run it.

This problem happens when you start mobloquer (the GUI) before moblock (the daemon) has ever run. Since moblock has never run, there is no logfile /var/log/moblock.log, and therefore mobloquer can't find it.
I assume you disabled the automatic start of moblock during the installation. 

The easiest solution to solve this is to create an empty logfile:
```
sudo touch /var/log/moblock.log
```

Alternatively you can start moblock manually once:
```
sudo blockcontrol start
```

Note that this problem only occurs until you have started moblock. Once you have done this, it will never bother you again and you can do everything with mobloquer in the future.

---

### Post by THXTom on 2009-12-14
Thanks for all your help jre, it's up and running.

Later T

---


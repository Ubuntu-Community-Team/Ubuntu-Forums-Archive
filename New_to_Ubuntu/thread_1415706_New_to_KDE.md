---
title: "New to KDE"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-02-25
I did a fresh install of Kubuntu 9.10 just cause I have never seen KDE environment .
Now I am facing some noobish problems please help!
I tried playing songs with Amarok an update notifier comes up as usual telling me to install some multimedia codecs.
Thumbnail attached.
I click on "Install Selected".
Another pop-up comes up..another thumbnail attached.
The next time I run Amarok same story.
I have tried my best to put the problem clearly.
Thanks in advance.
PS The same happens with dragon player.

---

### Post by blazemore on 2010-02-25
Open a terminal (Konsole)
type
```
sudo apt-get install kubuntu-restricted-extras
```
Press Enter
Enter your password (there is no visual feedback)
Press Enter

This solves the majority of audio filter related errors.

---

### Post by GrammatonCleric on 2010-02-25
Have you installed the "kubuntu-restricted-extras" package yet?    

```


sudo apt-get install kubuntu-restricted-extras 


```

It's in the multiverse repository.  And should contain all the restricted codec's (i.e. mp3, dvd, etc.)

-GC

---

### Post by peace.gangsta on 2010-02-25
```
abhinav@ubuntu:~$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-restricted-extras

```
I am confused what happened .. My Internet connection is working well.

---

### Post by GrammatonCleric on 2010-02-25
Sounds like you don't have the multiverse repos enable.  Launch Synaptic -> Settings -> Repositories and put a check next to 4th option down that states "Software restricted by copyright or legal issues (multiverse)."  Then click "Close."  Now either click the reload button or close Synaptic altogether and drop into a terminal and run...

```

sudo apt-get update

```

followed by...

```

sudo apt-get install kubuntu-restricted-extras

```

-GC

---

### Post by peace.gangsta on 2010-02-25
Perhaps the most drastic part it this . I tried
```
sudo apt-get update
```
And what I got was 
> abhinav@ubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]                                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                              
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]                                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                        
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]                                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]                                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                        
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]                                                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                                                                
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                                                     
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                               
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                 
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                               
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                        
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US                                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                                       
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US                                         
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                                       
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                             
Reading package lists... Done                                                                                      
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                              

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]          

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]    

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]      

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]    

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
abhinav@ubuntu:~$


---

### Post by peace.gangsta on 2010-02-25
> **GrammatonCleric said:**
> Sounds like you don't have the multiverse repos enable.  Launch Synaptic -> Settings -> Repositories and put a check next to 4th option down that states "Software restricted by copyright or legal issues (multiverse)."  Then click "Close."  Now either click the reload button or close Synaptic altogether and drop into a terminal and run...

```

sudo apt-get update

```

followed by...

```

sudo apt-get install kubuntu-restricted-extras

```

-GC
Pardon my illiteracy but how do I launch "Synaptic"?

---

### Post by Silent Warrior on 2010-02-25
peace.gangsta: Regarding the output from apt-get update (maybe you should double- and triple-check the command you enter to make sure you put 'sudo' in front of it, if you are using the terminal?), it looks like you can't connect to the server. In Synaptic (Settings -> Administration -> Synaptic Package Manager, or run [gksu synaptic] ) you can go into Settings -> Repositories and pick a different download-server. Maybe it'll even have an option to look for the best server for you - could be the server you were trying to reach was down at the moment for one reason or another.

---

### Post by shihkster1015 on 2010-02-25
If you want to, you can go ahead and switch to GNOME. 
I find it a lot more user friendly

---


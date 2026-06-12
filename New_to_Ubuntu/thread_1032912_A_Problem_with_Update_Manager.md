---
title: "A Problem with Update Manager?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-01-06
I'm running 8.10 and tonight got the red triangle telling me to get some important updates from Update Manager. So I ran it and got the following error message after clicking on 'Check':
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://gb.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Could someone give me some idea of what's wrong, why it's wrong, and what I should do to correct it?

---

### Post by 2hot6ft2 on 2009-01-06
Have you tried running
```
sudo apt-get update
```
in a terminal?

---

### Post by Roger Allott on 2009-01-06
> **2hot6ft2 said:**
> Have you tried running
```
sudo apt-get update
```
in a terminal?

I hadn't but I just have. I get exactly the same error message as I had with Update Manager, except with a new and rather bizarre extra comment at the end:
```
W: You may want to run apt-get update to correct these problems
```

So I ran apt-get update again and got exactly the same message again!

---

### Post by Roger Allott on 2009-01-06
> **2hot6ft2 said:**
> Have you tried running
```
sudo apt-get update
```
in a terminal?

This is the full output from apt-get update:
```
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Hit http://gb.archive.ubuntu.com intrepid Release.gpg                          
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Hit http://archive.canonical.com intrepid Release.gpg                          
Hit http://winff.org intrepid Release.gpg                                      
Ign http://repository.cairo-dock.org intrepid Release.gpg                      
Ign http://repository.cairo-dock.org intrepid/cairo-dock Translation-en_GB     
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB               
Ign http://repository.cairo-dock.org intrepid Release                          
Ign http://archive.canonical.com intrepid/partner Translation-en_GB            
Ign http://winff.org intrepid/universe Translation-en_GB                       
Hit http://security.ubuntu.com intrepid-security Release                       
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB              
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB          
Ign http://repository.cairo-dock.org intrepid/cairo-dock Packages              
Hit http://archive.canonical.com intrepid Release                              
Hit http://winff.org intrepid Release                                          
Hit http://packages.medibuntu.org intrepid Release                             
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Hit http://repository.cairo-dock.org intrepid/cairo-dock Packages              
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://winff.org intrepid/universe Packages                                
Hit http://packages.medibuntu.org intrepid/free Packages                       
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB           
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB         
Hit http://security.ubuntu.com intrepid-security/main Sources
Get: 1 http://gb.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid Release         
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Get: 2 http://gb.archive.ubuntu.com intrepid-updates Release [51.2kB]          
Err http://gb.archive.ubuntu.com intrepid-updates Release 
  
Hit http://gb.archive.ubuntu.com intrepid/main Packages
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources                         
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://gb.archive.ubuntu.com intrepid/universe Packages                    
Hit http://gb.archive.ubuntu.com intrepid/universe Sources                     
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources                   
Fetched 190B in 8s (24B/s)                                                     
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://gb.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

---

### Post by 2hot6ft2 on 2009-01-06
> **Roger Allott said:**
> I hadn't but I just have. I get exactly the same error message as I had with Update Manager, except with a new and rather bizarre extra comment at the end:
```
W: You may want to run apt-get update to correct these problems
```

So I ran apt-get update again and got exactly the same message again!
That was rather redundant wasn't it...:confused:
It looks like for some reason it doesn't like the GPG signature. Someone else had that yesterday and I don't know if anyone had an answer or not. I can copy the url and go there so I know it's not down.

Sorry but I don't have the answer for you, someone with more knowledge will have to jump in with an answer on this one.

---

### Post by tuxxy on 2009-01-06
hmm have you changed any repository lately or edited /etc/apt/sources.list? 

```
sudo apt-get update
sudo apt-get upgrade
```
If them coammdns dont help off the top of my head you could go into software sources and make sure you have the correct server set or try a different mirror.

---

### Post by 2hot6ft2 on 2009-01-06
He tried update and it told him to run update...:confused:

Maybe upgrade will do it. He went offline so thanks I'll remember that.

Thanks tuxxy

---

### Post by Roger Allott on 2009-01-07
> **tuxxy said:**
> hmm have you changed any repository lately or edited /etc/apt/sources.list? 

I think I might have done but I really don't recall which one was most recent.

Is there any way you can tell from what I posted in post #4 which of my repository list is causing the problem? Or is it a more global problem?

---

### Post by Roger Allott on 2009-01-07
> **tuxxy said:**
> 
```
sudo apt-get update
sudo apt-get upgrade
```

The output from upgrade is bog standard with no error messages:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

> **tuxxy said:**
> 
If them coammdns dont help off the top of my head you could go into software sources and make sure you have the correct server set or try a different mirror.

How do I do that?

---

### Post by tuxxy on 2009-01-07
> **Roger Allott said:**
> The output from upgrade is bog standard with no error messages:

How do I do that?

Open system > admin > software sources and select one from the download server tab.

---

### Post by Joeb454 on 2009-01-07
Try using the Main Server.

I had an issue earlier with the GB server (not sure where you are...) but changing the server and reloading the sources seemed to work.

---

### Post by Roger Allott on 2009-01-07
> **Joeb454 said:**
> Try using the Main Server.

I had an issue earlier with the GB server (not sure where you are...) but changing the server and reloading the sources seemed to work.

Thanks. That seems to have done the trick.

One of the updates installed was nvidia-177-modaliases, which is odd because not only do I not have an nvidia card, but I have a basic laptop PC that has no specialist sound/video cards at all as far as I know.

Could this rogue driver set be the reason why I can't run Googleearth, Celestia and other image-intensive applications without getting unreadable text or image distortion?

I've done a search on Synaptic for 'nvidia' and there are a few packages marked as installed:
[LIST][*]nvidia-common
[*]nvidia-71-modaliases
[*]nvidia-96-modaliases
[*]nvidia-173-modaliases
[*]nvidia-177-modaliases
[*]xserver-xorg-video-nv
[*]smartdimmer
[*]jockey-gtk
[*]jockey-common[/LIST]

Would it be a good idea, in your opinion, to uninstall those packages?

---


---
title: "error from Update Manager"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by ubun_tut on 2010-08-23
hi,

while i was doing a software update, i received this error 

```

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh/language-pack-zh_8.04+20100117_all.deb
  404 Not Found

```

so i searched for some posts here which report the same problem, and tried 'sudo apt-get clean' and then 'sudo apt-get update' on the terminal, and got the following:

```

Hit http://sg.archive.ubuntu.com hardy Release.gpg
Get:1 http://dl.google.com stable Release.gpg [189B]                                                                      
Ign http://dl.google.com stable/main Translation-en_SG                                                                    
Ign http://sg.archive.ubuntu.com hardy/main Translation-en_SG                                                             
Get:2 http://dl.google.com stable Release [2544B]                                                                         
Ign http://sg.archive.ubuntu.com hardy/restricted Translation-en_SG                                                       
Ign http://sg.archive.ubuntu.com hardy/universe Translation-en_SG                                           
Ign http://sg.archive.ubuntu.com hardy/multiverse Translation-en_SG                                                       
Get:3 http://dl.google.com stable/main Packages [1063B]                                                                   
Get:4 http://sg.archive.ubuntu.com hardy-updates Release.gpg [189B]                                                       
Ign http://sg.archive.ubuntu.com hardy-updates/main Translation-en_SG                                 
Ign http://sg.archive.ubuntu.com hardy-updates/restricted Translation-en_SG                           
Ign http://sg.archive.ubuntu.com hardy-updates/universe Translation-en_SG                             
Ign http://sg.archive.ubuntu.com hardy-updates/multiverse Translation-en_SG                           
Get:5 http://sg.archive.ubuntu.com hardy-security Release.gpg [189B]                                  
Get:6 http://sg.archive.ubuntu.com hardy-security Release.gpg [189B]                                  
Get:7 http://sg.archive.ubuntu.com hardy-security Release.gpg [189B]     
Ign http://sg.archive.ubuntu.com hardy-security/main Translation-en_SG                                
Get:8 http://ppa.launchpad.net hardy Release.gpg [307B]                                               
Ign http://sg.archive.ubuntu.com hardy-security/restricted Translation-en_SG                          
Ign http://sg.archive.ubuntu.com hardy-security/universe Translation-en_SG                            
Ign http://sg.archive.ubuntu.com hardy-security/multiverse Translation-en_SG                          
Hit http://sg.archive.ubuntu.com hardy Release                                                        
Get:9 http://packages.medibuntu.org hardy Release.gpg [197B]                                                              
Get:10 http://sg.archive.ubuntu.com hardy-updates Release [58.5kB]                                                        
Err http://sg.archive.ubuntu.com hardy-updates Release                                                                    
  
Get:11 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]                                                       
Get:12 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]     
Get:13 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]        
Get:14 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:15 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:16 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:17 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:18 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Ign http://ppa.launchpad.net hardy/main Translation-en_SG                    
Get:19 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:20 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:21 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:22 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Get:23 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]          
Ign http://packages.medibuntu.org hardy/free Translation-en_SG               
Get:24 http://sg.archive.ubuntu.com hardy-security Release [58.5kB]                                          
Err http://sg.archive.ubuntu.com hardy-security Release                                                                   
  
Hit http://sg.archive.ubuntu.com hardy/main Packages                                                                      
Hit http://sg.archive.ubuntu.com hardy/restricted Packages                                            
Hit http://sg.archive.ubuntu.com hardy/restricted Sources                                             
Hit http://sg.archive.ubuntu.com hardy/main Sources                                                   
Hit http://sg.archive.ubuntu.com hardy/multiverse Sources                                             
Hit http://sg.archive.ubuntu.com hardy/universe Sources                                               
Get:25 http://ppa.launchpad.net hardy Release [65.9kB]                                                
Hit http://sg.archive.ubuntu.com hardy/universe Packages                                              
Hit http://sg.archive.ubuntu.com hardy/multiverse Packages                                                  
Ign http://packages.medibuntu.org hardy/non-free Translation-en_SG                                          
Get:26 http://packages.medibuntu.org hardy Release [11.7kB]                          
Ign http://packages.medibuntu.org hardy Release           
Get:27 http://ppa.launchpad.net hardy/main Packages [24.1kB]
Get:28 http://packages.medibuntu.org hardy/free Packages [6342B]
Get:29 http://packages.medibuntu.org hardy/non-free Packages [6215B]         
Fetched 179kB in 6s (29.4kB/s)                                                                                            
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://sg.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://sg.archive.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2

W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

can someone pls tell me what is wrong and how i can solve it?

thanks.

---

### Post by inameiname on 2010-08-23
Firstly, it sounds as if it's merely the repository that has misplaced that deb file, and/or is having the issues, not you. That's all. So I wouldn't worry about it. 

And then, looking at your terminal readout, the 'lock' was because of another running program that was using the updating stuff, presumably update manager since you had just used that. A restart should've fixed that. 

Finally, I think your main issue is because it's Ubuntu Hardy. My guess is the repos are becoming less and less updated, and they are starting to close shop. I suggest updating, as that might fix things.

---

### Post by ubun_tut on 2010-08-24
sorry for being a noob, but can you tell me how to relocate that deb file in the repository?

---

### Post by LiquidMeson on 2010-08-24
Changing the download location might make it work again. System>admin>software sources> Download From: 

System>admin>synaptic manager> search for language-pack-zh

---

### Post by inameiname on 2010-08-24
I agree with LiquidMeson, might be good idea to try another download location as well as search synaptic for that package. You could also do the same search through the terminal, by:

sudo apt-cache search language-pack-zh

...and see what pops up.

On mine, I performed a 'sudo apt-cache policy language-pack-zh', and it turned up these results:

language-pack-zh:
  Installed: (none)
  Candidate: 1:10.04+20091218
  Version table:
     1:10.04+20091218 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages

So perhaps check out the US download location, which you can change for your current one by Applications -> System -> Administration -> Software Sources and change the Download from section to another one, (here it's Server for United States). 

Of course, since you are not on Lucid, perhaps you are unable to get it on Hardy. If you are even trying to download it. :P

---

### Post by coffeecat on 2010-08-24
> **ubun_tut said:**
> can you tell me how to relocate that deb file in the repository?

I don't need to add to the good advice given by others, but just a word of clarification. A repository is a server providing Ubuntu packages. There are Ubuntu repositories all around the world. Your system will have been set up to download packages from a server/repository near you. One possible explanation for the first error is that the particular server was down for maintenance. The 404 - not found message would be consistent with this. This happens occasionally. If this happens to you, you can either wait a few hours for things to get resolved or change to another repository the way LiquidMeson described.

---

### Post by ubun_tut on 2010-08-25
i changed the software server as suggested, and now it seems to be working fine. thanks!

but then i notice another problem. i have both windows xp and ubuntu 8.04 installed on my desktop, so that when i boot up the machine, it prompts me to choose to start up in windows or ubuntu. usually, i have 3 options at this screen: other than windows and ubuntu, there is another one that goes like ubuntu recovery mode. but as of yesterday, i suddenly have many more options. these are, however, all repetitions of the ubuntu options, so now i have several normal ubuntu options, and several ubuntu recovery mode options. they dont seem to be causing any trouble though, as i can still get into ubuntu from anyone of the normal ubuntu options.

what should i do to remove these redundant options? is it something to do with the master boot record?

---

### Post by coffeecat on 2010-08-25
> **ubun_tut said:**
> as of yesterday, i suddenly have many more options. these are, however, all repetitions of the ubuntu options, so now i have several normal ubuntu options, and several ubuntu recovery mode options. they dont seem to be causing any trouble though, as i can still get into ubuntu from anyone of the normal ubuntu options.

what should i do to remove these redundant options? is it something to do with the master boot record?

These will be different kernel versions, one instance each of normal and recovery mode for each kernel. The kernel versions are numbered, "2.6.x-y", the latest appearing first and becoming the default. You will have seen the extra grub menu entries after a kernel update which doesn't remove the old kernel, but leaves both. The reason is that, rarely, the newer version of the kernel gives problems with some hardware. If this happens to you, you can simply choose the previous version for booting into.

It's a good idea, therefore, to leave the immediately previous kernel version in case you need it. You can uninstall older versions, if you have more than two in the grub menu, by using Synaptic. This will remove their entries in the grub menu automatically. But unless the menu is getting unwieldy, you might not want to bother.

If it troubles you, post the actual kernel numbers (2.6.x-y) for all the kernels you have there, and someone will tell you what you need to do to uninstall the unwanted ones.

---

### Post by 3rdalbum on 2010-08-25
> **ubun_tut said:**
> i changed the software server as suggested, and now it seems to be working fine. thanks!

but then i notice another problem. i have both windows xp and ubuntu 8.04 installed on my desktop, so that when i boot up the machine, it prompts me to choose to start up in windows or ubuntu. usually, i have 3 options at this screen: other than windows and ubuntu, there is another one that goes like ubuntu recovery mode. but as of yesterday, i suddenly have many more options. these are, however, all repetitions of the ubuntu options, so now i have several normal ubuntu options, and several ubuntu recovery mode options. they dont seem to be causing any trouble though, as i can still get into ubuntu from anyone of the normal ubuntu options.

what should i do to remove these redundant options? is it something to do with the master boot record?

This is a different problem so it should be in a different thread, but oh well.

This is because you've run system updates that have installed a new Linux kernel. The kernel is the most underlying part of the operating system. The old kernels are kept in case there's anything wrong with your new kernel, but if you can boot into the new one okay then you can delete the old ones.

Deleting them in Synaptic Package Manager will also remove them from the GRUB menu. Just remember to keep the most recent one installed. Some users will also suggest keeping the 2nd-most recent one installed too as an insurance policy.

---

### Post by ubun_tut on 2010-08-25
i see. i will keep them first then, since its still not getting out of hand.

thanks, and my bad for posting in the wrong forum!

[edit: i mean wrong thread]

---

### Post by PPPilot on 2010-08-25
When you do decide to remove the old kernels, you will have to update the grub.conf file in order to remove those extra entries from the grub menu. From the Terminal run: ```
sudo update-grub
```The next time you reboot, the grub menu should be up to date.

---

### Post by coffeecat on 2010-08-25
> **PPPilot said:**
> When you do decide to remove the old kernels, you will have to update the grub.conf file in order to remove those extra entries from the grub menu.

Point of information: not if you uninstall using Synaptic. It's always done an update-grub for me whenever I've done a cleanout of old kernels.

---

### Post by PPPilot on 2010-08-25
I know it is suppose to work that way but when I was running Karmic, it would not update my grub. So I got in the habit of running update-grub. I have not tried it since I've been on Lucid.

---


---
title: "Synaptic Package Manager trouble..."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-23
Hey all. I went to add the OpenOffice.org extension repository to my list in SPM and am now getting this error;

'E:Malformed line 63 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

It won't let me in to delete the extension repository that I just added and now I can't access SPM at all. Any suggestions as to how to fix it?

Thanks!

---

### Post by taurus on 2009-01-23
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Either delete the entry in line 63 or modify it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Nepherte on 2009-01-23
Open /etc/apt/sources.list:
```
gksudo gedit /etc/apt/sources.list
```
and remove the offending line 63 or correct it. Afterwards you save and exit.

---

### Post by Jynxx on 2009-01-23
Awesome, that worked. I can now access SPM. I'm getting one other error that I can't see to figure out.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035


Any ideas on this one?

---

### Post by PriceChild on 2009-01-23
> **Jynxx said:**
> Awesome, that worked. I can now access SPM. I'm getting one other error that I can't see to figure out.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035


Any ideas on this one?
The "W:" signifies that that is a warning, rather than an **E**rror.

GPG is used to verify that the software you are downloading is the ubuntu developers wanted to build. However launchpad doesn't support this functionality (yet) and so if you want to use ppas you'll have to bear with it I'm afraid.

---

### Post by Jynxx on 2009-01-23
Ok, sounds good. It doesn't seem to affect SPM in any way except for the message that pops up. I'll just deal with it. Thank you all for the assistance!:p

---

### Post by blackgr on 2009-01-23
I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
you have to run this with sudo

---

### Post by nossifer on 2009-06-06
I tried the bash script.  Changed to Jaunty.  It seemed to run fine, but I still get the error after I refresh synaptec.

$ sudo ./launchpad-update                                                                                                                                      
Reading package lists... Done                                                                                                                                                             
Building dependency tree                                                                                                                                                                  
Reading state information... Done                                                                                                                                                         
The following NEW packages will be installed:                                                                                                                                             
  curl                                                                                                                                                                                    
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                                                                                                                            
Need to get 210kB of archives.                                                                                                                                                            
After this operation, 324kB of additional disk space will be used.                                                                                                                        
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main curl 7.18.2-8ubuntu4 [210kB]                                                                                                               
Fetched 210kB in 1s (157kB/s)                                                                                                                                                             
Selecting previously deselected package curl.                                                                                                                                             
(Reading database ... 169761 files and directories currently installed.)                                                                                                                  
Unpacking curl (from .../curl_7.18.2-8ubuntu4_i386.deb) ...                                                                                                                               
Processing triggers for man-db ...                                                                                                                                                        
Setting up curl (7.18.2-8ubuntu4) ...                                                                                                                                                     
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current                                                                                                           
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information

---


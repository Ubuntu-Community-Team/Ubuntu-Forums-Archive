---
title: "Update Manager downloads the same info again and again"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by telovin on 2010-01-26
My update manager goes on updating the same information. Once it updates, it says your system is uptodate and it was updated less than an hour ago. When I click on check, it again downloads the same software information. Update manager basically updates the same info. It goes on updating. It says "the repositories will be checked for new , removed or upgraded software packages' and continues  the same thing. Basically update goes on and on. Just want to know if my computer is infected. Mine is karmic koala 9.10.
After this my grub manager shows every entry twice. Is there any antivirus or antispyware scans and removal for ubuntu? Kindly help

---

### Post by x33a on 2010-01-26
I think you mean, the repositories are being updated each time. if that is the case, then it is absolutely fine. but, if the packages are downloaded again, then we have an issue.

as for the several entries at grub, when newer kernels are added to the system, they get added to grub automatically. you'll have to manually remove the older kernels.

---

### Post by telovin on 2010-01-26
Repositories being updated is fine. But update manager is downloading the same updates again and again.

---

### Post by benfindlay on 2010-01-26
Does typing ```
sudo apt-get update && sudo apt-get upgrade
```into a terminal window produce the same results?

---

### Post by 3rdalbum on 2010-01-26
Your computer doesn't have viruses or spyware. Even if this was Windows, I'd say the same thing: Being presented with updates that you've already installed is not something a virus would cause.

You're using Linux which currently does not have any viruses, and is built to be resistent to many of the ways that viruses can enter a computer.

I'd suggest running:

```
sudo apt-get update
sudo apt-get upgrade
```

and see if there are any error messages.

---

### Post by telovin on 2010-01-26
I ran the command. It downloaded packages worth 10mb again.

Inthe end, the terminal showed the following result:
" Fetched 10.6MB in 6min 14s (28.2kB/s)                                          
Reading package lists... Done"

Is everything ok now?
Someone had hacked on to my system before thats y I switched to ubuntu. Hope ubuntu will always protect my machine n data.

---

### Post by mcduck on 2010-01-26
Are you sure it's actually downlaoding packages, not just repository indexes?

Veery time you click the "check for updates"-button (or run "sudo apt-get update") it will download the repository index files to get up-to-date informationa bout available updates. After that, if there are any updates available, they are shown to you and you can start the actual update process that downlaods the ne packages and installs them.

"the repositories will be checked for new , removed or upgraded software packages' sounds like it's just downlaoding the repository indexes, not any actual packages. The indexes will of course be downlaoded again and again if you keep on telling it to check for updates.

---

### Post by x33a on 2010-01-26
ok, one thing to confirm is try
```

sudo apt-get update && sudo apt-get upgrade 
```> post all the output here, wrap it in quote. then immediately try the above command again, and post the output here. this way, we'll be able to confirm if everything is being updated again.

---

### Post by telovin on 2010-01-27
Hi,
I am posting the entire thing which happened on terminal after typing sudo apt-get upgrade.
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg [189B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN   
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg [189B] 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release [65.9kB]           
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                       
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [905B]                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release [44.1kB]             
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages [1,353kB]              
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages [7,971B]         
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages [190kB]         
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources [640kB]                
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages [5,133kB]         
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages [158kB]       
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources [48.1kB]       
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages [93.0kB]  
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources [22.8kB]   
Fetched 10.6MB in 11min 54s (14.8kB/s)                                         
Reading package lists... Done

---

### Post by mcduck on 2010-01-27
Those are just the repository indexes (text fiels that tell what packages there are available in the repositories). Not any actual packages. Everything is working just like it should. :)

---

### Post by telovin on 2010-01-27
Hi,
I am posting details after entering the commands.
sudo apt-get update
> **telovin said:**
> 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg [189B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN   
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg [189B] 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release [65.9kB]           
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                       
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [905B]                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release [44.1kB]             
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages [1,353kB]              
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages [7,971B]         
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages [190kB]         
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources [640kB]                
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages [5,133kB]         
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages [158kB]       
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources [48.1kB]       
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages [93.0kB]  
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources [22.8kB]   
Fetched 10.6MB in 11min 54s (14.8kB/s)                                         
Reading package lists... Done...........

---

### Post by telovin on 2010-01-27
sudo apt-get upgrade
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by telovin on 2010-01-27
Is it? when it started downloading so much, I thought may be something is wrong. Ohh thnx so much. I was very much worried. It was checking for updates daily even though I had set the updates frequency as weekly.

---

### Post by x33a on 2010-01-27
you can comment out the sources repository, if you don't need them. that'll save you a few megabytes.

---

### Post by telovin on 2010-02-02
Thank u so much x33a. how do we command out the repository?

---

### Post by x33a on 2010-02-02
open system -> administration -> software sources.

under downloadable from internet, uncheck source code.

---

### Post by telovin on 2010-02-03
Thanks once again. I have done that.:)

---


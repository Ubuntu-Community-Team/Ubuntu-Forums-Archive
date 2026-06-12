---
title: "Error Message RAR SUPPORT"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by MatthewWaterman on 2009-08-27
[COLOR=Red]When I try to get Rar support 

I try to follow this [/COLOR]
 				 				[B]
Re: rar support?[/B] 			
 			 			 		   		 		 		1. Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2.  	Code:
 	sudo aptitude update
sudo aptitude install rar unrar 

 		                   		  		  		 		 			[COLOR=Red]I have enabled the extra repositories but when I copy the above in to the terminal I get this message

[COLOR=Navy]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: You may want to run apt-get update to correct these problems



[COLOR=Red]HELPP!!![/COLOR]
[/COLOR]
[/COLOR]

---

### Post by tgm4883 on 2009-08-27
looks like you missed a 

```
apt-get install medibuntu-keyring
```

---

### Post by MatthewWaterman on 2009-08-27
Sorry I get this

[FONT=monospace]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What do I do?

[/FONT]

---

### Post by SunnyRabbiera on 2009-08-27
> **MatthewWaterman said:**
> Sorry I get this

[FONT=monospace]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What do I do?

[/FONT]

he forgot the sudo, the command should be:
sudo apt-get install medibuntu-keyring

---

### Post by MatthewWaterman on 2009-08-27
Cheers sorry I still fairly new to all this 
Sorted

---


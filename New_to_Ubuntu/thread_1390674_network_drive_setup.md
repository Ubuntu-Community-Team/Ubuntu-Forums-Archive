---
title: "network drive setup"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by squrl on 2010-01-25
I would like to ask for someone with the knowledge to accomplish my goal to please give me a detailed walk thru of how to get this done if its even possible.

Dell 8400 P4 3.2 gig  -  D-link DNS-321 network box with two drives. (They currently have old files on them. NTFS) I have never been able to access the network drives. I don't have a windows machine available to use the disk that came with the DNS-321 The Dell machne works fine for any other functions. I have searched and tried several tutorials to accomplish this but so far none have worked. I do know the DNS321 is located at 192.168.15.2  Samba smbfs has been installed. Clicking on network under 'places' does nothing. 

Any help would be appreciated.

---

### Post by cariboo on 2010-01-26
I not familiar with your device, but it should have a web interface to access it and set it up to do what you need. try http:/192.168.15.2. One other thing to check is to make sure that you are in the same netblock, in other words, the rest of the computers in your network should be using ip addresses in the 192.168.15.0 - 192.168.15.254 range.

---

### Post by Morbius1 on 2010-01-26
I helped someone about  month ago on that exact same device [http://ubuntuforums.org/showthread.php?t=1357070](http://ubuntuforums.org/showthread.php?t=1357070). See if this helps.
On your ubuntu machine:

> Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add to the [COLOR=Blue][global][/COLOR] section the following two lines:
     
     ```
client lanman auth = Yes 
lanman auth = Yes 
```Save the file and exit gedit

Back in the terminal type **sudo service samba restart**

Wait a few minutes, and see if you can access the NAS

---

### Post by Gone fishing on 2010-01-26
Can you ping 192.168.15.2? my guess is not. If not and you run ifconfig what IP address are you on?

I think in the first instance I'd manually set your network IP to something like 192.168.14.4 using the network connections applet and see what happens.

---


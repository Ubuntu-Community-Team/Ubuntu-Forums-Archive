---
title: "Cannot browse network in Ubuntu 13.10"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by Gaddy on 2013-10-23
Since I've upgraded (clean install) to 13.10, I'm unable to browse my Windows network.
I've tried this using the "Files" application. 
I am however able to connect to a specific computer by using the "Connect to server" option (also in files).
This would normally suffice, however I need to be able to print to a shared windows printer. And everytime I try to browse the network, whether in "Files" or within the "New Printer" dialogue, nothing happens. It appears to be searching for something but nothing comes up.
Sometimes i'm faced with:
"
Unable to access location
Failed to retrieve share list from server: Connection timed out
"


This was working just fine in 13.04.
Any ideas?

---

### Post by gwm on 2013-10-23
Similar problem. My printer is attached to the Ubuntu PC but after the upgrade, it is no longer visible to the Windows box. I tried browsing the network and I too get unable to access location.
```
Unable to access Location
Failed to retrieve share list from server. No such File or directory.
```
Perhaps the upgrade removed Samba? How does one find out what is installed? Since Unity arrived, I find that these sort of things have become hidden and I don't even know how to check what is installed any more.

---

### Post by skleist29s on 2013-10-26
Same problem. And I can add that after the upgrade my Windows shares still connect through etc/fstab, but I can no longer write to the shares.
Consider going back to 13.04 :-(

---

### Post by gwm on 2013-11-04
The silence is ominous!
Only 270 odd views suggests we are in the minority and others aren't having this trouble.
I found this How-To about fixing Windows shares:

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

At the end of the How-To is a bit about configuring Windows 7. I've tried to apply everything to my Ubuntu 13.10 desktop and to my Windows7 laptop. The only things I ended up changing were on the laptop - enabling sharing and turning off password protection. Perhaps I still need to reboot everything because I still can't see my laptop.
In Nautilas, I click **Browse Network** and a **Windows Network** icon appears. When I double click the icon I still get the same error

[SIZE=3]**Unable to access location**[/SIZE]
Failed to retrieve share list from server: No such file or directory

Oh well! Despite many threads dealing with similar problems, nothing is happening. I guess there's a bug and we'll just have to wait and hope that some update is going to come along and fix it for us. My work around is a memory stick. Transfer files to memory stick. Transfer memory stick to target computer. Copy to target. When printing is needed, I use email to send it all the way to Google and back to the computer with the printer attached. That is less hassel than the memory stick.

---

### Post by ian-weisser on 2013-11-04
> **gwm said:**
> Similar problem. My printer is attached to the Ubuntu PC but after the upgrade, it is no longer visible to the Windows box. 

Your problem (Windows cannot see a Ubuntu box) seems dissimilar to the original poster's problem (Ubuntu cannot see a windows box). Consider a separate thread for it to avoid confusion.

---

### Post by ian-weisser on 2013-11-04
> **Gaddy said:**
> Since I've upgraded (clean install) to 13.10, I'm unable to browse my Windows network.
I've tried this using the "Files" application. 
I am however able to connect to a specific computer by using the "Connect to server" option (also in files).
[...]
Any ideas?

Have you tried the guides and troubleshooting tips at [https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

---

### Post by smuggly on 2013-11-11
This is a real problem as of 13.04. I used to be able to install winbind edit nsswitch.conf. & go. Now everything is borked again. I really don't understand why this happens ALL THE TIME with Buntu?

---

### Post by me-patrickavella on 2013-11-12
Yeah, I too am having a horrible time with ubuntu 13.10, I can not access any windows boxes (or some of the linux boxes) on my network despite apt-get installing samba. It seems just a couple of the computers, and times out if I try to access them. I cringe everytime there's a new ubuntu release, but the 12 LTS version doesn't run on my current hardware.

---

### Post by smuggly on 2013-11-13
Has Anyone out there got the network browsing working with the 13.10 release? Thanks Smuggly

---

### Post by Morbius1 on 2013-11-13
> **smuggly said:**
> Has Anyone out there got the network browsing working with the 13.10 release? Thanks Smuggly
Yep. Know what I did to get it working? Nothin'

No nonsensical use of nsswitch or winbind. No modifications of smb.conf. Not a damn thing. Works out of the box. And by the way this is all despite that fact that I can't ping another box on my home network by name if my life depended on it.

---

### Post by smuggly on 2013-11-15
This maybe the firewall? I haven't checked this yet. Ubuntu is a great OSD & i'm sure this will be fixed. I hope soon. I,m gonna try a fresh install again this weekend.

---

### Post by ian-weisser on 2013-11-15
Reinstalling Ubuntu seems rather extreme.

Have you tried [http://askubuntu.com/questions/287546/unable-to-access-windows-share-in-ubuntu-13-04](http://askubuntu.com/questions/287546/unable-to-access-windows-share-in-ubuntu-13-04) ?

or [http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau) ?

What happened?

---

### Post by smuggly on 2013-11-19
I can't browse my windows network after 12.10 on Ubuntu Xubuntu or any variant. I even have to edit nsswitch.conf & install winbind in 12.10 & earlier. I'm not sure why but. after googling I see I'm not alone. Im on my way to work but will be doing a lot of work on it this weekend, Thanks Smuggly

---

### Post by YumaJim on 2013-11-19
I also was not able to connect to my network printer after upgrading to 13.10.
However after rereading the 13.10 release notes. I solved this problem by editing
file '/etc/cups/cups-browsed.conf'. I made the following change:

< # BrowseAllow 192.168.1.0/255.255.255.0
---
>  BrowseAllow 192.168.0.1/255.255.255.0

Note that I uncommitted one line and changed the address to 192.168.0.1, the address of my router. My printer has a static address of 192.168.0.99
Now the printer add function finds my printer (HP psc 2510) and I can print from all my computers including my laptop via wireless (wireless router conection).

Hope this helps.
best to all
yumajim

---


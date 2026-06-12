---
title: "connecting to a usb drive on a router"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by patrick60 on 2014-11-01
Well here we go first time user. And not skilled with Ubuntu 14.04

To day i connected my 1 TB USB drive to my Budii Lite Router. Got every thing working with windows 7 and ipad, all good.

But when i try to access drive from my ubuntu machine i keep getting the following attachment.



I have tried all the manner of user names and passwords i am aware of.

Can any one help
Thanks

---

### Post by kurt18947 on 2014-11-01
I am not familiar with that router so can't help directly. I can relate my experience.  I've done what you want to do with two different routers, a Western Digital N600 and Netgear WNDR3400.  The Western Digital worked but was a bit of a pain, the Netgear was plug 'n' play pretty much.  I'm using Ubuntu Gnome currently 14.04. I first tried Nautilus file browser - browse network and Connect to Server.  In each case the Western Digital would see the attached storage but would not open it, I'd get an error messages. The Netgear router will open and access attached drives using Nautilus.  If I click on "Browse Network" I see the attached storage devices. Double clicking opens them.  I could also use "Connect to Server" and enter the router's I.P. address and access the storage device that way.

The Western Digital router was not as straight forward. What ultimately worked for me was to install "Filezilla" from the repositories.  I used the router's I.P. address as the server address. I still couldn't open a file on the storage device using Filezilla but could move files between the storage device and the computer.

---

### Post by Bucky Ball on 2014-11-01
Welcome. Have you entered the username and password you use to login to Ubuntu?

Have you got a username and password set up on the router?

Is the disk encrypted somehow?

You've tried a bunch of usernames and PWs, but what is the message you get when it fails to connect exactly, please?

---

### Post by weatherman2 on 2014-11-01
If it's an open Windows share (sounds like it), try entering a username of "guest" and a blank password.

---

### Post by patrick60 on 2014-11-01
THANK U FOR YOUR REPLY.
I HAVE TRIED MY UBUNTU CREDENTIALS, NO GO
THE 1 TB DRIVE IS NOT ENCRYPTED
I GET NO ERROR MESSAGES. THE POPUP WINDOWS ASKING FOR USERNAME AND PSWD JUST REFRESHES

THE DRIVE ON THE ROUTER HAS A USERNAME "Pat" AND A PSWD OF "1". I KEPT IT ALL SIMPLE FOR NOW TILL I CAN ESTABLISH CONNECTION THE SETUP MORE SECURE CREDENTIALS LATER.

I HAVE TRIED THE ROUTER LOGIN CREDENTIALS, NO GO

IT WAS SUGGESTED TO TRY FILEZILLA. WHICH I HAVE INSTALLED. WHEN THE ACTIVITY WINDOW WITHIN FZ THE USERNAME IS ACCEPTED BUT FAILS PSWD AUTHENTICATION WITH ERROR 530.

THATS IT FOR NOW. STILL TRYING

PATRICK

---

### Post by phidia on 2014-11-02
If you search the string "FAILS PSWD AUTHENTICATION WITH ERROR 530" you'll get a lot of hits. 
The thread [here]("https://forum.filezilla-project.org/viewtopic.php?t=4864") (9th post down) looked most promising to me but you would have to try that of course.

---

### Post by Bucky Ball on 2014-11-02
@patrick60: Please avoid posting in capitals. It is considered shouting. ;)

A search for 'filezilla error 530' gave me a gazillion hits. 

[https://duckduckgo.com/?q=filezilla+error+530](https://duckduckgo.com/?q=filezilla+error+530)

You might want to dig through that and get back to us with what's working and what's not. Filezilla's great. Use it myself. Very handy.

Filezilla uses ftp. Just a point: are you using Samba to connect with Windows??? Do you have Samba installed in Ubuntu??? Not sure that it is installed by default anymore in the desktop version. Check. If the external drive has Samba shares and is NTFS then that could be the way to go. 

But I have a feeling that without cracking the password thing, this is going to be tricky. Could you boot into windows and unmount that drive in Windows, then restart to Ubuntu and see if it's any different?

Do you use a password to login to Windows? Have you tried that?

* Just looked at your screen shot again. Yep, it is saying 'Windows shares' and 9 times out of 10 that means 'samba shares', probably NTFS or FAT.

---

### Post by barroncm on 2014-11-02
I had a similar issue with a belkin router that allowed usb drive sharing. After banging my head against the wall for a while ( Same un/pw issue) I broke down and read the instructions. It seems that 90% of that type of sharing is set up for windows networks only and only supported by a windows/Mac network.


So it sits, waiting for a version of DD-WRT that will support it.

---

### Post by Bucky Ball on 2014-11-02
> **barroncm said:**
> It seems that 90% of that type of sharing is set up for windows networks only and only supported by a windows/Mac network.



Which means they are samba shares, as mentioned in my last post. Install samba from software centre, research setting it up, and try again. You may have a password set up for samba sharing in Windows. That is what you will need to use, but you need to have samba installed in the Linux box first.

---

### Post by kurt18947 on 2014-11-03
> **barroncm said:**
> I had a similar issue with a belkin router that allowed usb drive sharing. After banging my head against the wall for a while ( Same un/pw issue) I broke down and read the instructions. It seems that 90% of that type of sharing is set up for windows networks only and only supported by a windows/Mac network.


So it sits, waiting for a **version of DD-WRT that will support it.**

Hmmm, you may have saved me buggering up my $12 off Ebay Netgear router. I was seriously considering installing DD-WRT, it's supposed to be supported and I much prefer it to vendor default firmware but I also want the USB port to work. I'll do some research and perhaps  inquire on DD-WRT's forum.

---


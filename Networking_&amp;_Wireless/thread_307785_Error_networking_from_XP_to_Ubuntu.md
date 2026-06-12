---
title: "Error networking from XP to Ubuntu"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by Hercules on 2006-11-27
Hi,

I'm having problems networking a PC running XP SP2 to another PC running Xubuntu 6.06.1.

I get the following error when I try to double-click on the Ubuntu PC under the MSHOME network tree on the XP PC:

"\\Ubuntu is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path was not found."

I'm aware that this is a common problem, and having search this forum and others have tried various fixes, and am still not getting anywhere. I'd be grateful for any help! I'm a total Linux newbie so I hope I haven't made an obvious mistake ;-)

In trying to set up the networking, I have taken the simplest approach. I am aware that it is not the most secure, but I intend to improve security once I have everything working ok.

I have pretty much followed these [Samba instructions]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29") on the Ubuntu guide forum.

So, I have typed this:
sudo mkdir /home/public
sudo chmod 777 /home/public/
sudo mousepad /etc/samba/smb.conf

Then edited the "user" line of smb.conf to read:
security = share

Then added these lines to the end of smb.conf:
[public]
comment = Public Folder
path = /home/public
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

And finally restarted Samba as follows:
sudo /etc/init.d/samba restart

But when I then try to connect from XP I get the error mentioned above...

I do see the Xubuntu PC listed under the MSHOME network when browsing it on the XP PC. And I am also able to ping the Xubuntu PC by IP address.

Any ideas? I don't think it's a firewall problem as I don't believe the firewall is running (although am not sure how to check!)

A few hardware details (that may or may not be relevant):
- The PCs are connected via a router, and IP addresses are assigned via DHCP, although I have configured the router to use a static IP address for each PC's respective MAC address
- The Xubuntu PC is connected to the router via an ethernet cable, whereas the XP PC connects wirelessly (as the router doubles up as a wireless access point)

Some software details on the Xubuntu PC:
- It is running Xubuntu 6.01.1.
- In addition I have installed Samba.
- I have also installed SlimServer (to stream music - which works ok).

---

### Post by syrleb on 2006-11-27
hmmm, im having alot of problems too, my I.T teacher is going to tell me how to fix it all up, when he tells me ill get back to ya, good luck

---

### Post by Iowan on 2006-11-27
Might also try **guestok = yes**

---

### Post by geekygreen on 2006-11-27
I will be looking forward to the reply, also...

I am having a similar problem.  I am Brand new to Linux/Ubuntu, but I did get it installed on the Desktop machine.  

Sitting at the Desktop, which is running Ubuntu 6.06, I can copy files FROM the LAPTOP running WIN XP  TO the Desktop.  But I am unable to connect TO the desktop FROM the LAPTOP.  

The most recent response to attempting to connect is a pop-up window asking for a user name and password.  After locating some help in the New Users portion of the Forum, I have ensured there is an account on the Ubuntu machine with the exact windows username and password I am using.  

When I enter this information in the pop up window, the result is that the window goes away for a moment, then pops back up with the full path name, asking again for a password.](*,)     Entering the password again results in the same reaction...

Before adding a user to Ubuntu that matches the log on for the machine with "That other OS", I got the same errors as noted in a previous post.

Hopefully, one day I can find replacements or a shell to run the applications I am addicted to soon, and switch the Laptop to Ubuntu also...:-D

---

### Post by Hercules on 2006-11-27
I've solved it - and it was my fault!

I run Zone Alarm on the XP computer, and I hadn't added the IP address of the Linux computer to the Trusted Zones.

Once I did that, it started working (using the conf file settings as listed above)!

---

### Post by geekygreen on 2006-11-27
Glad you got it fixed.:D ..I have been using the graphic interface to SAMBA, perhaps I'll try what you did, and see if it works.  My symptoms were a bit different, however.  I did check and make sure the firewall would let my LAN connections happen, and that didnt help...

---

### Post by Hercules on 2006-11-27
Good luck!

I've now applied more security, and have followed this guide:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

It's all working fine. Next step is to learn about iptables so I can get security all finished...

As for your difficulties, perhaps you need to do some sort of "chmod" thingy to set permissions?

Is your main Linux user different to your Windows user? I chose different names for the two users so as not to risk causing confusion. (Although I have of course added the Windows user specifically as a user in Linux as the instructions state.)

---

### Post by syrleb on 2006-11-27
well im glad u figured out ur problem, im still ******

---

### Post by geekygreen on 2006-11-28
After going through the steps outlined in post #1, my system is now up and working great!:\\:D/ 

Note: if you try this at home, make sure MousePad is installed first....or, substitute an appropriate editor in place of "Mousepad".](*,)  

Also, take care that you dont change permissions in the Admin/users and groups that might prevent your logon user from having admin privleges, or you may have  to reload the whole shooting match...][-X  

Note that at this time I do have a user identified on the linux machine for both my login user on the XP laptop, and also a user for the computer name.  One day I will see if both are necessary, and post that info here...;)

---

### Post by Hercules on 2006-11-28
Glad to hear you've fixed it!

Sorry, should have pointed out that I substituted Xubuntu's "mousepad" for Ubuntu's normal "gedit" (because Xubuntu doesn't have "gedit" installed") =;

By the way, if you want to make your network more secure then [this article]("http://www.ubuntuforums.org/showthread.php?t=202605") is good. I followed the instructions, and have successfully changed the networking from the relatively open "security=share"  to the more secure "security=user".

So, I'm on a roll! All I need to do now is learn about iptables, then anti-virus, and then set up a remote connection of some sort (e.g. VNC).

---


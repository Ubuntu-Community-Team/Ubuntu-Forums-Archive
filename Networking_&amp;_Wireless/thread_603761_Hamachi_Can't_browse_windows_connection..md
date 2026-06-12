---
title: "Hamachi: Can't browse windows connection."
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Fireblend on 2007-11-05
Hey. I just installed Hamachi and it seems to work pretty well, I created a network in which my Ubuntu laptop and windows PC both exist. I can browse my laptop from my PC pretty well, as well as with any network. However, I can't seem to go the other way. The browse option seems to open in nautilus smb://[IP OF WINDOWS PC HERE], which doesn't seem to work. 

I have Samba and smbfs installed, and actually, these two computers are on a real network, but I connect to the PC by its name and not by its IP, which makes sense :p

So, any way to make Nautilus be able to display it? Or any other way to browse through these files? 

Thanks in advance!

---

### Post by powertower on 2007-11-05
Your configuration in windows seems to be setup incorrectly. Open up your network connections from the control panel and right click local area connection, then select properties. Verify that File and printer sharing for microsoft networks is installed allong with NetBIOS. Then double check your firewall settings in the control panel, select the exceptions tab at the top and verify file and printer sharing is selected as an exception. Try making a folder on your XP desktop then right clicking it and selecting sharing and security. Then enable it as a share. 
If you are still unable to browse it from smb://ipaddress then make sure all your anti-virus software is disabled. Or any third party firewalls such as Zonealarm. You may have to do a reboot of the XP machine afterwards.....Hope this helps

-POWERTOWER-

---

### Post by Fireblend on 2007-11-05
Actually, I just discovered something. If I copy that smb://ip.address.here and paste it on Firefox, I can get in the machine as if it were a ftp server, which makes me think it's actually Nautilus' fault, not being able to display the content, when Firefox can pretty well... However, I will check the settings on Windows, thanks for the help.

Ok, I have figured it out. Somehow, since I'm executing hamachi as "sudo hamachi" because it won't work otherwise, what is opening is root's file browser, which can't open smb:// stuff for some reason. On the other hand, if I copy paste the smb:// address to my user's file browser, it does work. So I'm gonna take the easy way and ask, how do I enable smb protocol addresses to be viewable on root's file manager?

---

### Post by Blind Tiger on 2008-07-06
Sweet news!  I had mirgrated to Ubuntu about a year ago and had attempted to install, configure, and connect to my Hamachi network that I had created while running XP. but was not successful!  I thought I had not done the install/config properly, but after taking another trial at it recently, I was able to get online, but still not able to browse -- getting the same nautilus error as described above.  But entering the smb address as a location in nautilus gets the job done!!  Or using Firefox via FTP!!!  Awesome.  If there's a better way to browse windows pcs from ubuntu using hamachi, let me know, otherwise, I'll stick with this method!!

---


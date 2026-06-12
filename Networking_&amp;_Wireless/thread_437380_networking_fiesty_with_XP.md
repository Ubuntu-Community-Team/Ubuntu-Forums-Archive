---
title: "networking fiesty with XP"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by ian_king2 on 2007-05-08
I've just installed Feisty as a dual boot oprion on my W2k machine. I've shared the ntfs disks as Read / Write.  I can see all he XP machines in the workgroup, acces shares etc. I can see the Feisty machine as a member of the workgroup from my XP machines, but am asked for a password when I try to connect - none of the user/password combinations I have set up on the Feisty machine will work, even if they are set a s administrators. 

Anyone any ideas for a fix? I really like Ubuntu, but can't use it unless I can access the shares on the machine from elsewhere.

---

### Post by Dr_Snapid on 2007-05-08
try 
sudo smbpasswd -a YOURUSERNAME YOURPASSWORD
on the feisty machine.
Then in windows, use this user/pass combo to connect. If you map a network drive you can have it save the user/pass.

---

### Post by mike2357 on 2007-05-08
In addition to the advice about running smbpasswd, look at the following:

1.  make sure the user names you added with smbpasswd are in the /etc/samba/smb.conf file, on the line for "valid users".  If you change this file, be sure to re-start samba with the following command:
sudo /etc/init.d/samba restart

2.  make sure the samba processes are actually running:
ps -eaf | grep smbd
should show lines that include /usr/sbin/smbd -D

Give all of the above a whirl (including the advice about running smbpasswd) and if you are still running into problems, post something back.

---

### Post by AlanR8 on 2007-05-09
I'm fairly new to all this, an old Doze hand and Linux of various flavours since Christmas 2006, finally settling on Kubuntu with the pre-release of Feisty in March.

I've now got three K boxes and and one XP box that I dare not swap for fear of a slow and lingering death at the hands of my wife. It's her machine.

This weekend I set out to get the networking sorted, and whilst it took a while, once I'd cracked it things are quite logical. I could always see the XP box from the K boxes but initially the Ks were not showing in the Workgroup. What I did to make things easier was went to Synaptics and made sure I had the following installed:

samba
samba-common
smbldap-tools

As I recall, I had to download samba and the tools. They were NOT installed by default.

Next I went to  [HTML][/HTML][http://www.webmin.com/download.html](http://www.webmin.com/download.html)[HTML][/HTML] and downloaded the Debian version of this incredibly useful tool that works in your browser of choice. 

Read the download instruction as there's a warning there that Webmin might complain about missing dependencies and it provides the apt-get to sort the problem.

Once Webmin is fired up in your browser, at [https://computer_name:1000](https://computer_name:1000) go down the menu on the left and select "Servers" then "Samba". You now have a graphical interface to work with. You can now make your selections, alter folder permissions, create shares and a lot more. Scroll to the bottom of the page and with a single click you can restart your samba server.

Webmin makes the alterations you need in your smb.conf file automatically and all should be well. However I did find a couple of things to watch out for and I'll share them here.

I picked up in these forums that you CAN'T log on twice to a 'buntu box with the same user name. The way around this is to make sure you allow "Guest" login and again this can be done in Webmin. 

You'll see there's a password that's looks pre-populated and it seems to be your existing main password. If that suits, and I suggest it will, save any changes. I'd RECOMMEND you then look directly at the smb.conf file. Again it can be done directly from Webmin, and make sure you have guest = yes in the file and that the line is NOT commented out with a ; or # symbol.

Restart samba and you should be in! I can now read and write XP to Kubuntu, Kubuntu to XP and Kubuntu to Kubuntu. In other words, as it should be.

Good luck

Alan

---

### Post by ian_king2 on 2007-05-09
Many thanks to everyone for your help - I've managed to see the Ubuntu machine and its home disk from the XP machines - now to see if I can access the NTFS shares.....

---


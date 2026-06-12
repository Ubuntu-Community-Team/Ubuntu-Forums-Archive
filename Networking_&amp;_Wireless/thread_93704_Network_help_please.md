---
title: "Network help please"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by scott63 on 2005-11-22
I have searched and have not found an answer, perhaps im just not seeing it. 
My question is how can a user on my local network access my Ubuntu pc with or without logging on? I prefer that they not have to enter a username or password to access shared files or folders. Thanks in advance for your help.

---

### Post by darth_vector on 2005-11-22
you can setup an ftp server on your computer. they will be able to access your shared files whether you are logged in or not.

---

### Post by scott63 on 2005-11-22
Thank you for your reply. I should have been more clear I would like the other pc's to be able to access the Ubuntu pc thru the network neighborhood or my network places. And also have accesss to the printer on the Ubuntu pc, like they can each other on the windows network with out the need for user names or passwords. This would make it much easier to transisition the other users to linux.

---

### Post by wylfing on 2005-11-22
So the other computers are Windows (probably Windows XP), right? The way to to go is to use Samba. You an do this by right-clicking on a folder you want to share and choosing Share folder. From the Share with drop-down list, choose SMB, select Allow browsing folder, and then -- if this is the first time you've done any sharing -- click the big button that says General Windows sharing settings. In *that* dialog enter the name of your Windows workgroup and (usually) specify that 'This computer is a WINS server' just to be complete. That should be enough to let your Windows computers see your shares.

I admit I don't know the GUI way to set up a printer for Samba, but on my network it's like this (the printer server runs Debian, which is close enough). Edit the file /etc/samba/smb.conf and go to the end of the file. There should be a prototypical [printers] section, which you can modify. (Remove the # before the start of each line to make it active.) Here is my [printers] section:
```
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

```

HTH

---

### Post by scott63 on 2005-11-22
I dont seem to be able to get my head around this. Ubuntu pc can access all XP Pro pc's on the network but they all get prompted for a password to access the Ubuntu pc. So I have no idea if the folders or printer are avaliable to them.

---

### Post by arphe_el on 2005-11-23
please share step by step procedures on how to do it (using ftp to access shared folders witin the network) thank you and GODspeed!

---


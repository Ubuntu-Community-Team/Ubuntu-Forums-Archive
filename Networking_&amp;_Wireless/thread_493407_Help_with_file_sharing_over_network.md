---
title: "Help with file sharing over network"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by alexv305 on 2007-07-05
I enabled Sharing and selected SMB and the unix one to be installed. I selected a folder and kept the default workgroup name but for some reason i cant access files from other computers...

How can I allow other computers to see my files?

---

### Post by alexv305 on 2007-07-05
Anybody?

---

### Post by NeoLithium on 2007-07-05
Hiya, 
I have the same basic idea setup for me and my wife's computer, and I just used the Samba guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org)   i'm not sure what steps you've already taken, though I DID set the shared folders as Read/Write/Execute for all users, since it's something i don't need to be careful with.  Not sure if that helps or not, but it's just something that works well with my setup.

---

### Post by scxtt on 2007-07-05
you have to allow a user to use samba: **sudo smbpasswd -a $USER** should allow your current user to use samba ...

---

### Post by alexv305 on 2007-07-05
Okay this is getting confusing. Ive read alot and still cant figure this out. I right click a folder and select share. Then I choose SMB for windows networks and no other computers are even picking it up now. I can access the internet perfectly but I am having trouble sharing files using the network. Ive rebooted and still nothing..

Someone help me please.

---

### Post by scxtt on 2007-07-05
try and connect directly to the samba share - don't rely on the "browsing" ... enter the IP address of the samba host directly ...

and be more specific about what you're trying to do, in terms of "connect A to B" (A is windows, B is linux) -- stiuff like that ...

---

### Post by alexv305 on 2007-07-05
Ok ill explain better. I am trying to share files from ubuntu to windows xp. Windows wont show the linux computer. Then I looked in the network on ubuntu and it doesnt show itself in the network folder but it does show other windows computers.

I want to set it up so windows users can access files on my ubuntu.

---

### Post by scxtt on 2007-07-05
if you're sure you've got the share set up correctly, do this:

from windows explorer: "map network drive" and enter the **\\<ip address>\<share_name>** and assign it a drive letter ... but make sure you've done **sudo smbpasswd -a $USER** and assign it a password (it's easiest if the username/passwords are the same for windows and ubuntu - but you can specify them in "map network drive") ...

---

### Post by alexv305 on 2007-07-05
ok what you just told me above doesnt work. i looked in the network on ubuntu and it doesnt show windows computers now. i think my network settings are messed up but for some reason i could still connect to the internet perfectly...

I have no idea whats going on..lol

---

### Post by scxtt on 2007-07-05
you could also try: \\<hostname> or \\<ip address> in windows explorer and you should see anything that's available ...

---

### Post by alexv305 on 2007-07-06
still nothing.....

by the way i appreciate the help :)

---

### Post by scxtt on 2007-07-06
are you sure samba is running?  do **ps -ef | grep "samba\|smb"** -- do you have a windows firewall (or even a linux one) running?  also, any changes to /etc/samba/smb.conf require a restart of samba (sudo /etc/init.d/samba restart) ...

---

### Post by alexv305 on 2007-07-06
Ok heres my update.

I tried restarted samba and now it shows myself on the ubuntu network as a computer but the windows computers arent picking it up. i tried typing the ip manually with the folder name (case sensitive) and still nothing.

I did however pick something up on ubuntu, i typed in the ip manually and it says natulius cannot display please use a different viewer. I also tried my browser and nothing. Normally it says cannot be found, but now its saying please use a different viewer because natulius cannot display..

???

---


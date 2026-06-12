---
title: "2nd Drive Mounted But Can't Share on Network?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Return Privacy on 2010-09-05
Hi all,
I just did new install of 10.04 on a Dell. Drive 1 is just the OS. I added drive 2 (sdb1), setup with Gparted. I followed articles and even got it setup to automount at bootup! I then set the permissions and ownership to 777, and now it lets me write files to it with no problems. The only problem I am having, is when I connect to this Ubuntu computer from my iMac (10.5.) I can not see the drive 2 (sdb1), all I see is the Home directory with Desktop, Documents, Downloads, Music, etc. folders. How come I can't see this drive 2? I forgot to tell you, I also had followed another article and installed and setup netatalk for afp. I did not setup anything named smb or samba. Does smb or samba setup automatically in Ubuntu 10.04? I'm assuming that the reason I can login and see the primary Ubuntu drive is because of afp? I wish it the Ubuntu computer would show up automatically in the Finder in iMac, but it won't. I  have to use "Go to server" and type in afp://10.0.1.3, and then put in the username and password for Ubuntu, then it shows up fine in iMac. If someone could help me get this second drive (sdb1) to show up on the network (iMac) I would really appreciate it! I've spent a lot of hours trying to figure this out, and I am stuck...

---

### Post by Ozymandias_117 on 2010-09-05
> **Return Privacy said:**
> Hi all,
I just did new install of 10.04 on a Dell. Drive 1 is just the OS. I added drive 2 (sdb1), setup with Gparted. I followed articles and even got it setup to automount at bootup! I then set the permissions and ownership to 777, and now it lets me write files to it with no problems. The only problem I am having, is when I connect to this Ubuntu computer from my iMac (10.5.) I can not see the drive 2 (sdb1), all I see is the Home directory with Desktop, Documents, Downloads, Music, etc. folders. How come I can't see this drive 2? I forgot to tell you, I also had followed another article and installed and setup netatalk for afp. I did not setup anything named smb or samba. Does smb or samba setup automatically in Ubuntu 10.04? I'm assuming that the reason I can login and see the primary Ubuntu drive is because of afp? I wish it the Ubuntu computer would show up automatically in the Finder in iMac, but it won't. I  have to use "Go to server" and type in afp://10.0.1.3, and then put in the username and password for Ubuntu, then it shows up fine in iMac. If someone could help me get this second drive (sdb1) to show up on the network (iMac) I would really appreciate it! I've spent a lot of hours trying to figure this out, and I am stuck...

Try mounting the second drive in the directory you're sharing. 

Samba is for networking with Windows computers.

---

### Post by Return Privacy on 2010-09-06
Hi, thanks for the reply. I had to add /media/backups (the name of the second drive)in the afpd.conf file. 
I can now see it and log into it from the iMac. The only problem I am still having is I can't get the Ubuntu computer to automatically show up in finder on the iMac. I know netatalk must be working ok because I can manually log into the Ubuntu's Home directory, and now the 2nd drive. Can anyone help me get this avahi to show the Ubuntu computer automatically on the network? I must have done something wrong. I am using a new install of Ubuntu 10.04, I installed netatalk, and avahi according to articles I read. I think I messed up the avahi somehow?

---

### Post by Return Privacy on 2010-09-06
Hi, I still haven't been able to figure out why my new Ubuntu 10.04 computer won't automatically advertise thru avahi to the network? I can manually login to it from my iMac, by going to "Go to Server" and typing in the ip 10.0.1.3 and putting in the Ubuntu username and password. I just can't get it to advertise or broadcast itself to the network like it is supposed to using netatalk and avahi. I've followed all of the tutorials I can find on this, but nothing works. Even if I issue the command to restart avahi daemon, Ubuntu still isn't seen in the iMac's finder window? Because I can manually login to it, I am assuming that netatalk is working properly. I've even tried to issue the command to restart netatalk first, then restart avahi, but still nothing? This is driving me crazy! Please Help, Thanks

---

### Post by Return Privacy on 2010-09-10
Hi all,
I kept searching for answers to my problem. Someone(I forget who) suggested to go in and look at the "daemon.log". When I did, I saw an error when it was trying to load the avahi-services.afpd file. It said it was a problem with line 8. Since I had originally just copied and pasted that file during the setup, I figured I messed up. Then I)) read where some people said that when following the how-to's on setting this all up, you have to be careful because sometimes the sytax code is messed up when posted on blogs and some online places. So, I went in and erased the avahi services.afpd file, and got it from another post, and pasted the text in the file. Then, I restarted netatalk and avahi, and it worked perfectly! I can even re-boot the computer and it works automatically like it is supposed to. So, I hope this helps other people with this problem, look at your /etc/var/daemon.log and look for errors when afpd file tries to load. You may have to re-do your file like I did. I hope this helps.

---


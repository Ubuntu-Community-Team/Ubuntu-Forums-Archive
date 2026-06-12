---
title: "Dual boot &amp; file sharing help"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by nowhere@cox.net on 2007-12-01
Hi all,

I have a two part question:

1.
I have a machine that I dual boot between XP and Gutsy. I have a large external drive connected to it with our music library on it. I would like to be able to access it from the other machines on my network. I have file sharing set up in XP andit works. I have samba set up in Gutsy and it works. Is there a way to make both boot schemes look the same on the network so the machines on the network don't care which way Im booted?

2. MythTV access to the music share. MythTV is running Fedora Core 7. When booted in XP, I can mount the share just fine on the mythbox. However, when my machine is booted to Gutsy, I cannot for the life of me get the Ubuntu share folder mounted in Fedora. sshfs doesn't exist on the fedora machine and can't find it using yum. mount -t cifs gives me a permission denied error 13 no matter what I do! 
Also, is there any suggestions on a little script that will automatically mount the music folder regardless of which machine is booted and reconnect if I reboot?

Thanks a ton!
Eric

---

### Post by victorbrca on 2007-12-01
1- If you are using SMB, what's the share name you have on XP and Gutsy? If the name is the same, they should appear as the same for the other machines. How about your hostname on both boots?

2- Haven't used MythTV, but are you using SMB? Any password authentification required?



Vic.

---

### Post by nowhere@cox.net on 2007-12-11
Thanks for the reply Victor,

I am using smb and I am trying to make sure the names/paths are the same on both shares whether booted in Windows or Ubuntu. 

I'm spending more and more time in Gutsy and less in Windows so this is a problem for the wife who likes to use the MythTV Fedora box to play music located on the external drive connected to my machine. 

I would move the drive to the Fedora box except I need the higher speed access on my machine.

Thanks!
Eric

---

### Post by victorbrca on 2007-12-11
1- Have you tried using IP address instead of host name?

2- You can try to mount as CIFS:

```
sudo apt-get install smbfs
sudo mount -t cifs //IP/sharename /media/sharename -o guest,iocharset=utf8
```

More info on mounting [here.]("http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba")


Vic.

---


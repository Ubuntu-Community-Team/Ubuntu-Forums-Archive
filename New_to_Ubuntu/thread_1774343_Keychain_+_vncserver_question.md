---
title: "Keychain + vncserver question"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by bichamar on 2011-06-03
Hello,


I am an complete beginner with both linux and these forums so if I did miss something please point out what.

So onwards to the main question! I just bought light low performance pc and thought to make it an nice o' homeserver for picture sharing and backups and so on. Installed xubuntu 11.04 and got it working nicely, got samba shares to work etc ... but now I'm having difficulties with keychain and vncserver. 

1)Keychain keeps bugging me about the password even though I select the "auto password when login" or similiar. I also have computer to login automaticly so if/when it goes out of power and gets up again I can get in there from outside my home network. So is there a way to get it login to keychain automaticly when logged in computer, I need this for wireless network connection computer is using.

2) I get vncserver (x11 and/or tightvnc) workin but cant figure out how to get it start on computer restart, did install tightvnc with "sudo apt-get install tightvncserver" and got it working ok but when i reboot coputer its not on, there is nothing about vnc in /etc/init.d if that info is helpfull.

So any help with these  2 things would be really nice. Also any good links to how-to set up mail server that downloads mails and shares them as one mailbox would be awesome.

Cheers.

Bichamar

---

### Post by jtarin on 2011-06-03
> 2) I get vncserver (x11 and/or tightvnc) workin but cant figure out how to get it start on computer restart, did install tightvnc with "sudo apt-get install tightvncserver" and got it working ok but when i reboot coputer its not on, there is nothing about vnc in /etc/init.d if that info is helpfull.Preferences>Startup Appliations>Add

---

### Post by Toz on 2011-06-03
> **bichamar said:**
> 1)Keychain keeps bugging me about the password even though I select the "auto password when login" or similiar. I also have computer to login automaticly so if/when it goes out of power and gets up again I can get in there from outside my home network. So is there a way to get it login to keychain automaticly when logged in computer, I need this for wireless network connection computer is using.
[http://ubuntuforums.org/showpost.php?p=10213535&postcount=4](http://ubuntuforums.org/showpost.php?p=10213535&postcount=4)

> Also any good links to how-to set up mail server that downloads mails and shares them as one mailbox would be awesome.
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by bichamar on 2011-06-03
Thank you very much for your answers, will try them when i get home to my server. 

jtarin: what should i add in there i tried to add the .vnc/tightvnc/xstartup or similiar, not sure about exact string since im not at the computer right now, but that didnt help. I Couldn't connect to server with tightvnc before I ran it. I will give it a second try and see if i fumbled something there.

---


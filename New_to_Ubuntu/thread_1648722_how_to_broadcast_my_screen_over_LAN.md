---
title: "how to broadcast my screen over LAN"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by itsols on 2010-12-19
Hi,
I'd like to make a few demos of my work to others on the LAN. i.e., while I explain something, I want the other users either Ubuntu or Windows to see what I do.

Is this possible? BTW, I only want them to VIEW my screen and not have access to anything beyond that.

---

### Post by Wtower on 2010-12-19
Take a look at the following links:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

I don't know if anyone has something to add.

Regards

---

### Post by itsols on 2010-12-19
Thank you for your fast inputs...

I'm desktop sharing is all that needs to be done, then why do we have to install VNC? Can't we just use the remote desktop feature instead?

Sorry if this sounds crazy but I'm honestly ignorant in this area. Looking back a couple of years, I think I was unsuccessful getting VNC to work but I don't know this time :)

Thanks again!

---

### Post by 12apennachi on 2010-12-19
Just go to System->Preferences->Remote Desktop. Deselect "Allow others to control you desktop". Tell them (the clients) to go to Applications->Internet-> Remote Desktop Viewer. Tell them to type in the ip address given in remote desktop preferences.

Oooooooh. Kinda didn't read the windows part. just give them a flash drive with ubuntu on it haha.

---

### Post by Wtower on 2010-12-20
The remote dekstop feature of Ubuntu uses the simple VNC protocol as far as I know. On the other hand, windows remote desktop is using its own protocol. If you enable the remote desktop on your Ubuntu machine you should be able to access it with any vnc viewer on any OS.

Regards

---


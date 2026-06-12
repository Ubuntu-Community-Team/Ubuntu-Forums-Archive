---
title: "Mounting Windows shares"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by ukprawn on 2008-04-28
Having some issues with accessing Windows shares and mounting said shares.

I installed the smbclient package. Everything worked fine; could see and access my Windows share. Then I started mucking round attempting to mount the Windows share. Followed some tutorials and tried to mount the share using the command:

smbmount //albert/albums /home/prawn/Music/albums -o username=guest,uid=1000,mask=000

After doing this I could see the share from within the local filesystem however when I browsed to the share and attempted to enter one of it's subdirectories the file manager (forget the name now :P) would lock up. After attempting this I could not effectively navigate to any folder, local or remote, without the file manager or my terminal getting "stuck", nor could I make changes to any files/dirs so I restarted the machine.

Can anyone more clued up see where I am going wrong? It would also be nice to mount the shares at boot; I had a play around doing so by editing my fstab but it didn't seem to work. Would greatly appreciate any help.

---

### Post by Swiftfeet8 on 2008-04-28
Not sure what has all happened with your computer but give this a try:

Go to "Places > Connect to Server..."
For "Service Type" choose "Windows share"
Fill in your server name (or IP address)
Then fill in the share name

Once you click "OK" you will be prompted for your username/password and domain/workgroup.  Fill out this information and then you can choose whether to remember or forget your password.  Then click "Connect" and you should be connected to your share.

This may or may not work depending on what you did with setting up the share from that other tutorial.  

This will put an icon on your desktop and under "Places".  Hope this helps.

---

### Post by Iowan on 2008-04-29
Dunno if it'll help - or if it's the source that caused problems... Check the link in my signature (observing that CIFS is replacing SMBFS).

---


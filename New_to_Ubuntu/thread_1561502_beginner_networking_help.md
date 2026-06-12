---
title: "beginner networking help"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Kyluke on 2010-08-26
hey guys I have a question.

I have installed samba, smb and nfs and yet I still am not having any success entering a network with windows pc's.

What am I doing wrong??

Another problem is the linux networking which also appears not to be working. This is from a fresh install of 10.04.

Any Ideas????

---

### Post by mikewhatever on 2010-08-26
> 
not having any success entering a network with windows pc's

linux networking which also appears not to be working


These descriptions are not very informative. What  happens exactly when you click on 'Network' in the file browser?

---

### Post by Kyluke on 2010-08-26
Nothing it just has the "Windows Networking" icon which when I open it doesn't work.

I don't know how to be more descriptive than that...

I'm new to this

---

### Post by mikewhatever on 2010-08-26
Stating what happens exactly is a good start, especially if there are error messages. Even if nothing happens, just say 'nothing happens'.;)
You shouldn't need to install samba, smb (no such package) or nfs to view files on a Windows computer from Ubuntu, since the smbclient package is installed by default.

---

### Post by Kyluke on 2010-09-05
Well after connecting my laptop to a network which is primarily filled with windows pc's, I still cannot see "shared" files nor can they "see" my shared files.

I have attached two screenshots which may be of help.

---

### Post by cogier on 2010-09-05
Have you set up shared files on Ubuntu?

Go to Nautilus, right click on a folder you want to share select **Properties**, select the **Share** tab and apply the share by checking the box. Ubuntu will say that it needs to load the software and reboot.

After the reboot you will need to set up the share again.

---

### Post by Kyluke on 2010-09-05
I will give that a try.

If that does not work, any other ideas?

---

### Post by halitech on 2010-09-05
I would check the IP addresses on the Ubuntu computer and the windows computers to make sure you are all on the same network (ie. 192.168.0.xxx) and then see if you can ping the other computers. Also check the windows computers for firewalls that could be blocking you.

---


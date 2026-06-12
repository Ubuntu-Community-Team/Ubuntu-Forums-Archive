---
title: "root access"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by ZeroDeficit on 2007-06-07
I currently have ubuntu as a second OS.

I found drivers for a WLAN USB stick I will be using to network. When I opened the read me, it said to copy the files to /lib/firmware/zd1211.

When I located the folder, I created a folder on the desktop called zd1211 and put the files in it. Then I tried to drag the folder into the /lib/firmware/ folder and it said I do not have permission to write to this folder. 

After consulting the properties of /lib/firmware/ folder under permissions tab, the owner was labled as "root" and I am unable to alter anything in it. At the bottom it says: "You are not the owner, so you can't change these permissions."

I only set up 1 account on ubuntu and I am currently logged into it. How could I not be the owner?

Is there a default owner?

Is there another way to unlock that folder so I can write to it?

Thanks,
   Cam

---

### Post by steeleyuk on 2007-06-07
Root is the administration account in Ubuntu. It allows only specified users to make change to certain areas of the filesystem and prevents unauthorised access (in some cases) and modification of files.

To write to the folder, you'll want to open the terminal and type:

gksu nautilus /lib/firmware

You will be prompted for your password and then given write access to the folder.

---

### Post by Catsworth on 2007-06-07
Or, you could (from the command line):

```


sudo cp -r /home/<yourUserName>/Desktop/zd1211/ /lib/firmware/


```

I think that should work.  You could probably just copy and paste from above.

---

### Post by ZeroDeficit on 2007-06-07
i tried gksu nautilus /lib/firmware and it opened a window, should i just drag the folder into it?

---

### Post by ZeroDeficit on 2007-06-07
i will try the sudo cp -r /home/<yourUserName>/Desktop/zd1211/ /lib/firmware/ tomorrow to see if it works, i currently do not have access to the machine using ubuntu, but this should just copy the zd1211 folder from the desktop to the lib/firmware folder which is currently locked to me. does the administration account have to be logged in seperate from my usual account with the same/different p.w.

thanks for your help guys(or girls)

---

### Post by chili555 on 2007-06-07
I don't think dragging or copying the *folder* into /lib/firmware is going to do it. There is currently a folder:```
/lib/firmware/2.6.20-16-generic/zd1211/
``` and I think you want to copy the individual files here.```
sudo cp -r /home/<yourUserName>/Desktop/zd1211/firmware/* /lib/firmware/2.6.20-16-generic/zd1211/
```You could also try copying the individual files to */lib/firmware/* but you want to avoid ending up with folders in folders in folders that can't be located and loaded.

---

### Post by ZeroDeficit on 2007-06-08
thank you so much Catsworth, the folder copied to there. according to the readme file, it needs to be loaded. is that automatic?

---

### Post by Catsworth on 2007-06-08
Not sure, I would try a reboot and see what happens.

---


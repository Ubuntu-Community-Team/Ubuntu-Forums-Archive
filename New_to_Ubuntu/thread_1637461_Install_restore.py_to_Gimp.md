---
title: "Install restore.py to Gimp"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Inisfad on 2010-12-04
I've been reading about a plug in for Gimp, for the restoration of old photos.  I have been trying to install this all day.  I downloaded the file restore-py to my desktop.  Original instructions were to install to home/me/gimp 2.6/plug-ins which I did, however although the file shows there, it does not show in Gimp/preferences/folders/plug-ins.  Then I read I should install this to usr/lib/gimp/2.0/plug-ins.  When I try to drag and drop this, I am getting access denied, no permission, etc.  Does anyone know how to install this plug in?  I understand that I am supposed to make this script executable, but I don't know how or where to do that.  I am a real newbie.  Please help.

---

### Post by Nytram on 2010-12-04
Hi Inisfad

Probably the easiest, and safest, way to move the file is using the terminal.

First to make the script executable:

> sudo chmod +x restore-py

And then to move it into your Gimp plugins folder:

> sudo mv restore-py /usr/lib/gimp/2.0/plug-ins

You'll need to change the current directory to your desktop before doing the above:

> cd ~/Desktop/

---

### Post by Inisfad on 2010-12-05
Thank you!!  Worked a treat.  I had these instructions doing the chmod thing, but no one had ever given the first step of changing the directory to the desktop.  Ah, all is well now.  Thanks very much for the clear directions!

---

### Post by Nytram on 2010-12-05
No problem glad to hear it worked for you.

---

### Post by philinux on 2010-12-05
What a cracking plugin. The before and after example pics are well good.

---

### Post by Inisfad on 2010-12-07
Surprised there is not more info on it on either Gimp forum or on the internet.  Really beyond excellent for restoring old photos/transparencies.  Highly recommended!!!

---


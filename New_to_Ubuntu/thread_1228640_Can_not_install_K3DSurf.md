---
title: "Can not install K3DSurf"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Tapas Bose, India on 2009-08-01
I installed K3DSurf from Add/Remove program, but when I am trying to launch K3DSurf from Application->Education->K3DSurf, I am seeing a tab appers on the panel saying 'starting K3DSurf' and the cursor is busy but after a while nothing is launched and the above mentioned tab is disappeared from the panel.  
 Please help me. I can not figure it out. Thanks in advance.
 

 I also be great full if anyone tell me how to install K3DSurf from terminal. Is there any other way to install K3DSurf ? Is there other software which is needed for running K3DSurf ?

---

### Post by Liolikas on 2009-08-01
```

sudo apt-get install k3dsurf
k3dsurf
scrot

```
You get sxreenshot post it then here.

---

### Post by Tapas Bose, India on 2009-08-01
Thank you Liolikas for quick reply. 

I did everything as you mentioned. In the terminal when I type k3dsurf the following event occurred :
get fences failed: -1
param: 6, val: 0
Segmentation fault

Next I type scrot, then the following information shown :
The program 'scrot' is currently not installed.  You can install it by typing:
sudo apt-get install scrot
bash: scrot: command not found

Then I type
sudo apt-get install scrot

And install 'scrot'. Lastly I again type k3dsurf but the same event occured as mentioned above.

Now what to do?

Thanks in advance.

And also the K3DSurf is not launched as I told in my 1st post.

---

### Post by Tapas Bose, India on 2009-08-01
Thank you. This K3DSurf is installed lastly.
One more information I would like to share, I have cairo dock and when I click on K3DSurf icon it comes into the dock, and when I click on that dock icon it is launched. But some black object appears on the bottom and the right side of the K3DSurf window.

---


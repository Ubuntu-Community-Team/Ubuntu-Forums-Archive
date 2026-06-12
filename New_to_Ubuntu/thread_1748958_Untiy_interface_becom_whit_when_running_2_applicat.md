---
title: "Untiy interface becom whit when running 2 applications"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2011-05-04
Hello every one,

I've installed ubuntu 11.04 this is not a clean install I installed 10.10 and upgraded to 11.04.

It's working flawlessly but I've come acros a issue that really nags me I tried to resolve this but to no avail. So thats why I'm seeking help here please read carefully and help to find a solution.

The issues this when I'm running a application in one workspace in maximized mode I can't open another program in that same mode the application work area becomes a blank white sheet only the top unity panel and the buttons are available.

Funny thing is that when I reduce the size of the second window it becomes available and this happens vise versa as well If I'm running a second window in the back ground and try to reduce the size of the first window it get a white overlay.

To give more clear idea of what's happening I've attached 2 print screen to this post and in the second one the application is in maximized mode so thats why it seems like a blank shot.

I'm using unity with nVidia card the model is GeForce 6100 nForce 405 if this helps and this a onboard VGA.

Please help me with this tahnk you.

---

### Post by sadaruwan12 on 2011-05-04
Can any one help me

---

### Post by r-senior on 2011-05-04
It's a bug in the current Nvidia driver. You can workaround by downgrading to v173 of the driver or by using the free Nouveau driver.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)

Fire up "Additional Drivers" and see what it offers as options. If you aren't sure, post a screenshot for advice.

---

### Post by fabricator4 on 2011-05-04
> **sadaruwan12 said:**
> 
The issues this when I'm running a application in one workspace in maximized mode I can't open another program in that same mode the application work area becomes a blank white sheet only the top unity panel and the buttons are available.

Neither of the applications in the first screen shot are maximised, though the virtualbox window is as large as it needs to be for the VM screen resolution.

It really looks more like a Firefox problem than an Ubuntu/Unity one, unless you've seen other programs doing the same.  You've only demonstrated the bug in Firefox here.

The main two things to check in Firefox is that there are no Firefox processes already running that are conflicting:
```

sudo killall -v firefox
```
Or possibly reboot.

Secondly, clear all the firefox configuration by making the hidden .mozilla directory unavailable.  You can move .mozilla to a backup if you like.  After running the killall command:

```
mv ~/.mozilla ~/.mozilla_backup
```

Or use nautilus to change the name if you wish.  Either way Firefox should not be running when you do  this.

Now when you restart Firefox it will recreate the configuration files from scratch.

Chris

---

### Post by sadaruwan12 on 2011-05-04
> **fabricator4 said:**
> Neither of the applications in the first screen shot are maximised, though the virtualbox window is as large as it needs to be for the VM screen resolution.

It really looks more like a Firefox problem than an Ubuntu/Unity one, unless you've seen other programs doing the same.  You've only demonstrated the bug in Firefox here.

The main two things to check in Firefox is that there are no Firefox processes already running that are conflicting:
```

sudo killall -v firefox
```
Or possibly reboot.

Secondly, clear all the firefox configuration by making the hidden .mozilla directory unavailable.  You can move .mozilla to a backup if you like.  After running the killall command:

```
mv ~/.mozilla ~/.mozilla_backup
```

Or use nautilus to change the name if you wish.  Either way Firefox should not be running when you do  this.

Now when you restart Firefox it will recreate the configuration files from scratch.

Chris

No I've seen this with LibreOffice pidgine and I'm well sure that this is not a FF4 issue.

THX for the replys

---

### Post by sadaruwan12 on 2011-05-04
> **r-senior said:**
> It's a bug in the current Nvidia driver. You can workaround by downgrading to v173 of the driver or by using the free Nouveau driver.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)

Fire up "Additional Drivers" and see what it offers as options. If you aren't sure, post a screenshot for advice.

This is the issue I'm having right now so it's a bug in the nVIDIA driver

THX I'll if your solution works

---

### Post by sadaruwan12 on 2011-05-04
> **r-senior said:**
> It's a bug in the current Nvidia driver. You can workaround by downgrading to v173 of the driver or by using the free Nouveau driver.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)

Fire up "Additional Drivers" and see what it offers as options. If you aren't sure, post a screenshot for advice.

r-senior Thank you very much this worked for now hope the next driver release solves this issue.

---


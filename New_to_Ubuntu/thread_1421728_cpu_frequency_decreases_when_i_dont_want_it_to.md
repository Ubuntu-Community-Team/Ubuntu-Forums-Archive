---
title: "cpu frequency decreases when i dont want it to"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by libihero on 2010-03-04
when watching some videos online, the video will run smoothly when my cpu is at 1.6 GHz, but when it goes down to 800 GHz, it starts to lag.  i used the cpu scaling panel applet to make the cpu 1.6 GHz, but it still scales down to 800.  how can i make it stay up without going down?

---

### Post by kouter on 2010-03-04
i use kpowersave on my kubuntu laptop, easy to manage different profiles (performance, power, acoustic, presentation) and power management settings, just not sure what the dependencies may be to run it in ubuntu.

---

### Post by Joshcush on 2010-03-04
Use the applet to set the processor to run on performance.

The current setting is probably set to Ondemand.

To do this, simply click the applet, click Performance then input your password.

Hope this helps

---

### Post by wojox on 2010-03-04
Have you tried setting it to performance?

---

### Post by libihero on 2010-03-04
i have tried to put it to performance.  it would go to 2GHz, but then it would keep going down again, and my video would lag everytime it went down

---

### Post by Jordanwb on 2010-03-04
There is a script that runs at boot time that sets the CPU governor to ondemand. Try 

```
sudo update-rc.d ondemand disable
```

and reboot

---

### Post by wojox on 2010-03-04
> **Jordanwb said:**
> There is a script that runs at boot time that sets the CPU governor to ondemand. Try 

```
sudo update-rc.d ondemand disable
```

and reboot

Thank you. Now it's persistent. :D

---

### Post by shae on 2010-03-04
I would suggest you check your temps to be sure.  Your CPU could be getting too warm.

---

### Post by Jordanwb on 2010-03-04
> **wojox said:**
> Thank you. Now it's persistent. :D

No problem. The ondemand BS was confusing the hell of me before I found that script.

---

### Post by libihero on 2010-03-04
> **shae said:**
> I would suggest you check your temps to be sure.  Your CPU could be getting too warm.

ok that might be it, my computer has had problems with overheating before lately, so i guess i'll just trust my computer on this one! thanks :)

---

### Post by Jordanwb on 2010-03-04
FYI the ondemand script is a result of a Ubuntu Brainstorm or a "bug" report (can't recall which, probably brainstorm).

What's this BS about security tokens not being passed?

---


---
title: "Running commands when the laptop resumes"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by charliehorse55 on 2009-03-02
I've googled and tried to figure out how to do this, and seem to have been able to half figure it out. 

I want to whenever the computer comes out of suspend to restart the appletouch. 

I can do it in terminal like so:
```

sudo modprobe -r appletouch
sudo modprobe appletouch

```
Now, if I wanted that to be a shell script, how would it change? Then I will put it in the /etc/pm/sleep.d dir, then chmod +x it. 

Can someone please just make a code box with what the contents of the shell script would be? I would really appreciate it!

---

### Post by Crafty Kisses on 2009-03-02
I guess you could technically edit your modules manually, you can run the following:
```
sudo gedit /etc/modules
```
Then add "appletouch" at the bottom of the file and save it, see if that works.

---

### Post by charliehorse55 on 2009-03-02
> **Codename said:**
> I guess you could technically edit your modules manually, you can run the following:
```
sudo gedit /etc/modules
```
Then add "appletouch" at the bottom of the file and save it, see if that works.
Will this restart the modules when the laptop comes out of suspend? Because the problem i'm having is that sometimes when I come out of suspend the mouse will not work. If i navigate to terminal and reboot the mouse like previously stated, all is well. I just want to automatically reboot the mouse everytime the computer comes out of suspend.

---

### Post by SamNSane on 2009-03-03
> **charliehorse55 said:**
> Will this restart the modules when the laptop comes out of suspend? Because the problem i'm having is that sometimes when I come out of suspend the mouse will not work. If i navigate to terminal and reboot the mouse like previously stated, all is well. I just want to automatically reboot the mouse everytime the computer comes out of suspend.

I'll be interested to see if you get a resolution to this. However, I think that you're going to have to restart it manually when you come out of suspend. The whole idea of suspend / hibernate is that it save the system state as is, then restores it. Your problem seems to be that the device drivers are not fully compatible with the suspend function. If you're to get this to work the way you envision, I think that something will have to make the suspend state / drivers work properly together.

You see the same sort of behavior with network interface cards (wired and wireless), for instance. Some systems can resume and regain their network connections, and some can't. When they can't, it's the fault of the drivers.

At least that's the way it appears to work. I'd be delighted to find out that I'm wrong.

---


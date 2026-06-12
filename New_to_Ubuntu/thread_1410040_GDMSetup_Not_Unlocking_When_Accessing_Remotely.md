---
title: "GDMSetup Not Unlocking When Accessing Remotely"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Excedio on 2010-02-18
Hey everyone, I need a little bit of guidance here. I am on a Windows work station now and I'm attempting to access my Ubuntu box at home. I can SSH in to it, but VNC is acting up. I would like to restart my Ubuntu box at home, but I know that if I do that I will not have access to type in my username & password. My solution for this is to enable my box to Login Automatically. Here's how I'm trying to accomplish this:
 
I have PuTTY installed and I have Xming installed. I then use PuTTY to SSH in to my Ubuntu box and then enable X11 forwarding through Xming. I type in ```
gdmsetup
``` and it brings up my login settings, but when I click Unlock nothing happens. So I decided to try ```
sudo gdmsetup
```hoping that it would be unlocked...no dice.
 
Can anyone give me some advice here? Is there a command I can use in the Terminal that will set my computer to login automatically?

---

### Post by cariboo on 2010-02-18
I know this may be not what you are looking for, but if you have openssh-server installed, why not use X-forwarding?

```
ssh -X user@server_ip_address
```

Then at the prompt type the name of the program you want to use.

---

### Post by Excedio on 2010-02-19
That is what I do when I'm using a Mac or another Linux box. However, Windows does not use X11 natively. Which is why I'm using PuTTY + Xming. Plus, I typically use```
ssh -X -C user@ip_address
```

---


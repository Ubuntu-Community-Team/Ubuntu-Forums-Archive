---
title: "Installed and nothing happens"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by breauxlg on 2009-02-13
I installed 8.1 and it told me to reboot. When it reboots, it comes to a pale orange background and the mouse cursor is visible and responsive, but that's all I see. Any ideas?

---

### Post by vikramaditya on 2009-02-13
Can you boot into recovery mode?

---

### Post by breauxlg on 2009-02-13
How?
 I am really, really new to this. I just downloaded the pocket guide, but haven't printed it yet

---

### Post by breauxlg on 2009-02-13
Figured out recovery boot. The esc message goes by pretty fast. Am booting to recovery now.

---

### Post by breauxlg on 2009-02-13
Tried to repair packages. It says it can't connect to the web site for the updates. Any ideas again?

---

### Post by Doug11 on 2009-02-13
You could try to boot from the cd again and do a disc check and see if your disc is ok.

---

### Post by breauxlg on 2009-02-13
I'll try that.
Thanks,
Lynn

---

### Post by breauxlg on 2009-02-15
Now it boots and asks for user and password, but after that, blank screen. I reloaded after verifying CD and had it analyse the disk to make sure there are not problems on the hard drive.

---

### Post by oldos2er on 2009-02-15
What are your hardware specs? Have you tried booting into recovery mode, and running xfix?

---

### Post by breauxlg on 2009-02-15
Yes, I will.

---

### Post by breauxlg on 2009-02-15
I ran xfix and it seemed to do something. Didn't give me an error that I could see, then let recovery reboot and it does the same thing.

---

### Post by breauxlg on 2009-02-15
I downloaded 8.03 and guess I should try to load that release.

---

### Post by abn91c on 2009-02-15
> **breauxlg said:**
> Tried to repair packages. It says it can't connect to the web site for the updates. Any ideas again?
if you have a wired broadband connection at the prompt type```
sudo dhclient eth0
``` to activate your network, also you may need to remove compiz to log in```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo reboot
```

---

### Post by breauxlg on 2009-02-16
I zapped 8.1 and loaded 8.4 and it is working now. Thanks for the suggestions.
Lynn

---


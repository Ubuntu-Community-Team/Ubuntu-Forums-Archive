---
title: "suddenly can't log in!!! - &quot;power manager has stopped responding&quot;"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by pythonscript on 2010-10-06
As of a few hours ago, I cannot log into the Ubuntu side of my laptop. It takes almost a minute for the log in screen to appear (before, it took about 15 seconds from the time I selected the grub entry) and when I try to log in, I get a window saying that the "power manager has stopped working". It gives me three options: Lock Screen, Cancel, Logout Anyway. All three options simply freeze when I select them. 

I can switch to a virtual terminal, and I killed the power manager processor with **sudo kill**, but when I switch back to tty7, it's still frozen. Any ideas? I can't log in **at all**, so doing much troubleshooting graphically from within is impossible now. 

Thank you for the help! I haven't updated my netbook yet, but I'm worried that it might have been a recent update. This is my production machine that's stopped working... so I don't want to knock out any of my other machines!

---

### Post by pizza-is-good on 2010-10-06
Have you tried to boot using recovery mode?
What happens if you boot a live CD?

Make sure you are plugged in...

~pizza

---

### Post by pythonscript on 2010-10-06
I can boot a live CD fine, and the win7 side of my machine boots just fine. How can I boot into recovery mode? My GRUB menu doesn't have an option to and I can't remember or find the parameter(s) online. 

I've had my laptop plugged in this entire time, so hopefully that isn't the problem. 

Thank you!

---

### Post by Locke_99GS on 2010-10-06
log into a VT and check available space on /

```

df -h

```

When / get full (99%-100%) it'll prevent you from logging in. This has happened to a couple of my buddies resulting in varying login issues. I, personally, have had the power-manager fail when / filled up.

---

### Post by luvshines on 2010-10-07
This happened with me too when I placed a large file in the linux partition which was mounted from windows(ext extension)

This may relate to "Locke_99GS" comment

---

### Post by pythonscript on 2010-10-08
I have 7.5G free space on my Linux partition, so I don't think that's the problem. Since it's a standalone program though, I just removed it, and I haven't had any problems since. It's certainly a blanket solution, but I needed the machine running immediately, and as of now it is. Thank you for the help!

---


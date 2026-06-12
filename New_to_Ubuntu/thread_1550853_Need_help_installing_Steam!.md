---
title: "Need help installing Steam!"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by PumaMania on 2010-08-11
Hey! I'm a very new Ubuntu user and I really want to use Steam on Linux!

I have the SteamInstall.msi file on my desktop and I have Wine Installer, my "virtual" c:/ drive and all that good stuff done thanks to a few confusing command prompts! However when I run the .msi file with Wine Windows Installer or whatever, I get an error saying "Incorrect Command Line Parameters". What do I do from here? D:

---

### Post by J V on 2010-08-11
Wine is too complicated...

Install the playonlinux package, it will let you install steam easily (point n click)

---

### Post by PumaMania on 2010-08-11
It says I need 3D acceleration. What does this mean?

---

### Post by Failboat88 on 2010-08-11
Something your graphics card enables. **glxinfo | grep rendering** to check if it's on. 

According to this, [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html), nvidia cards won't have it enabled by default. The link has instructions on how to enable ati or nvidia. When your done you can use the code above to double check.

Edit: I just noticed the documentation is for an older version of Ubuntu. It may still apply. You could paste the results of **lspci** from terminal to see what card you have. Then someone else may be able to help you.

---

### Post by Thelasko on 2010-08-11
Woah Woah Woah!  Back up a minute.

Did you read the [How To]("http://ubuntuforums.org/showthread.php?t=885111") article in the [Wine section]("http://ubuntuforums.org/forumdisplay.php?f=313") of the forums?

I bet it will answer all of your questions.

Hang on...
What do you mean "Wine Installer"?  You used something other than ```
sudo apt-get install wine
```
Where exactly is this "virtual c:/ drive" you are talking about?  (ubuntu should set that up automatically if you did everything right)

---

### Post by PumaMania on 2010-08-16
I used PlayOnLinux and it worked pretty well! Thank you!

---


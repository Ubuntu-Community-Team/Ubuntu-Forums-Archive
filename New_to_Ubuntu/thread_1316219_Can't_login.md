---
title: "Can't login"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Firepower-EX on 2009-11-05
So, I was trying to compile Chromium, and I had to install some stuff here and there using APT. probably dependencies

After that, I found a .deb for Chromium and did not want to compile the file, so I used 'Apt-get remove' to remove the stuff that was needed to be installed according to a guide.

Then it started deleting alot of stuff like brasero and some other programs.

I closed terminal and did a reboot, and there was a log in screen even though I had set it to directly go to desktop, and when i logged in, it led me back to the login screen. What i dont get is, I specified the things needed to be removed in apt-get, and yet it deleted so many programs.

i most definitely did not run rm -rf /

---

### Post by kansasnoob on 2009-11-05
So what happens if you type in your password?

Sorry, I didn't read close enough. Let me think.

---

### Post by kansasnoob on 2009-11-05
Well, I'm thinking your sudoers file might be hosed so I'd start here:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by cranecreek on 2009-11-05
You of course know your user name and password right? Just login .

---

### Post by nothingspecial on 2009-11-06
It sounds like you have removed ubuntu-desktop.

See if you can log in to recovery mode and ```
sudo apt-get install ubuntu-desktop
```

If you closed the terminal during the process you might have to do a ```
sudo apt-get install -f
```

---


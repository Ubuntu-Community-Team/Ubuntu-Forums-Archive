---
title: "Firefox Refuses to Start up"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Salamancero on 2010-03-12
I installed the Firefox 3.6 recently and everything seems to be working fine until one update.  I had to close firefox and when I decided to switch it on, it just refuses to run.  I decided to uninstall and reinstall it again and at first it seems to work out.  Firefox will run but the moment I switch it off and try to start the browser again, it would simply refuse to run.  I tried using 3.7 but it seems to lock-up in my system.  I tried swiftfox but that didn't work either.  In fact, swiftfox seems to have the same problem save for it not running at all.  I'm a little worried about this as I want to make use of google gears for my offline gmail and google reader usage.  

Any ideas?  Thanks! :)

---

### Post by amsterdamharu on 2010-03-12
What is the output if you start firefox from the terminal (command firefox)?
What do you get iin safe mode? (command: firefox -safe-mode)

You could try seamonkey and see if that works, if only until you fix firefox problems.

---

### Post by dmillard10 on 2010-03-12
Also try

```
killall firefox
```

I had a problem where firefox refused to start because it was already running, but for some reason wouldn't give me the "already running" message.

---

### Post by lovinglinux on 2010-03-12
If you have Prism installed, then removed it. It is causing this problem when using Firefox 3.6.

If not, then see [this](http://lovinglinux.megabyet.net/?page_id=220#Troubleshooting-1).

---

### Post by Salamancero on 2010-03-12
Thanks for the help guys.  I tried accessing firefox from the terminal and it seems to be working.  Also removed Prism so I'll see where this goes.  Apparently, Google gears doesn't work with firefox 3.6 yet so PRISM is unnecessary at the moment. :)

---


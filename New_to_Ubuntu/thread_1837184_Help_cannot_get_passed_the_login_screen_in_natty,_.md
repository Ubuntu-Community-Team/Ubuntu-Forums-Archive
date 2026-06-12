---
title: "Help cannot get passed the login screen in natty, bounces me back, stuck in a loop"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by florinpnicola on 2011-09-01
Hi,

This is the first time this has ever happened to me, I had numerous other issues with Linux, which I always managed to solve via Google, not this time...
The problem:
At login screen, I login as usual, but afer a few seconds, instead of seeing the desktop, I am sent back to the login screen, and I can do that over and over again.
What did I do before this happened:

sudo insmod wl.ko

and 

sudo rmmod wl


those two or both, and I use the sta broadcom driver for wifi, which is working, but I wanted to get rid of it since it disconnected me suddenly while browsing and the wifi card light dissappeared, my netbook, Acer one, has an infamous Brodcom card...I can assure you, my next latop will NOT have one of those
another limitation I have is my home folder is encrypted...


Please help!

Thanks

---

### Post by Rex Bouwense on 2011-09-01
The system is not accepting your password because
1.  You are not typing it correctly.  This is not likely.
2.  Your Caps Lock is on.  Check this because as you know Linux is case sensitive.
3.  You did something knowingly or unknowingly.

I would suggest that you reset your password:
```
http://psychocats.net/ubuntu/resetpassword
```

---

### Post by florinpnicola on 2011-09-01
Reset password and got into deeper trouble, I will post the errors in the order they appear after login...

First one:

Could not update ICEauthority file /home/presidente/.ICEauthority

Second:

There is a problem with the configuration sever. (usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

Third

Nautilus could not create the following required folders: /home/presidente/Desktop, /home/presidente/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them

Then I got the "update information" about recording my encryption passphrase

Then I see a message like this:

GConf error: No database available to save your configuration: Unable to store a value at key 'apps/nautilus/preferences/clutter_test' as the configuration server has no writable databases...and so on



Then, after I close this, I only get the purple Desktop and from there, I can only start terminal but some commands don't even work, like stopping and restarting gnome-panel etc...

Thanks for the help :)

---


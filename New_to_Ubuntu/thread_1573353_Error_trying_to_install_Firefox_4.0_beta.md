---
title: "Error trying to install Firefox 4.0 beta"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by JJuel on 2010-09-12
I am having troubles while trying to install Firefox 4.0 beta. When I go to install it looks like it is going to, but then it gives me an error message. 

The way I went about trying to install is like this:
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-4.0

The first two worked fine, and then when I type the last one I get two errors.
E: Could not get lock var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

If anyone has any idea what is going on and could help me resolve this problem that would be great!

Thanks!

---

### Post by mikewhatever on 2010-09-12
You have either Synaptic or the Software Center open. Close all open windows except the Terminal and run the last command again.

---

### Post by JJuel on 2010-09-12
Thanks! I checked and thought I had all windows closed, and made sure I did. It still didn't work. So I restarted to make sure nothing would be on and then it finally worked. I am not impressed with 4.0 for Ubuntu, but that is a different topic altogether.

Thanks again for your help though!!

---


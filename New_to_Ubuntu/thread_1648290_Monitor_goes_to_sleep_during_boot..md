---
title: "Monitor goes to sleep during boot."
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Sneas on 2010-12-18
Hi all,
I'm having a dilemma.  My monitor goes to sleep upon booting Ubuntu 10.10.  It also did that with the Live CD, but I followed the steps outlined [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
I was able to install following step 1 and using nomodeset for nVidia as that is my graphics card.  However step 2 will not work, so I am stuck and don't know what to do.  If it's any use, I'm using a Compaq Presario SR2013WM desktop PC.
Thanks for your help.

---

### Post by Quackers on 2010-12-18
Are you getting a grub menu up? If not hold down the shift key while booting. Then press the "e" key and remove quiet splash and replace it with nomodeset.

---

### Post by Sneas on 2010-12-18
Thanks so much, it worked and I'm in.  Will activating the NVidia driver work or will I have to finish the steps stated in the guide?

---

### Post by Quackers on 2010-12-18
Hopefully installing the nvidia drivers through System > Admin > Additional drivers will be enough. After a reboot you shouldn't need the nomodeset parameter.

---

### Post by Sneas on 2010-12-18
It worked!  Thanks for your help! :)

---

### Post by Quackers on 2010-12-18
Excellent :-)
Please mark the thread as solved using the Thread tools near the top of the page. Thanks.

---


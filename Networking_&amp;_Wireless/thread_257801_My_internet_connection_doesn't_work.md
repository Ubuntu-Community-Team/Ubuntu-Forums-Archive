---
title: "My internet connection doesn't work"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by ahmad.magdi on 2006-09-15
Hi guys,

I've been using Ubuntu for almost a week, and it worked perfectly fine, till now?? I enter, try to open a few webpages and so, and I can't connect to the internet. Yesterday, it worked fine, but today I can't connect, and I haven't altered anything. Can anyone help me please??

---

### Post by erwinquita on 2006-09-15
> **ahmad.magdi said:**
> Hi guys,

I've been using Ubuntu for almost a week, and it worked perfectly fine, till now?? I enter, try to open a few webpages and so, and I can't connect to the internet. Yesterday, it worked fine, but today I can't connect, and I haven't altered anything. Can anyone help me please??

I experienced the same problem my internet use to work just fine and after two months... It doesn't connect.

I suggest you try to plug out the cable and plug it in again reboot and try to browse sites or ping sites.

Did you apt-get upgrade?

all I remember is that after i apt-get upgrade I started having problems connecting.

Hope this helps.

---

### Post by ahmad.magdi on 2006-09-15
I did all that, and nothing worked. Besides, how can I apt-get upgrade if I can't connect from the 1st place:confused: If you mean I apt-get upgraded before the problem appeared, then you're right, I did apt-get upgrade. But I thought that should improve things, not the other way around!

---

### Post by Dale61 on 2006-09-15
> **ahmad.magdi said:**
> I did all that, and nothing worked. Besides, **how can I apt-get upgrade if I can't connect from the 1st place**:confused: If you mean I apt-get upgraded before the problem appeared, then you're right, I did apt-get upgrade. But I thought that should improve things, not the other way around!

Funny you should mention that.

I did a fresh install of 6.06 on a Toshiba Satellite A30, and have not had internet access since day one.  This si due to the modem not being accessible.

All the recommended fixes require me to download this or download that, but how do I download something if I can't access the internet in the first place!

Maybe future distros can include drivers/modules for the more popular hardware devices.  It seems a lot of users are having trouble with their AC '97 sound / modem (which my laptop has), but the only fix seems to involve having to download something, and until someone comes up with a fix that doesn't need to be downloaded, my laptop will remain inaccessible to the internet.

BTW, I'm posting this from my (dual boot)desktop box, which took 6.06 flawlessly.

---

### Post by dufusmatt on 2006-09-15
Something similar has happened to me too

I ran an get-apt update, and now i can't get webpages.  I am definitely connected to my network, and on the internet.  I can ping sites, and Gmail-Notify works, but firefox/bon echo/gaim2 and synaptic all fail to access the internet.

Could this be an update error?:roll:

---

### Post by gitfiddler on 2006-09-16
Just to weigh in, I have the same problem.

Oddly, I upgraded another machine from Breezy to Dapper, and it works properly. On this machine I performed a fresh install, and now I find myself cruising this forum from Windows.

The problem seems to be widespread, but I've yet to find a definitive answer. Someone has to have one. How about it?

---

### Post by talrasha on 2006-09-16
I also have a problem regarding my Modem. That's why I'm still using windows, by the way I'm writing this reply using my winXP box. And right now I'm reading some tutorials on how to get your modem work.

There are a lot of Linmodems tutorials on the web but I preffered to use the sites being used in Drapper's documentation since I'm trying to configure it in my Drapper box

You can try visiting this sites:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[http://www.linmodems.org](http://www.linmodems.org)
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

---

### Post by Velox Letum on 2006-09-16
The same thing happened to me. I upgraded my kernel yesterday with the new updates and my ipw2200 wireless card stopped associating. Odd, that.

---

### Post by dufusmatt on 2006-09-16
Yup i use the ipw2200 also, and i've tried a direct connection to my router via ethernet ... still nothing.  It's as if the interface that links certain programs to the internet has been damaged, and things like pings, or gmail-notify still work.

Someone help us!

---

### Post by drakshug on 2006-09-16
Me too. I've had to reinstall 4 times. I always have internet til I reboot. I've tried pppoeconf and rp-pppoe but after a reboot they don't work. I've tried every tweak I could find. I though it might be an update prob so didn't do one the last time and then tried a reboot - same. I'm now sitting on dapper and don't dare reboot. It is either back to 5.1 (which was a dsl pain) or go over to Mandriva. Just as well I have my xp on another hdd.
Could the devs please sort this out and could they please offer a gui

---

### Post by Mick the Tick on 2006-09-16
Wondering if this is a kernel issue? Same problem here. Internet connection fine on first install. After update, there are two kernels listed in my grub loader. If I choose 1st entry (newer). no internet but if I choose 2nd (older), internet working fine.

---


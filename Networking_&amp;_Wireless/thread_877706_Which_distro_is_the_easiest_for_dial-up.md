---
title: "Which distro is the easiest for dial-up"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by zieglerj on 2008-08-02
I just install Ubuntu Gutsy for a friend who uses dial-up internet. We've got the drivers for the modem installed and wvdial set up for his ISP but when connected he can only get at most 4 Kb per second even though his isp says that we should be able to get 30. 
I used wvdialconf in root to set up the modem in wvdial, I think the baud rate it set was 406000 or something along those lines. 
He's using a 56k modem. 
Is this normal in Ubuntu? I use broadband myself so I can't tell. If it is normal with Ubuntu, what is the best distro for dial up?

---

### Post by zieglerj on 2008-08-02
I'm Really at a loss here, I need help with this.

---

### Post by ModelM on 2008-08-02
Here's my /etc/wvdial.conf:

```
[Dialer Defaults]
    New PPPD = yes
    Stupid Mode = yes
    Modem Type = Analog Modem
    ISDN = 0
    Auto DNS = yes
    Auto Reconnect = 0
    Modem = /dev/modem
    Baud = 115200
    Init1 = AT&F
Phone = 503 488 3200

Username = whoisthis
Password = guessit
```

You can back up your config file by typing into a terminal:

sudo mv /etc/wvdial.conf /etc/wvdial.conf.saved

You can copy my code here to /etc/wvdial.conf, edit the phone #, username, password, & give it a try.

If you don't like it just type into a terminal:

sudo rm /etc/wvdial.conf && mv /etc/wvdial.conf.saved /etc/wvdial.conf

to go back to where you were.

---

### Post by Vorian Grey on 2008-08-03
> **zieglerj said:**
>  
I used wvdialconf in root to set up the modem in wvdial, I think the baud rate it set was 406000 or something along those lines. 
He's using a 56k modem. 


I think the baud rate is too high. It should be 115200 like in ModelM's wvdial file.

---

### Post by zieglerj on 2008-08-04
Thank you both, I've tried messing with the baud rate but the problem is elsewhere. I just found out the driver I installed from linuxant poses as free open source but the free version caps the modem at 14kbps. Does anyone know of another hsf conexant modem driver out there?

---

### Post by ModelM on 2008-08-04
Dell has one here...

[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/)

...obviously the one you want is the .deb package. I'm using this driver with a PCI softmodem in one of my machines here & it works very well.

---

### Post by zieglerj on 2008-08-04
What kernal are you using it with? There is only one driver there and I want to make sure to get the right kernel version installed before uninstalling the linuxant modem driver.

---

### Post by ModelM on 2008-08-04
During the install of the .deb package, it is compiled against your kernel & installed. It also re-builds itself automatically if you should upgrade kernels.

You'll need to have the kernel headers & build-essential installed before you install this .deb pkg.

---

### Post by dmizer on 2008-08-04
Moved thread to "Networking and Wireless"

---

### Post by zieglerj on 2008-08-05
Do you just install with the package installer (double clicking the .deb)? I wound up going with the $20 driver but I'm still having the same problems that I was with the driver you recomended. Changing the baud rate doesn't seem to do anything. I think the only other diference in my wvdial.conf file is that mine doesn't mention "stupid mode." would that affect it?

---

### Post by ModelM on 2008-08-05
"Stupid Mode" changes the logon procedure from open text handled by wvdial, to PAP/CHAP handled by PPPD. It wouldn't affect speed.

Yes, I installed using the package manager via the double-click. I've done nothing more to tune or tweak the driver.

With the driver from Dell, if you'll add "S95=45" to the init string, the modem will return additional info when it connects. This will include the protocol (V92, V90, V34, etc), DTE rate, DCE rate (both up & down), & compression (V42bis, V44). This info might be useful in helping diagnose what's going on.

I don't know if this command will work with the driver from Linuxant but, if not, theirs will have an equivalent command, I'm sure.

---

### Post by zieglerj on 2008-08-07
A tech support sent out some new init strings to try. At the first one an online speed test said it was getting 26 Kbs but when I go to install updates, they only download at 2.6 kbs. Could it be that the problem isn't in the modem or driver but in Ubuntu itself?

---

### Post by ModelM on 2008-08-07
One of the problems with dialup modems is finding a reliable method to measure throughput. The speed readout of the Synaptic package manager *cough* could be better.

Various websites will try to give you a speed measurement but you are at the mercy of many variables - protocol overhead (both tcp/ip & ppp), server location, traffic switching changes, etc.

You need a consistent & convenient tool which is both reliable & repeatable in order to gauge the true metric of your modem. And you have one.

When you are downloading a file for testing, just open a terminal & type:

pppstats -w10

This will print every 10 seconds the stats of the ppp interface. You can change the number to -w1 which will print every second but I prefer -w10 as it smooths the numbers somewhat. Using pppstats -w10 and rounding off to the first two digits will give you a good picture of data flowing across the interface. So a number of 49282 would be about 49k, not bad for a 56k modem. You'll see different number ranges for different file types depending on how compressible the file is, but with some time trying different file types you'll get a good feel for the numbers.

---


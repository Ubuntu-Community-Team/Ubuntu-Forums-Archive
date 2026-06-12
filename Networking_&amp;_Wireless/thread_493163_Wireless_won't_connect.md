---
title: "Wireless won't connect"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Bofur on 2007-07-05
Ok I just reformatted to Ubuntu but my wireless is having trouble connecting. So heres what I did:
This is also a Dell 802.11n WLAN Mini Wireless Card
1. I installed Ndiswrapper from Synaptic
2. Got the drivers from the dell website, and extracted the exe file. 
3. ```

sudo ndiswrapper -i /home/justin/.WLAN/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
bcmwl5.sys : invalid driver!
sudo modprobe ndiswrapper
```

How do I install the bcmwl5.sys driver because I know the .sys file is in the driver folder. 

I'm guessing because I don't have the .sys file installed my wireless isn't working. Any help would be appreciated.

---

### Post by md2020 on 2007-07-05
Check out this thread. It is for a different wireless card, but it still is describing what to do for ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

See "Step 4 - Installing drivers". "The last command says that the drivers are invalid. That's because it didn't install the sys files! We need to do this manually. Run these commands, assuming you haven't closed the terminal since the last few commands:"

Hope that helps.

---

### Post by Bofur on 2007-07-05
```
justin@ubuntu:~$ sudo cp bcmwl5.sys /etc/ndiswrapper/
cp: cannot stat `bcmwl5.sys': No such file or directory

```

I'm lost..

---

### Post by md2020 on 2007-07-05
Did you execute the cp command from the same directory where the bcmwl5.sys is located?

You also need to copy bcmwl5.sys to the subdirectory under /etc/ndiswrapper for your wireless card.

I assume that the bcmwl5.sys file is in the same directory as the bcmwl5.inf you indicated in your first post. I also assume that the subdirectory in /etc/ndiswrapper is called bcmwl5. If that is not correct alter it below.

To copy where it needs to be, run this.

```
sudo cp /home/justin/.WLAN/DRIVER/bcmwl5.sys /etc/ndiswrapper/bcmwl5/
```
After successful copy, you can run this:
```
ndiswrapper -l
```

My apologies if I have misunderstood something.

---

### Post by Bofur on 2007-07-05
You are right but:
```
justin@ubuntu:~$ sudo cp /home/justin/.WLAN/DRIVER/bcmwl5.sys /etc/ndiswrapper/bcmwl5/
Password:
justin@ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
bcmwl5.sys : invalid driver!
justin@ubuntu:~$ 


```

---

### Post by md2020 on 2007-07-05
Ug. Sorry, looks like you better remove that file with this:
```
sudo rm /etc/ndiswrapper/bcmwl5/bcmwl5.sys
```

I thought yours was going to be a simple fix of just getting that sys file in the right place. But thankfully there appears to be a HowTo for your wireless card. Hopefully the steps outlined there can get you up and going:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Best of luck...

---

### Post by Bofur on 2007-07-05
Thats exactly what I did. The wireless card seems to be picking up my router, but it just sits at connecting. So I don't know what the deal is.

---

### Post by md2020 on 2007-07-05
You are probably beyond my ability to help, but I have one last suggestion. As indicated in the above referenced HOWTO, make sure you have encryption turned off on your router to make sure that is not playing into your issues.

When I got mine working, I think I had to do this the first time to get it to connect:
```
sudo dhclient wlan0
```
This assumes you are not using static IP addressing. If your wireless card is not wlan0, substitute whatever your card is. This for getting or renewing your IP address.

I also found this HOWTO on wireless security helpful. Check out the section called "Other useful commands".
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---


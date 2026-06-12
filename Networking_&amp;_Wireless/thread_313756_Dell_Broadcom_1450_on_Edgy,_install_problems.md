---
title: "Dell Broadcom 1450 on Edgy, install problems"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by gerbel01 on 2006-12-06
Hey, newbie linux user here having trouble setting up my Inspiron 9100 with the Broadcom 1450 wireless card.  I know there are loads of threads on this, but I was having trouble finding exactly what i needed from them.  

I have ndiswrapper downloaded and working, and have two dell drivers (bcmwl5a.inf, and bcmwl5.inf), the two i saw mentioned in the threads ive been looking into, and ndiswrapper is saying they are both invalid, for reasons i dont know.  I was wondering if anyone had some insight on which one exactly i need, if either of them, and how to get them to run correctly.  

Thanks.

---

### Post by gitargr8 on 2006-12-06
Can you post the output you get when you try to install the drivers with ndiwrapper? 

I would recommend downloading the correct driver for your card from Dell's website, and try to install all of the .inf files until one works, then simply remove the ones that didn't.

~Ryan

---

### Post by gerbel01 on 2006-12-06
i downloaded the newest correct one off dell's website (bcmwl5.inf), but when it did not work i attempted the bemwl5a.inf, which i saw mentioned in other threads.  

heres the code, im not sure how you do that code-in-box thing :)


ben@ben-laptop:~$ sudo ndiswrapper -i /home/ben/Desktop/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
ben@ben-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

---

### Post by gitargr8 on 2006-12-07
> heres the code, im not sure how you do that code-in-box thing
If you hit the # looking icon it will bring up the bb code tags. Put your code between them, and it will appear in a code box.

Now, first off, I'm not completely sure you've got the correct driver. Run the following and post your results:
```

~$ lspci | grep "\(Net\|net\)"
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

This should give you the model numbers for your network controllers. Verify that you downloaded the correct driver package for your card from Dell. Once you've double checked that you have the correct files, navigate to the folder where the driver files reside and run:

```

~/Desktop/YourDriverDirectory$ ls | grep .inf
```

This will give you a list of all .inf files in that folder. Try installing all of them:

```

~/Desktop/YourDriverDirectory$ ndiswrapper -i DriverFile.inf
```

Until you get one that works:

```

~/Desktop/YourDriverDirectory$ ndiswrapper -l
installed drivers:
lsbcmnds                driver installed, hardware (14E4:4320) present (alternate driver: bcm43xx)
```

If you see (alternate driver: module), like my output shows, you need to add that module to the blacklist file. I can fill you in on how to do that if need be.

Good Luck,
~Ryan

---

### Post by gerbel01 on 2006-12-13
> **gitargr8 said:**
> If you hit the # looking icon it will bring up the bb code tags. Put your code between them, and it will appear in a code box.

Now, first off, I'm not completely sure you've got the correct driver. Run the following and post your results:
```

~$ lspci | grep "\(Net\|net\)"
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

This should give you the model numbers for your network controllers. Verify that you downloaded the correct driver package for your card from Dell. Once you've double checked that you have the correct files, navigate to the folder where the driver files reside and run:

```

~/Desktop/YourDriverDirectory$ ls | grep .inf
```

This will give you a list of all .inf files in that folder. Try installing all of them:

```

~/Desktop/YourDriverDirectory$ ndiswrapper -i DriverFile.inf
```

Until you get one that works:

```

~/Desktop/YourDriverDirectory$ ndiswrapper -l
installed drivers:
lsbcmnds                driver installed, hardware (14E4:4320) present (alternate driver: bcm43xx)
```

If you see (alternate driver: module), like my output shows, you need to add that module to the blacklist file. I can fill you in on how to do that if need be.

Good Luck,
~Ryan

```

ben@ben-laptop:~$ lspci | grep "\(Net\|net\)"
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```
when i run ls |grep.inf, i get nothing
```

ben@ben-laptop:~$ ls | grep .inf
ben@ben-laptop:~$ 

```

---


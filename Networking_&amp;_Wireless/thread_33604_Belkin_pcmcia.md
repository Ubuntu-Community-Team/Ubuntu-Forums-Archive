---
title: "Belkin pcmcia"
date: 2005-05-11
forum: Networking &amp; Wireless
---

### Post by hack_benjamin on 2005-05-11
Running a Belkin pcmcia card with a broadcom (or so gnome device manager says) chip, Is there a way to get this to work free?
or is it only driverloader that works?
I tried it and "dpkg -i driverloader...deb" didn't work because i didnt have some kernel sources- but how do i get them without internet access??

Thanks

---

### Post by az on 2005-05-11
Use ndiswrapper.  

sudo ndiswrapper -i (driver.inf)
sudo modprobe ndiswrapper
and then configure your device with the networking tool.


If you need the kernel source, use the linux-heaqders package.

---

### Post by AMP on 2005-05-11
I have the same if not a similar card. I Installed Ndiswrapper and installed the drivers, modprobed, even set up my settings Yet my pccard is not on, the power and link buttons never light up at all, what should i do? :neutral:

---

### Post by AMP on 2005-05-12
Ok i got the power but the dhcp always fails, now what should i do, i need my wireless net?!?

---

### Post by AMP on 2005-05-14
Is there any other way to configure my card or Make it work?!

---

### Post by spd106 on 2005-05-14
Hi, can you see your ap?

ie. What's the output of $iwlist wlan0 scan

Have you set up wep? If yes, it might be best to disable until you know it works.

---

### Post by AMP on 2005-05-14
[QUOTE=spd106]Hi, can you see your ap?

ie. What's the output of $iwlist wlan0 scan

Have you set up wep? If yes, it might be best to disable until you know it works.[/QUOTE]
I get No Scan results and no WEP is set up.

---

### Post by spd106 on 2005-05-15
Hi, if you can't see any aps then you're either too far from one to get a signal, or perhaps more likely your pc card isn't working properly.

Check it is installed and has a valid driver with
```
$sudo ndiswrapper -l
```

You might need to compile ndiswrapper from source. There are a few resources to help you through this 
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

Make sure you know as much about your card as you can because the manufacturers are known to change the chipset even on the same model without warning.
```
$lspci
```

Good luck

---

### Post by AMP on 2005-05-16
Thanks i will try, i finaly realized i never compiled as root :roll: , thank you!

I know i am not too far away the router is 20 feet away!

---


---
title: "Driver Problems"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Jsgrabo on 2007-03-07
Hi, im trying to install a Linksys WPC54GS v1.1 wireless card on my laptop. I installed ndiswrapper and I pretty sure that i've installed the driver correcty using this guide: [http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php]("http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php").

The driver appears to install correctly but when i enter

```
 ndiswrapper -l 
```

i get this

```
 
Installed ndis drivers:
lsbcmnds        invalid driver! 
```

What im wondering about is the "invalid driver". After installing the driver, I go to system>administration>networking, and the wireless card still does not show up. So do I just have the wrong driver or what? Any advice/help is greatly appreciated.

Thanks

---

### Post by Floppyjoe on 2007-03-07
Delete the invalid driver using:
```
sudo ndiswrapper -e drivername
```
Then make sure you have all the necessary files in the same directory you are installing the .inf file from like any .sys and .bin files.
This is case sensitive so make sure you type the name of the driver.inf file correctly with caps where there are caps and small letters where there are small letters.

To install enter:
```
sudo ndiswrapper -i drivername.inf
```

---

### Post by Jsgrabo on 2007-03-07
Oh ok; i originally pulled the .inf file out of the folder containing the .sys and .bin file and tried to install it. My mistake. I put it back and tried it; it worked! Thanks for your help!!

---


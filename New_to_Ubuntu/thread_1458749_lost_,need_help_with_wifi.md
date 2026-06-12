---
title: "lost ,need help with wifi"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by jobo123 on 2010-04-20
Hi folks im looking for some help 

ive had a difficult journey with linux, having periodical, over the last two years tryed to get it working, mostly unbunto but ive also tried to use a couple of other disros as well

And i all ways fall down at the point of trying to get other things to work with it

this time ive installed ubunto 9. 10 on dual boot with vista and it works to the extent i can use the internet on wire :P which is a major step forwarded

But i cant get the wi fi working, ive got an edimax ew77 11 uan antena

ive done search on here, well to be honest, some one on another linux foriumht did for me and came up with this
[http://ubuntuforums.org/showthread.php?t=1236802](http://ubuntuforums.org/showthread.php?t=1236802)

My problem is i get to number two on the list of instructions and im scratching my head at how to open a terminal let alone do the programming required, read error messages etc

Im happy to read guides and do research, but i seem to be lacking some under pinning knowledge


so my question 

is there anybody with the patience to guide me through what seems to be a simple process for those in the know, but complete gibberish to me  ?

thanks for reading 

joe

---

### Post by LowSky on 2010-04-20
jobo123 welcome to the forums. I'm willing to help, but when I get home from work, which will be in about an 2 hours. That link you supplied is horribly written for a new user and I would like to clean it up to help you out. maybe in he meantime my bump will bring more attention.

---

### Post by LewRockwell on 2010-04-20
> **LewRockwell said:**
> Saw this earlier today so I went back and grabbed the link.

[http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/)

.

[http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/)

---

### Post by nothingspecial on 2010-04-20
In your menus applications > accessories > terminal

Download the correct driver from [[COLOR="Magenta"]here[/COLOR]]("http://www.ralinktech.com/support.php?s=2")

Download it to your home directory.

```
cd
```

```
ls
```

I don`t know which your driver is but the ls command should show you what you have downloaded

```
cd exact_name_of_downloaded_driver/os/linux
```

```
nano config.mk
```

Find the lines (with your arrow keys)
```


HAS_WPA_SUPPLICANT = n

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n
```


and change both lower case n to y
```



HAS_WPA_SUPPLICANT = y

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y
```

Press Ctrl O to save, Enter to confirm then Ctrl X to exit.

```
cd ../../
```

```
make
```

```
sudo make install
```

```
cd os/linux/
```

```
sudo insmod rtxxxxsta.ko
```


Follow these directions exactly (although I`ve probably made a typo) and if your wireless suddenly starts working we`ll look at making it permanent.

Assuming we are in different time zones, if it does work, and I`ve no idea wether it will or not, if you reboot you will have to type 
```
cd exact_name_of_driver/os/linux
sudo insmod rtxxxxsta.ko
```

To get it to start working, not the whole lot.

---

### Post by jobo123 on 2010-04-20
thanks lew, im reading that now

and sky if you could id be very great full

nb i can now open a terminal:)

---

### Post by jobo123 on 2010-04-20
Thank NS

is down loading to your home directory an obvious thing to do, ie is that an option which comes up or do you need to do something first

i have to go and sit in the cold to d
get hard wired so il; go and try it in a few mins 

cheers

nb im on GMT

---

### Post by nothingspecial on 2010-04-20
Firefox should ask you.

The reason I said to was that I have no idea where you have set firefox to download stuff to.

The command ```
cd
```

changes to your home directory, so where ever your terminal is, if you type cd you go home, which makes simplifying the instructions easier for me.

---

### Post by jobo123 on 2010-04-20
dont thing ive got firefox on the installation ?

just google

---

### Post by nothingspecial on 2010-04-20
Firefox is your web browser, just click on the correct file to download and select your home (your username)

---

### Post by Don Mega on 2010-04-20
hey i had this long fight with WIFI on my laptop for two weeks trying ndiswrapper and .conf editing, looking for drivers and everything under the sun EXEPT](*,) going to update manager - check for update - install up dates - restart - check for updates again - installed again - and wollla! wifi started scanning found my network and bamm 2 weeks down the drain for simple steps.:) Try this first before everything else brother. let me know how it goes..

---


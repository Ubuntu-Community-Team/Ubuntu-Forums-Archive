---
title: "WinModem + External Modem, is it possible?"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by chakra_dude on 2005-11-29
Hello guys! i was having problem setting up my internet connection. First i tried downloading drivers for my winmodem which is a Conexant. I opted not to configure it because the modem boosts up to only 14 kbps according to the site where i downloaded the driver and it's not possible in my situation to shell out some dollars for the full driver(i'm from the Philippines). 

Now as a religious follower of this site, i've read that most experts here recommend getting an External modem, which I did. 

My question are as follows:
1. Ubuntu detected only my Internal winmodem. I tried to let Ubuntu autodetect my External but it doesn't. Do i have to uninstall my Winmodem or remove it entirely from my system?
2.Is it possible to have my two modems at the same time?
3.What can you guys recommend for a noob like me?

Thanks in advance to all. 
Cheers!!!

---

### Post by mips on 2005-11-29
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)


[http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
[http://www.linmodems.org/](http://www.linmodems.org/)
[https://wiki.ubuntu.com/Conexant](https://wiki.ubuntu.com/Conexant)
[https://wiki.ubuntu.com/WinModemConexantHSF](https://wiki.ubuntu.com/WinModemConexantHSF)
[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

---

### Post by Tony6316 on 2005-11-29
Yes, it's possible to have a winmodem in the computer along with an external modem.  I wasn't able to use my winmodem with Hoary (although I could with Mandrake 9.1) so I purchased an external modem that's known to work with Linux.  I configured it using wvdialconfig which will search your com ports and tell you where it found a modem it could use.  It then creates a little script which you edit with appropriate information regarding your ISP's phone number, your username, password, etc.  You then use wvdial to make your connection.

All of the above is from memory so it may not be completely accurate.  I'm sure you can get better details from the wvdial documentation.

Cheers.

---

### Post by chakra_dude on 2005-11-29
[QUOTE=Tony6316]Yes, it's possible to have a winmodem in the computer along with an external modem.  I wasn't able to use my winmodem with Hoary (although I could with Mandrake 9.1) so I purchased an external modem that's known to work with Linux.  I configured it using wvdialconfig which will search your com ports and tell you where it found a modem it could use.  It then creates a little script which you edit with appropriate information regarding your ISP's phone number, your username, password, etc.  You then use wvdial to make your connection.

All of the above is from memory so it may not be completely accurate.  I'm sure you can get better details from the wvdial documentation.

Cheers.[/QUOTE]

Thanks dude. How do i do a wvdialconfig? Do i type it in the terminal?
I'll try researching for it though.

By the way, i'm using an Ambient external modem. Is there a way i can make this work? 

Take Care.

---

### Post by StefanoCole on 2005-11-30
I think you have to run wvdialconf from terminal.
For its use try "man wvdialconf".
I think you can type
$ wvdialconf .wvdialrc

enter your info and type wvdial to get on the net.
You can also use pon.wvdial and poff.wvdial

Bye, Stefano

---

### Post by Tony6316 on 2005-11-30
That's right Stefano.  That's how I recall doing it.

---

### Post by chakra_dude on 2005-11-30
Thanks for all your replies guys. I will update you with my progress as soon as i get my hands on my home pc. We've been doin so much work in the office lately, i can only play with my Ubuntu box on weekends.
Anyway, thanks for all the great info!

---

### Post by chakra_dude on 2005-12-05
Question: I tried pppconfig with no luck. Is it the same with wvdialconfig?

Thanks

---

### Post by Tony6316 on 2005-12-05
I don't know about pppconfig, I never used it.

If you do wvdialconfig, be sure to do it as sudo, e.g. you need to do:

```
sudo wvdialconfig
```

It should probe your com ports (be sure you turned on your external modem and have it connected to one of your com ports first) and give you a report.

Then edit the output file (I think it may be wvconfig.txt but check the man pages) correcting the phone number of your ISP, your login name and password, etc.

Next, make sure you have access to the wvconfig file and invoke wvdial by doing:

```
sudo wvdial
```

It should dial your modem and then you can activate your browser, email client, etc.

Cheers.

---

### Post by chakra_dude on 2005-12-05
Thanks!

---


---
title: "4G-stick Huawei E3372: internet connection via command line?"
date: 2021-07-26
forum: Networking &amp; Wireless
---

### Post by rosika on 2021-07-26
Hi all, 

does anyone know a method of how to establish internet connection using the 4G-stick **"Huawei E3372h-320" **via the *command line*?

Right now it works this way:

In contrast to my previous stick (which was Huawei E1550),
the new one no longer logs on to the computer as a modem, but as a virtual network card.
A new LAN interface ("Kabelgebundene Verbindung 2") is created and the computer connects to this one. 

The internet connection itself is established by using the stick via the **browser**. 
The respective page is "http://192.168.8.1/". Here a Huawei-powered GUI presents itself and I establish the internet connection by clicking on something like "connect".

Thanks a lot in advance.

Many greetings
Rosika ):P

P.S.:
my system: Linux/Lubuntu 20.04.2 LTS

---

### Post by TheFu on 2021-07-26
Normal networking can be controlled using **wicd-cli** or **nm-cli** if you don't want to setup a netplan YAML file.

I don't know anything about specific devices, but if they are seen and the drivers are automatically loaded, either of those 3 options can work.

---

### Post by rosika on 2021-07-26
@TheFU:

Hi,

thanks so much for the suggestion. I´ll look into it.

Many greetings and keep safe.
Rosika

---

### Post by TheFu on 2021-07-26
I have doubts that those tools I listed will be useful. 

If the modem connection is just a cell data connection, perhaps using the ppp connection technique could work, but I've not used that in about 15 yrs.  I had a work-provided data card in the early 2000s and used it daily for a few years.  Fortunately, it didn't have any data limits and was often as fast as my home broadband connection at the time, even when using the mandated VPN software too.

If the web interface to start the connection is simple, you might be able to capture the commands and reply them later. If the web interface is simple HTML, then that isn't too hard. If it is javascript and ajax, then it becomes exponentially more difficult.

---

### Post by rosika on 2021-07-27
@The Fu:

Hi,
thanks so much for your new answer.
> If the modem connection is just a cell data connection, perhaps using the ppp connection technique could work

Well, it´s just cell data connection. Yet unlike the "Huawei E1550": 
> the new one no longer logs on to the computer as a modem, but as a virtual network card.

Therefore I cannot use tools like **modem-manager-gui** any more. It´s not using the ppp connection technique.
Normally I wouldn´t have any issues opening a browser and establishing the conection manually with a click. But...

The background to my question is:

I once wrote a script for administration/statistics (for my old  "Huawei E1550").

This script works incorrectly now due to the fact that  it´s based on the use of **vnstat**.

 **vnstat** monitors the newly created interface (“enx001e101f0000” in my case).

 The page “[http://192.168.8.1/](http://192.168.8.1/)” takes a pretty long time to load (about 40 secs.), but it affects **vnstat**.
 This means that **vnstat** already counts some sort of “data consumption”, namely almost exactly 5 MB. 
At this point I am **NOT** yet connected to the Internet, i.e. AldiTalk (using O2 as internet provider) cannot bill me for these 5 MB.


 Same thing when closing the internet connection at the end of the day.
This already amounts to 10 MB per day. 


 The whole thing adds up to a rather large false amount during the monthly flatrate period (28 days). 

 Plus: If I use the SMS functionality, it´s same thing again.
Because loading any page based on “[http://192.168.8.1/](http://192.168.8.1/)” “consumes” data according to vnstat (but not via the Internet).

Anyway thanks a lot for your help.

Many greetings.
Rosika  :)

---

### Post by TheFu on 2021-07-27
Did you see this: [https://askubuntu.com/questions/757638/can-not-connect-huawei-e3372-modem-on-ubuntu-15-10-please-help](https://askubuntu.com/questions/757638/can-not-connect-huawei-e3372-modem-on-ubuntu-15-10-please-help)

---

### Post by rosika on 2021-07-27
Hi again,

thanks a lot for the link.
Well, it seems to contain quite a wealth of information. Some of it I can certainly confirm.


> This is HiLink modem, that means no need for ppp, wvdial, ttyUSB, usb_modeswitch, fallback mode switching etc.
Quite so. I think that´s the reason why **modem-manager-gui** isn´t suitable for that stick any longer.
> The USB dongle works directly as a "wired connection"
Exactly the same with me.

> Additionally, I had to visit [web interface]("https://askubuntu.com/a/864069/69296"), and click "Connect".
Yes, with me, too. And that´s the point I wanted to avoid as loading the web-interface will already add to my "data-consumption".
Not in reality, as internet connection isn´t established yet at that point. But it´s _**counted**_ as "data-consumption" by **vnstat** (monitoring the respective interface).

I guess one solution might be to manually stop **vnstat.service** for the time during which I establish internet connection via the browser and re-start it later when I´m done.
But that procedure seems a bit clumsy to me. It might help if** vnstat.service **could be **paused** (perhaps wit the help of a shortcut) instead of stopped and re-started. Yet I cannot imagine that´s possible... :-k

Nevertheless: thanks so much for your help.

Many greetings.
Rosika :smile:

---


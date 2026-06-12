---
title: "Kismet error!!!! Assistance needed!"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by JudasReanimated on 2008-04-08
```
Unknown capture source type 'RTL8187' in source 'RTL8187,wlan0,kismet'
```

I´m not sure what I´ve done wrong. Any ideas on what I can do?

Also I´m obsessed with Network Security and Penetration, so if you know any great programs like kismet or better, or different, let me though.

---

### Post by Junglizer on 2008-04-09
> **JudasReanimated said:**
> ```
Unknown capture source type 'RTL8187' in source 'RTL8187,wlan0,kismet'
```

I´m not sure what I´ve done wrong. Any ideas on what I can do?

Also I´m obsessed with Network Security and Penetration, so if you know any great programs like kismet or better, or different, let me though.

Is this a Realtek card? I will assume that is is given the 'RTL.' RTL8187 does not appear to be a valid source type, as can be seen in the error, as well in accordance to their documentation, which only lists the following: [http://www.kismetwireless.net/documentation.shtml]("http://www.kismetwireless.net/documentation.shtml")

It simply lists [QUOTE=Kismet online documentation]
rt8180          Realtek 8180 11b    Linux       rtl8180-sa2400

[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)
Realtek 8180 based cards (there seem to be an awful lot of
them) using the GPL drivers.
[/QUOTE]

---

### Post by JudasReanimated on 2008-04-09
I may be misunderstanding as I'm in a rush at work with only a few moments to spare on this, but does this mean I can't use kismet at all, or is there something I have to do to rectify this?

Sorry if I come off ignorant.

---

### Post by Junglizer on 2008-04-10
There isn't (yet) a specific reason that you wouldn't be able to use Kismet, however to get a better idea can you post what card you have and its chipset? 

Well since your error is: 
**Unknown capture source type 'RTL8187' in source 'RTL8187,wlan0,kismet'**

It means you have something listed wrong in the source listing of **/usr/local/etc/kismet.conf**. Edit that file and go to the line that has 'source=RTL8187,wlan0,kismet'. You will need to change something within that line. RTL8187 is not a valid source listing for the Kismet program, this may just be a simple typo. Try replacing 'RTL8187' with 'rt8180' so your like looks like:```
source=rt8180,wlan0,kismet
``` save the file and try to re-run Kismet.

Some other apps you may like include IPTraf (ncurses based) and Wireshark (formerly Ethereal). Both are good packet sniffing/monitoring apps, though not directly similar to Kismet. You will also probably want the Aircrack-NG suite.

---

### Post by JudasReanimated on 2008-04-10
Thanks, I'll give it a try, as for the chipset and card, I'm not 100% sure, I'll check when I get home and let you know. I know it's a Realtek, and it uses the RTL8187 Driver.

My Laptop is a Clevo M670SRU if that helps any?

---

### Post by JudasReanimated on 2008-04-11
AzureWave Technologies, Inc

Thats pretty much all the info I could get.

---


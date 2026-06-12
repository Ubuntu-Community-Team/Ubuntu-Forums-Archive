---
title: "I can't get my Ubuntu 11.04 to print on Canon PIXMA IP2772"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-08-17
Dear All,
Today I bought a Canon PIXMA IP2772. Natty detected the printer and model as soon as it was connected. I used driver for IP2000 series since this was the nearest one during installation. 

However, I do not get any print output. When I submit a Test Page, it shows that I am printing a test page, shows all the times and percentages but nothing happens on the printer. 

Any pointer or suggestion will be appreciated. Thanks in advance.

(I have visited [http://www.openprinting.org/printer/Canon/Canon-PIXMA_IP2700](http://www.openprinting.org/printer/Canon/Canon-PIXMA_IP2700) from [http://www.linuxquestions.org/questions/linux-newbie-8/i-cant-get-my-ubuntu-11-04-to-print-on-canon-pixma-ip2772-882974/](http://www.linuxquestions.org/questions/linux-newbie-8/i-cant-get-my-ubuntu-11-04-to-print-on-canon-pixma-ip2772-882974/). But do not find a download link.)

---

### Post by Matt__ on 2011-08-17
IP2700 Series Download
[http://support-asia.canon-asia.com/c...100272002.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html")

Disconnect printer

terminal:

          [LEFT]                      [COLOR=#000000] [COLOR=#FF8000][COLOR=Navy]```
sudo  dpkg -i cnijfilter-common_3.30-1_i386.deb
```[/COLOR][/COLOR][/COLOR][/LEFT]
       
     [LEFT]                      [COLOR=#000000] [COLOR=#FF8000][COLOR=Navy]```
sudo dpkg -i cnijfilter-ip2700series_3.30-1_i386.deb
```[/COLOR]
[/COLOR] [/COLOR]               [/LEFT]
  Administration / Printing / delete printer

Start up the printer again and you should be good to go.

---

### Post by PapaGary on 2011-08-17
Look here:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

---

### Post by zebastian on 2011-08-27
> **Matt__ said:**
> IP2700 Series Download
[http://support-asia.canon-asia.com/c...100272002.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html")

Disconnect printer

terminal:

          [LEFT]                      [COLOR=#000000] [COLOR=#FF8000][COLOR=Navy]```
sudo  dpkg -i cnijfilter-common_3.30-1_i386.deb
```[/COLOR][/COLOR][/COLOR][/LEFT]
       
     [LEFT]                      [COLOR=#000000] [COLOR=#FF8000][COLOR=Navy]```
sudo dpkg -i cnijfilter-ip2700series_3.30-1_i386.deb
```[/COLOR]
[/COLOR] [/COLOR]               [/LEFT]
  Administration / Printing / delete printer

Start up the printer again and you should be good to go.

Great, thank you! :guitar:

---


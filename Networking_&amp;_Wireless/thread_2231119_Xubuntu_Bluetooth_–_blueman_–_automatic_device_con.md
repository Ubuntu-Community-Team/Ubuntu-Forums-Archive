---
title: "Xubuntu Bluetooth – blueman – automatic device connection"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by Alan_Dean on 2014-06-23
[SIZE=3][FONT=arial]I need to change the audio.conf **in /etc/bluetooth/**  so I can connect my headphones as described below. That is [COLOR=#000000]remove the comment from the last line of the coda, save out then restart bluetooth. However it will not allow me to save the changes. How can this be done?
[/COLOR][/FONT][/SIZE]
# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good

# idea.

AutoConnect=**true**


[SIZE=3][FONT=arial]
[http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset/](http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset/)


Thank you

Alan[/FONT][/SIZE]

---

### Post by ajgreeny on 2014-06-23
You will have to open the /etc/bluetooth/audio.conf file as root so try either ```
sudo nano /etc/bluetooth/audio.conf
``` or if you prefer a GUI text editor to nano ```
gksudo mousepad /etc/bluetooth/audio.conf
``` make your changes and then save the new file.

I don't use nor have any bluetooth hardware, so I am assuming your need to make those changes is correct but you may like to double check all this before committing to changes that could affect your system.

PS: I am not sure if gksudo is installed by default any more, so if you get an error in terminal about that, just follow the instructions to install what is needed.

---


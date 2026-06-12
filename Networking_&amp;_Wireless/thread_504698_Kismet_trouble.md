---
title: "Kismet trouble"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by tennvolsmb on 2007-07-19
ok ive been trying for days to get my kismet working, but every time i run it i get a FATAL error telling me that no packet sources are defined

```
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

how do i configure packets it is driving me crazy!!!

---

### Post by reckless2k2 on 2007-07-19
you have to define your source in the config file depending on your wifi card. try the kismet page and they explain everything. then you'll have to lspci for your wifi card details and go from there.

---

### Post by tennvolsmb on 2007-07-19
well actually the website is no help i've looked at it many times and i cant find anyting but just to let you know im using a Broadcom BCM4318 card, if anyone can help me from there

---

### Post by tennvolsmb on 2007-07-19
can anyone help. Please this is driving me crazy figuring it out

---

### Post by jml on 2007-07-19
First, here is the Kismet documentation page:

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

Second, Kismet in not a particularly user friendly application, as it comse from the developers. So hang in there. 

Thirdly, once you do configure Kismet correctly, many of its functions require that your wireless card be placed in passive mode.  Its my recollection that the Broadcom based cards do not support this function.  If I am wrong about that one, I am sure someone else will correct me.  Good luck.

Joe

---

### Post by reckless2k2 on 2007-07-19
yep...i'm almost certain broadcom does not work with kismet.

edit: wrong....bcm43xx is source you need in kismet config file

---

### Post by tennvolsmb on 2007-07-19
ok well i can't find where to configure your packets if anyone could help me with that... that is the main problem since the only FATAL error message is that i dont have any packet sources configured.

---

### Post by reckless2k2 on 2007-07-19
ok...i'll hold your hand but as the other poster suggested...kismet is a serious tool and if you can't figure out how to edit a config file or how to read the man page, then this is not a program for you. you'll have a bunch of questions next how to use kismet and we will be back here again. 

give me a second and i'll give you the edits.

---

### Post by reckless2k2 on 2007-07-19
sudo nano /etc/kismet/kismet.conf

go down a few lines to where is says:

source=none,none,addme

change it to:

source=bcm43xx,wlan0,wlan0source

then save it. THIS DEPENDS ON YOUR WIFI CARD BEING DEFINED AS WLAN0. IF IT'S SOMETHING ELSE YOU HAVE TO DEFINE IT AS WHATEVER IT IS UNDER IFCONFIG. 

then sudo kismet from terminal. you should be fine then.

i can't remember off hand if interface (wifi) needs to be down or up before running kismet. try both.

---

### Post by tennvolsmb on 2007-07-19
well thanks for the reply but it is still giving me the same FATAL error message "no packet sources are defined"

---

### Post by reckless2k2 on 2007-07-19
this might not be what you want but if you are hear, try this to get there......google backtrack linux....pull and burn the ISO. i use this distro to do any penetration testing because it is designed for it. it's very easy to use. no HDD install required and it'll run off livecd. kernel is patched up for wifi devices and such even for broadcom. inject and sniffing. you'll still need to edit kismet.conf prior to running but you'll see that you just uncomment the bcm43xx area because they have them all in there. 

it will work with backtrack. with stock ubuntu sometimes you have to jump through additional hoops with kernel mods or such to get certain things working whereas pen distros are kinda setup out of box. all the investment would be is a little time and a cd. hahaha. i'm going back to this being a broadcom issue but i could be wrong.

---

### Post by tennvolsmb on 2007-07-19
ok then... well right now im downloading the backtack iso image right now. Is there anything im gonna need to install? is it easy to configure wireless internet on it?

thanks tennvolsmb

---

### Post by reckless2k2 on 2007-07-19
backtrack is kde friendly so you should be alright. once you identify the network there are scripts to bring interface up and such. i can nav around and find all that stuff.

---

### Post by tennvolsmb on 2007-07-19
ok thanks this download still has an hour left to download so that would be great

---

### Post by reckless2k2 on 2007-07-20
did it work out for you?

---

### Post by t4thfavor on 2007-07-20
With a broadcom card you may have to install the firmware(plenty of noob friendly tutorials available). I am not sure if they work without it.
The only source line in kismet.conf should be this. exactly as shown(except for using the correct eth device).
source=bcm43xx,ethX,broadcomSource

where ethX is the interface that the broadcom card comes up as. 

I assure you this works on a stock ubuntu kernel/kismet install, at least on a 4306 pcmcia card.

I messed around with it a bit the other day and was astounded that my broadcom card even worked.

---

### Post by tennvolsmb on 2007-07-20
hey well backtrack i got working but im not sure how to use it still, im getting a different fatal error message but i do like using backtrack for this is and that, thanks for suggesting it and i will also try and download the firmware. if it doesn't work ill get back to you. Thanks for all your help

---

### Post by reckless2k2 on 2007-07-20
hhmmm....post the error or google the error. i know i'm not saying anything you might not have heard but broadcom is not really linux supported. i use atheros chipset which is out of box support on many things like penetration testing distros. it would require that you ebay a cheapy card or get a atheros on board chip. i had pen test friend that had similar experience and had to get atheros orinoco. i have an atheros wifi card collecting dust. let me know.

---


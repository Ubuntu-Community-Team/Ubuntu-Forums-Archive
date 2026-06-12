---
title: "Why must I reset the network to switch between my wireless and EVDO?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-28
I've spent a good chunk of this afternoon tracking down an issue that was driving me nuts...I seriously thought I was going insane.

I could get my EVDO card to work, but then when I would want to connect to my WiFi, it woudn't work.  Then, later, I could get my WiFi to work but my EVDO wouldn't connect.

Then I found out that by restarting my computer, I could connect to the other interface, without problems, but I still couldn't just switch back and forth at will.

So a friend suggested I just reset the network with the following:

```
sudo /etc/init.d/networking restart
```

Lo and behold, it friggin worked!

The strange thing is that he does not need to do this on his laptop to switch between his WiFi and EVDO.

I'm running a Spring PC5740 for EVDO and my built in wireless is Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) according to 'lspci'.  He's running a Verizon card (don't know the model), but I'm not sure of what WiFi.

Any reason for this?  Is there anything I can do to prevent this from happening?

---

### Post by JDuc on 2008-12-29
This same friend of mine wrote a script that will automatically restart the network and check to see if Gnome-PPP is already running before doing so.

I figured I would list it here in case someone else could use it or wanted it.

```
#!/bin/sh
SERVICE='gnome-ppp'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    zenity --error --text "Gnome-ppp is currently running."
    exit 0
else
    zenity --question --text "Would you like to restart networking first?"
    if [ $? = 0 ];
    then
        gksudo /etc/init.d/networking restart
        gnome-ppp
    else
        gnome-ppp
    fi
    zenity --question --text "Do you want to restart networking?"
    if [ $? = 0 ];
    then
        gksudo /etc/init.d/networking restart
    fi
fi
exit 0
```

---

### Post by Tidder on 2008-12-31
Nice script. ;)

Just for completeness' sake, I'm using a Verizon U720 and an Atheros based wifi card.  No issues.

---

### Post by JDuc on 2008-12-31
Yeah- thanks tidder!

---

### Post by crjackson on 2008-12-31
Are you using 8.04 still or is it doing this under 8.10? 8.10's networking manager doesn't have that problem for me using a UM-150 device (also Verizon) and with the same WiFi card. However I did have that issue under 8.04.

---


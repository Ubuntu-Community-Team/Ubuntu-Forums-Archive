---
title: "Internet connection has stopped"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by andydovey on 2011-04-28
Hi, I have been using Ubuntu for about a month now on a computer that I built from scratch and it worked! Ubuntu just configured everything, downloaded all drivers etc with no fuss at all so well done whoever sorted all that lot out!
A couple of days ago my internet connection stopped working. It is a wired connection to a router and works on another computer if I connect from the same cable. 
I have found similar problems described in non beginners threads but I got as far as ifconfig and could not understand what I should do from there. Can you help please? I cant paste what it says in ifconfig as I am sending this on another computer.
Thanks 
Andy

---

### Post by gauth91 on 2011-04-28
Hai dude...May i know whether the network manager indicates that your cable is plugged in?????

---

### Post by andydovey on 2011-04-28
Hi gauth,
I cant find Network Manager
In Network connections it says
Auto ethO Last used: Never
The cable is plugged in though and gives a connection on another computer
Thanks for quick reply
Andy

---

### Post by computerandu on 2011-04-28
I face similar problem with my wireless connection. Sometimes it will not work in Ubuntu and at the same time runs fine on Windows. After few hours when I switch back to Ubuntu the wireless works fine. Strange things always happens.

---

### Post by plucky on 2011-04-28
> I cant paste what it says in ifconfig as I am sending this on another computer.

From a terminal ```
ifconfig > ifconfig.txt
``` and copy the file to a pen drive and post the output from the other computer.

Then open Firefox,and input the address of your router into the address bar and see if you can connect to the router.

What happens if you right click on the network icon in the top panel.

Is the "Enable Networking" ticked?

Then select **Edit Connections**.

Is there a "Wired Connection" setting?
Is that setup correctly?
Are the green LEDs working on the network card?

Can you ping your computer? ```
ping -c 5 localhost
```

Can you ping the router ```
ping -c 5 192.168.x.x
``` 

where 192.168.x.x is the actual address of your router.

---

### Post by grahammechanical on 2011-04-28
Are you saying that you do not see a Network Manager icon in the top panel? With a wired connection it will look like two arrows going in opposite directions. When disconnected the icon changes to four concentric arcs radiating upwards with a red exclamation mark against it. You should also get messages saying either that you are connected or that you are not connected. Are you not getting any of these things?

I suggest two things to start with. 1) Go to System>Preferences>Startup Applications and make sure that Network Manager is ticked as one of your startup applications. 2) right click on the top panel and select Add to panel and select Notification Area. If you are not seeing a Network Manger icon then this will put it back.

Regards.

---

### Post by andydovey on 2011-04-28
Hi Plucky, thanks for your help.
I got the contents of ifconfig onto a pen drive but I cant get this computer (windows vista) to do anything with it, I will keep trying.
In the mean time, 
Enable networking is ticked, 
In Edit Connections, under Wired Connections it says Auto ethO    Last Used   Never
Network card is built in to m/board (ASUS P7H55-M PRO) so I cant see any LEDs
When I ping the computer it says 5 pckts transmitted, 5 pckts received

I didnt realise the icon on the right was Network Manager, it looks like a telephone with a line through it 

Thanks again
Andy

---


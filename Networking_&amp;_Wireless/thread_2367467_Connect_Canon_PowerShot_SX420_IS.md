---
title: "Connect Canon PowerShot SX420 IS"
date: 2017-07-30
forum: Networking &amp; Wireless
---

### Post by BobvanderPoel on 2017-07-30
Got a Canon PowerShot SX420 camera the other day. Nice camera :)

I works fine to transfer photos via USB. But, is should work over wifi as well. One of my routers has WPS enabled, but the camera just sits there with a "looking for network" message.

I'm not sure of the process I need. Do I need to signal the camera from the computer or something, or should it just connect to the router where I can then connect to the network using my file brower?

Thanks.

---

### Post by Hadaka on 2017-07-30
Hi, please open a terminal...ctrl/alt/t... and do..
```
cat /etc/timezone
sudo iw reg get
```
post the output....
Then RTFM [read the fine manual] for your camera and router.
Starting here..
[COLOR=#006621][FONT=Roboto]gdlp01.c-wss.com/gds/7/0300022097/01/pssx420is-cu-en.pdf

[/FONT][/COLOR]Thanks.

---

### Post by BobvanderPoel on 2017-07-30
Just before we get side tracked too much ... my computer doesn't have wifi. It's connected via cable. 

What I'm trying to do is to connect the camera via my router to my LAN where I can, hopefully, connect to it using nautilus (or whatever). My first read though the manual suggests I can do this. The second read I get the impression that my Windows computer has to send something to the router as well of WPS to work. But, I'm confused about it all :)

---

### Post by Hadaka on 2017-07-31
The statement...
"works fine to transfer photos via USB. But, is should work over **[COLOR=#ff0000]wifi[/COLOR]** as well."
Led me to think you were doing this with wifi..not cable.
The camera ..from your statement...
"the camera just sits there with a "looking for network" message."
This means the router never "sees" or gives the camera  an IP address.
Nor does the camera find any connection to the router or network.
All this happens between the router and the camera. And has nothing to do with
the OS...be it Ubuntu,windows or Mac IOs.
So..again..[Read The Fine Manual] to correctly configure the camera so the router
can hand it an IP address.
*If your camera came with a set up disc..it is very likely to be for windows ,apple or android
or...but NO linux/Ubuntu. So to set up the camera as a [local area network] LAN device
will most likely need to be done on a computer that can read the setup disc.
I do see info about access points and network connection on page 84 of the above link, and
while it seems to be about wireless, perhaps once in the menu you will see LAN connection or
get an idea of how to add it as a network device.
Good Luck.

---


---
title: "How To Disable Dialup Modem From Connect On Startup"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by magichsjx on 2007-08-01
HELLO
i AM USING UBUNTU FEISTY. I SETUP MY MODEM USING A LINMODEM AND CONFIGURING WVDIAL AS WELL AS PPPCONFIG. I DON'T KNOW WHY THE MODEM CONNECTS ON STARTUP OF UBUNTU AND I CANNOT ACCESS THE INTERNET. I HAVE TRIED DISABLING DEFAULT ROUTE OPTION ON MODEM MONITOR BUT IT DIDNT SEEM TO HELP IS THERE A FILE I NEED TO EDIT TO TELL THE SYSTEM NOT TO CONNECT TO THE NET AUTOMATICALLY ON STARTUP? PLUS MODEM MONITOR DOES NOT HAVE A ACTIVATE DEACTIVATE OPTION ITS GRAYED OUT. TY FOR HELP.

---

### Post by Chappy7777 on 2007-08-01
Mine does the same thing, I think. W/mine it starts dialing as soon as Ubuntu is being stared (after bios ifo is shown). I think the way to prevent this is to be sure to turn the modem off (I can turn mine off because it's an external serial modem and has an on/off switch) by opening the Network and clicking on "Deactivate". That should, well, deactivate the modem until you open network again and click on Activate to start the dialing. If you rt.click on the top panel add click on "add", you'll see a red telephone Icon. I put that on my top panel, and it allows me to start from there, and tells me when I'm connected and for how long. Sadly, it doesn't say what my conneck speed is. That is something I have never found.

Maybe this will help. I am pretty new at this.

---

### Post by magichsjx on 2007-08-05
Thank you for your response. I did try that but the telephone's activate/deactivate is grayed out. I removed the networking altogether sadly and just use the terminal. I used to have it work with Dapper. True no indication of speed nor of how long you have been on. I never got that to work on Dapper either. Any ideas would be appreciated. Thank you just the same.

---

### Post by scottym on 2007-12-16
I know this is late but if you stillhave the problem of connecting but being able to access the internet here is what I do:

In terminal

sudo poff
then do  command
wvdial

that should get you connected with the proper password if you have added that to your setup.

Now if we just figure out how to stop the auto connect to the internet....:lolflag:

---


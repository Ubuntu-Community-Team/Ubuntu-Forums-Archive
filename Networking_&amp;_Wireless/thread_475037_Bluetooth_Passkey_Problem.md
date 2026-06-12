---
title: "Bluetooth Passkey Problem"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by penguin666 on 2007-06-15
I think this is a common problem. but I can't seem to find any solution for it.

I have just installed ubuntu, and i have a bluetooth dongle connected to my pc. However when I search with my phone it detects the pc but it doesnt allow me to pair with it. My phone asks to input a pin number so i put one in, however I'm not asked for it in ubuntu, then my phone says failed to pair after a while.

I have tried editing things in hcid.conf that other posts have said, however they have brought no luck at all. Also entering 1234 which is the default passkey doesnt work either.

The bluez-pin software which is already installed according to the package manager should ask me to input the pin in ubuntu. Does this software run in the background all the time? It seems like something is stopping the phone communicating any more to the pc after a certain point, is there some sort of bluetooth firewall security settings that I can turn off?

Thanks

---

### Post by freethinker89 on 2007-07-13
bump

---

### Post by tck on 2007-08-02
I'm having the same issue.
the dongle was given to me by a friend 

Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by volkswagner on 2007-08-02
Same boat here.  Phone wont pair but i can transfer files after following this post

if you just want to transfer files try it, also what phones are you using?

>  Re: [IDEA] Better Bluetooth support.
Today almost every cell phone, notebook comes with bluetooth. There are lots of bluetooth mouse, headphones, remote controls, etc. I believe it is important to have good bluetooth support.
I know people that goes back to windows because of this things.

At least having something in System->Preferences that automatically installs the needed packages and let you configure bluetooth and search for devices.
With the help of the Ubuntu community we can develop something.
This is what I did to have bluetooth on my DELL inspiron 9400 that may be useful, it can be done automatically.

On a terminal type:
sudo apt-get install gnome-bluetooth bluez-gnome python-bluez python-libbtctl bluez-utils bluez-gnome
Now "Bluetooth File sharing" will appear under Applications->Accesories, once activated a new icon will appear near the clock to identify it.
To execute it automatically at startup, go to System->Preferences->Session-> Startup Programs, click on new and type gnome-obex-server.
Restart your computer. (Maybe doing something else this won't be needed)
You will also have under System->Preferences->Bluetooth preferences some extra configuration to play with to make you cellphone, etc work.
To search for bluetooth devices:
Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual) and then search for the device with this command:
sudo hidd --search
If that command doesn't work, try this one:
hcitool scan
Hint: If no devices are being shown and you are using Edgy Eft (6.10), you may try
sudo hciconfig hci0 inqmode 0
See bug [[https://launchpad.net/ubuntu/+source...th/+bug/70718]](https://launchpad.net/ubuntu/+source...th/+bug/70718]) #70718. If this helps, you may add the hciconfig command (without "sudo") to your /etc/rc.local file for a permanent workaround.
To change the location that files are saved to when using bluetooth transfers
gconf-editor
Then navigate to
/apps/gnome-obex-server
where you can specify the save directory and also turn off that annoying dialogue box!
__________________
Last edited by fmaste : 4 Weeks Ago at 03:27 PM. 

I feel so close with my nokia 6123, i think it may  be a proprietory problem, seems to be related to the channel the phone needs to use.  i get real close with pairing following this thread got oopup for pin but no joy

[http://ubuntuforums.org/showthread.php?t=403717&highlight=bluetooth+pairing]("http://ubuntuforums.org/showthread.php?t=403717&highlight=bluetooth+pairing")


here is wher i got even closer but seem channel on phone is an issue

[http://ubuntuforums.org/showpost.php?p=1779032&postcount=3]("http://ubuntuforums.org/showpost.php?p=1779032&postcount=3")

good luck

---

### Post by efrenefren on 2008-01-26
have the same problem too.
and there's no bluez-pin in gutsy.
its in the package bluez-gnome

---

### Post by brokenhachi on 2008-02-02
i just figured this out i think... when ur phone or whatever asks you for a pw, just put whatever in.. i put 1111 and then ubuntu pops up with something at the top that says click for pw pairing or something like that.. then u just put the same pw in and click ok.


worked for me.

---

### Post by diegosacchetti on 2008-02-03
> **penguin666 said:**
> I think this is a common problem. but I can't seem to find any solution for it.

I have just installed ubuntu, and i have a bluetooth dongle connected to my pc. However when I search with my phone it detects the pc but it doesnt allow me to pair with it. My phone asks to input a pin number so i put one in, however I'm not asked for it in ubuntu, then my phone says failed to pair after a while.

I have tried editing things in hcid.conf that other posts have said, however they have brought no luck at all. Also entering 1234 which is the default passkey doesnt work either.

The bluez-pin software which is already installed according to the package manager should ask me to input the pin in ubuntu. Does this software run in the background all the time? It seems like something is stopping the phone communicating any more to the pc after a certain point, is there some sort of bluetooth firewall security settings that I can turn off?

Thanks
>>>>>>>>
'm experiencing the same problem trying to connect an Ibm T41 (Ubuntu 7.10) with a T60 (Win Xp) : when trying to send files a pairing passkey  is required by the program running on XP, but not on Ubuntu and the connection fails. I tried also to edit hcid.conf, setting the parameter pairing none and security none, but nothing different happened.
Is there anything more to do ? Thanks

---

### Post by diegosacchetti on 2008-02-05
> **diegosacchetti said:**
> >>>>>>>>
'm experiencing the same problem trying to connect an Ibm T41 (Ubuntu 7.10) with a T60 (Win Xp) : when trying to send files a pairing passkey  is required by the program running on XP, but not on Ubuntu and the connection fails. I tried also to edit hcid.conf, setting the parameter pairing none and security none, but nothing different happened.
Is there anything more to do ? Thanks

>>>>>>>> 
I solved this installing gnome-vfs obexftp : now a passkey pop is displayed and pairing can be completed

---

### Post by steveneddy on 2008-02-05
Using [blueman]("http://blueman.tuxfamily.org/") should solve other bluetooth problems.

You should also install gnome-obex-server and make it start when you boot by putting it in System --> Preferences --> Sessions

Try[ this link]("http://ubuntuforums.org/showthread.php?t=586105") also.

---


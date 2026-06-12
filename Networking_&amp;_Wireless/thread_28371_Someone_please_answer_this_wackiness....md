---
title: "Someone please answer this wackiness..."
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by DoubleDangerClub on 2005-04-19
I've been through a ton of things and still can't get my Linksys WPC11 v.3 pcmcia card to work with Hoary 5.04.

My question:

My card worked flawlessly without doing anything before Hoary (it showed up automagically in the network settings panel).  So why doesn't it show up anymore since the upgrade?  Is it the pcmcia settings or the network card settings in the new kernel?

Anyhow, I'd really like someone to just let me know if I'm alone in this or if my computer's just insane and being dumb.  Thanks.  Sorry to sound somewhat pathetic in this, I'm just frustrated that it worked and now it won't.

Thanks.  DDC

---

### Post by ming0 on 2005-04-20
finally a post I might be able to help with :)

What sort of output do you get from the following command:
 ```
iwconfig
```

---

### Post by DoubleDangerClub on 2005-04-20
This is my output from iwconfig:

```
jake@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
``` 

Thank you so much for helping.

DDC

---

### Post by ming0 on 2005-04-20
Darnit, I have the *exact* same card somwhere in the hose, but I can' t seem to find it :roll:

Oh well...

Let's see if you have drivers loaded for it. What happens when you try these commands:```

lsmod |grep orinoco
``` ```
lsmod |grep hermes
``` If you get no output, try these commands: ```
sudo modprobe orinoco
``` ```
sudo modprobe orinoco_cs
``` ```
sudo modprobe hermes
```If those seem to go without any errors, try the 1st set of commands again, and if that tells you that the modules are indeed loaded, then try the original command:```
 iwconfig 
``` Let me know what you get out of all this :)

---

### Post by DoubleDangerClub on 2005-04-20
Here's what I got from all this:

```

jake@ubuntu:~$ lsmod |grep orinoco
jake@ubuntu:~$ lsmod |grep hermes
jake@ubuntu:~$ sudo modprobe orinoco
Password:
jake@ubuntu:~$ sudo modprobe orinoco_cs
jake@ubuntu:~$ sudo modprobe hermes
jake@ubuntu:~$ lsmod |grep orinoco
orinoco_cs              8968  0
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
pcmcia                 21380  5 orinoco_cs
pcmcia_core            53568  3 orinoco_cs,pcmcia,yenta_socket
jake@ubuntu:~$ lsmod |grep hermes
hermes                  7936  2 orinoco_cs,orinoco
jake@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jake@ubuntu:~$

``` 

Again, thank you so much for helping me out.  Since it comes up with info the second time I grep those commands, wouldn't that mean the drivers should be working?

DDC

---

### Post by ming0 on 2005-04-20
Seems like they should work... Maybe try loading the modules with modprobe, and then use the command: ```
cardctl eject
```pull the wifi card out, reseat the card, and run: ```
cardctl insert
``` Now try ifconfig again.
(if cardctl doesn't work, you are probably safe just pulling the card out **this is what I do, but the usual 'i am not responsible for explosions disclamer' applies**)

Do we get any more results?

---

### Post by DoubleDangerClub on 2005-04-20
When I do the eject after loading, it's all good.
When I ctl insert, the lights on the card come on and stay on for a second, but when the terminal prompt comes back empty, the lights turn out and no wifi.

Suck.

Do you think this could be more of a kernel issue dealing with the pcmcia cards?

Thanks again.  You're helping me learn a bunch about this.

DDC

---

### Post by ming0 on 2005-04-20
I forgot, but you will need to be root to use the cardctl command--did you already do it that way?

I seriously doubt it's a kernel problem--most likely just the modules aren't loading at boot for some reason...

One thing that might be easy would be to add the following lines to /etc/modules:  ```
orinoco
orinoco_cs
hermes
``` (you will need to do that as root), save the changes, reboot, and try iwconfig again...

---

### Post by DoubleDangerClub on 2005-04-20
I added those lines to the /etc/modules.
I even did the modprobe...etc,
I did the cardctl eject and cardctl insert,
did iwconfig and still this:

```

jake@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

``` 

It just doesn't want to see the card.  Anything else to suggest? :)
Thanks.

DDC

---


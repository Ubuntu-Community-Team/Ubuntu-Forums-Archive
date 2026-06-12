---
title: "blueman for ubuntu 8.04 hardy"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by spicyraj on 2008-11-18
hey guys i am not able to install blueman in hardy
Actually i want to connect to internet using bluetooth through GPRS.
please give me steps to install it
or suggest me other way to connect using bluetooth GPRS
[http://blueman.tuxfamily.org](http://blueman.tuxfamily.org)
[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)
i m waiting
bye!

---

### Post by bem202 on 2008-11-26
I can't help you on connecting to your phone via bluetooth for internet BUT to install "blueman" just copy and paste the commands they have [listed]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56") into the terminal and you are set.

To make it even easier. After you run this:"sudo apt-get install update", just type "sudo apt-get install blueman".

Also, just a little advice on posting. Saying things like "i am waiting. bye!" will tend make people want to make you wait more.

---

### Post by tkmunzwa on 2009-04-01
> **spicyraj said:**
> hey guys i am not able to install blueman in hardy
Actually i want to connect to internet using bluetooth through GPRS.
please give me steps to install it
or suggest me other way to connect using bluetooth GPRS
[http://blueman.tuxfamily.org](http://blueman.tuxfamily.org)
[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)
i m waiting
bye!

I'm connected to the 'net using GPRS over bluetooth right now, using 8.04. I just recently managed to do this, my only hope is that you still require the information.

The steps i took are:
1. Edit /etc/network/interfaces add the following lines:
```
auto bnep0
iface bnep0 inet dhcp
```. Restart the network services ```
sudo /etc/init.d/networking restart
```

2. Edit /etc/modules - add the following line
```
bnep
```

3. Enable bluetooth on PC and handset. I had already paired my phone with PC already, so I suggest you do the same before proceeding (not sure if it affects anything). Next step is to get the phone's bluetooth hardware address. use the following command on a console
```
hcitool scan
```
I got ```
00:16:B8:BD:2E:93       TK_Z550i
``` The hardware of your handset will be different, and if you have more than one discoverable bluetooth devices in range, all will be listed. Note down address of your handset.

4. Connect to handset using pand: ```
sudo pand -r PANU -c 00:16:B8:BD:2E:93 -e bnep0
```

5. The first time, my phone (SonyEricsson Z550) asked "(Computer Name) want's to use phone as a modem. Allow/Deny"

6. After allowing, connection came up! (you can check using ```
ipconfig bnep0
``` which should show you an IP address assigned to the bnep0 interface. Or simply opening Google in a browser)

I hope you find this was useful, and that I did not skip a stage. My GPRS is slow - but it's better than no connection at all.

*Not all this is original research, btw. I consolidated & tweaked a number of suggestions I found on several threads, but they were mostly talking about using phone to **dial out** using specific commands, and not using the preconfigured GPRS connection.

---


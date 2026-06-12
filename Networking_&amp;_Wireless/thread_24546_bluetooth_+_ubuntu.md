---
title: "bluetooth + ubuntu"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by moore on 2005-04-07
O:)  Hi i have Ubuntu Hoary 5.0.4
I have a problem i want to connect my moblie to Ubuntu with bluethoot.
Can somebody help me please ?
I searching for a simple tutorial.
Thanks  ;-)

---

### Post by sas on 2005-04-08
I've not found any information specific to Ubuntu, and you've not said which phone you have...here's a list of information on linux and mobile phones [http://tuxmobil.org/phones_linux.html](http://tuxmobil.org/phones_linux.html), most of the pages come with HOWTOs on how to get bluetooth working...

---

### Post by rwabel on 2005-04-08
[QUOTE=moore]O:)  Hi i have Ubuntu Hoary 5.0.4
I have a problem i want to connect my moblie to Ubuntu with bluethoot.
Can somebody help me please ?
I searching for a simple tutorial.
Thanks  ;-)[/QUOTE]

here you go
[http://www.watkissonline.co.uk/linuxbluenet.html](http://www.watkissonline.co.uk/linuxbluenet.html)
[http://usefulinc.com/software/gnome-bluetooth/](http://usefulinc.com/software/gnome-bluetooth/)

unfortunately some of the packages in hoary are not working well. One should mix it with warty packages. I can't remember another link where I read that.

when I find it again I'll post it

good luck

---

### Post by hamil on 2005-04-17
Hey!

Well I have experienced some difficulties with Hoary and bluetooth connection with my celluar phone.
In warty I could send and recieve files from/ to the celluar via Nautilus. In Hoary, I am not able to find out why it is not working.
I have installed all the diffrent packages, bluez-utils, gnome-bluetooth, bluez-pin, obexftp, obexserver...
But I am not able to communicate with my celluar..
When i search for other bluetooth devices with the computer, it recognice my celluar. But I am not able to send anything to the celluar, since there is no option for it anywhere. If I do a search with my celluar, it can not find any active devices.
In Warty, i had a nice possibility to send files via bluetooth in Nautilus, just by right cliking the item. This option is no longer visible in Hoary...

Is there anybody who have a solution for this problem?

Brgds
/Lasse

---

### Post by rwabel on 2005-04-17
[QUOTE=hamil]Hey!

Well I have experienced some difficulties with Hoary and bluetooth connection with my celluar phone.
In warty I could send and recieve files from/ to the celluar via Nautilus. In Hoary, I am not able to find out why it is not working.
I have installed all the diffrent packages, bluez-utils, gnome-bluetooth, bluez-pin, obexftp, obexserver...
But I am not able to communicate with my celluar..
When i search for other bluetooth devices with the computer, it recognice my celluar. But I am not able to send anything to the celluar, since there is no option for it anywhere. If I do a search with my celluar, it can not find any active devices.
In Warty, i had a nice possibility to send files via bluetooth in Nautilus, just by right cliking the item. This option is no longer visible in Hoary...

Is there anybody who have a solution for this problem?

Brgds
/Lasse[/QUOTE]

that's a known problem. There is a bug in the hoary package as I read once on a website. Unfortunately I can't remember the site.

But they suggested to downgrade the bluetooth packages to the warty one and it should work.

I hope that the hoary one will work once

---

### Post by Grenshad on 2005-05-08
How can I tell synaptic or apt to use the usefulinc or warty repository instead of hoary ones ? :-/

---

### Post by rwabel on 2005-05-14
you can force packages from a repository and then to not let apt/synaptic upgrade to a newer you can lock the installed version.

---

### Post by anders.ostling on 2005-05-15
Hi
AFAIK, the problem with not being able to transfer stuff is caused by a change in gnome 2.10. Nautilus obviously have a new package called "nautilus-sendto", and I can not see that BT is included (yet). For me, BT Manager detects both my Palm and my Sony Ericson V800 phone. I am also able to dial out to Internet over BT/ppp. I have a Vodafone connection, and it seems to work just fine.

A strange thing is that my BT dongle (CSR based) did not work when it was inserted into my USB hub. The command hciconfig hci0 up returned an "invalid i/o" message. But moving it to an internal USB port solved the problem. Strange since I have many other USB stuff on the HUB (mouse, disk etc).

Anyway, if anybody finds a way to get back the "Send to Bluetooth" menu option, please leave a note here.

Anders

---

### Post by Grenshad on 2005-05-15
[QUOTE=anders.ostling]Hi
AFAIK, the problem with not being able to transfer stuff is caused by a change in gnome 2.10. Nautilus obviously have a new package called "nautilus-sendto", and I can not see that BT is included (yet). For me, BT Manager detects both my Palm and my Sony Ericson V800 phone. I am also able to dial out to Internet over BT/ppp. I have a Vodafone connection, and it seems to work just fine.

A strange thing is that my BT dongle (CSR based) did not work when it was inserted into my USB hub. The command hciconfig hci0 up returned an "invalid i/o" message. But moving it to an internal USB port solved the problem. Strange since I have many other USB stuff on the HUB (mouse, disk etc).

Anyway, if anybody finds a way to get back the "Send to Bluetooth" menu option, please leave a note here.

Anders[/QUOTE]

Same for me, when i heard lots of people who said bluetooth works well on hoary, i try to plug my dongle directly on the USB ports (no more on my USB hub), and all works well since. To send files to my phone i use the "open with" dialog where i add "gnome-obex-send" in the wait of an official add to the "send to" menu of nautilus :).
(sorry for my horrible english speaking  ](*,) )

---

### Post by rwabel on 2005-05-15
[QUOTE=Grenshad]Same for me, when i heard lots of people who said bluetooth works well on hoary, i try to plug my dongle directly on the USB ports (no more on my USB hub), and all works well since. To send files to my phone i use the "open with" dialog where i add "gnome-obex-send" in the wait of an official add to the "send to" menu of nautilus :).
(sorry for my horrible english speaking  ](*,) )[/QUOTE]
 bluetooth is working for me and I can see my Sony Ericsson T610 and I can also see my computer from my mobile phone. But I cannot send from and to my phone. When I want to send from my phone I cannot see my computer. Did you achieve that?

---

### Post by Grenshad on 2005-05-15
I have to launch "Bluetooth Share Manager" before trying to send something from my phone (T630) to my computer. To send from computer to phone i use the gnome-obex-send command, which send the file of your choice to a bluetooth device (a pop-up let you choose it).

---

### Post by rwabel on 2005-05-15
[QUOTE=Grenshad]I have to launch "Bluetooth Share Manager" before trying to send something from my phone (T630) to my computer. To send from computer to phone i use the gnome-obex-send command, which send the file of your choice to a bluetooth device (a pop-up let you choose it).[/QUOTE]
 I've Bluetooth File Sharing and Bluetooth Manager but still cannot send. I can connect to my pc, but it doesn't show up when I want to send from my phone.

I've also tried with "open with" gnome-obex-send. I could then choose my phone but I get the following error "remote device doesn't support receiving objects". But my phone can receive files.
and I don't get asked on my phone if I want to receive the file

---

### Post by rwabel on 2005-05-16
it's working now. I came across this howto [http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth]("http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth")

---

### Post by anders.ostling on 2005-05-18
I think that the original poster also wanted to have network from his PC over the phone. Here is what I did

1. Create a file /etc/ppp/peers/gprs-vodafone

lcp-echo-failure 0
lcp-echo-interval 0
nodetach
debug
show-password
connect '/usr/bin/wvdial --chat --config /etc/ppp/peers/gprs-wvdial.conf vodafone'
disconnect /etc/ppp/peers/sharp-disconnect-chat
/dev/rfcomm0
115200
crtscts
:212.73.32.10
noipdefault
ipcp-accept-local
defaultroute
usepeerdns
novj
nobsdcomp
noaccomp
nopcomp
noauth
user "vodafone"
password "vodafone"

2. Create a file /etc/ppp/peers/gprs-wvdial.conf

[Dialer Vodafone]
Init1 = ATH
Init2 = ATE1
Init3 = AT+CGDCONT=1,"IP","internet.vodafone.net","",0,0
Dial Command = ATD
Phone = *99***1#
Username = vodafone
Password = vodafone

3. Create a shell script /root/btdial.sh

#!/bin/sh
rfcomm bind /dev/rcomm0 00:0F:DE:8F:F8:98
pppd call gprs-vodafone

EDIT: Note that the phone's mac address must be changed to match your phone. Do a 'hcitool scan' to find out your phone's address.

Assuming that you have a working bluetooth connection (which you should have after reading through this thread), then you also should have a dialup connection. If you dont have Vodafone, then you need to change those params as well.

Contact me if there is any problems with the instructions above!

Anders

---

### Post by erick_rdch on 2005-06-11
[QUOTE=Grenshad]Same for me, when i heard lots of people who said bluetooth works well on hoary, i try to plug my dongle directly on the USB ports (no more on my USB hub), and all works well since. To send files to my phone i use the "open with" dialog where i add "gnome-obex-send" in the wait of an official add to the "send to" menu of nautilus :).
(sorry for my horrible english speaking  ](*,) )[/QUOTE]

Hey, I'm new to ubuntu and debian, but not to linux. I have been using madrake for about 3 or 4 years and now I love Ubuntu.

I have a bluetake dongle, BT009X to be more specific. I just install the bluez and gnome-bluetooth packages using synaptic, and i follow your great idea (open with) I have no trouble at all :D  Sorry for my english.

Hola! soy nuevo en Ubuntu y Debian pero no en linux. Tengo 3 o 4 años usando mandrake y ahora amo a Ubuntu.

Tengo un dongle bluetake, BT009X para ser mas especifico. Acabo de instalar los paquetes bluez y gnome-bluetooth usando synaptic, y segui tu grandiosa idea (abrir con) No tuve ningun problema :D

---

### Post by atlas95 on 2005-07-17
My phone ask me a password to send a file to it...i configure this password on the phone but how to config it on the computer?
My phone is a samsung sgh-d500...

Thanks for your help...

---

### Post by schumifer on 2007-01-14
Probably too late now but the password thing is very easy actually. Just enter what 4 numbers you wish on the first device that asks you to, and then enter the same pasword on the next device.
 Now , for a question of my own.
I use kubuntu 6.10 edgy.
I try to connect to to my qtek 8080 smartphone. When i try to connect to the pc through the phone it all works great and i can send files.
However when i try to pair the pc with the smartphone (the other way around) i can't even discover the device. I setup a new discovery job in bluetooth settings but no matter which job i setup i always get a horrible sound and a popup that says

Device search job /home/alx/.kde/share/apps/kbluetoothd/discovery_jobs/8080 returned with error code 127.

Also i couldn't connect to my motorola bluetooth handsfree. 
Any tips or recommendations?
Thanks

---

### Post by Angry penguin on 2007-01-25
I am having the same problem when pairing with the computer, my phone is detected, each device sees the other and when I try to connect to my computer from my phone or vice versa I have to put in a code. How do I know what code to put in to connect to the computer?

There is no dialog box that pops up and asks me for the pin on the phone, and I haven't set a pin for the computer.

What the hell am I missing?

---

### Post by julv on 2007-01-26
I had this problem too, i solved it by using kbluetoothd instead of gnome-bluetooth. 
Once kdebluetoothd is launched, a pop up window will open if you try to initiate the connection from the phone (a K750 in my case) and enter a pin. The syncing worked without problem with multisync as well (although i think it is only one way so far, i didn't really push it further, just wanted to save my contatcs).

I kinda read that if was possible to solve the popup problem with the gnome app, but i an trying as much as possible to use only graphical solution, just so that i can convince the doubters that you don't actually have to use the terminal every other day...

---


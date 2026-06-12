---
title: "No Internet Connectivity"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by merlinus on 2018-08-14
I just did an upgrade to 18.04 LTS, which seemingly worked perfectly.  However, after the computer restarted, I have no Internet, not wired, not wireless.  Rebooting did not help, but the machine is connected to my router.

Assistance appreciated!

---

### Post by kc1di on 2018-08-14
Give a little more info on your system, What wireless card and Ethernet cards are in the machine?

---

### Post by merlinus on 2018-08-14
Thanks for responding.  Any easy way to find out?  I obviously cannot post the output of terminal commands.

---

### Post by merlinus on 2018-08-14
When I wake up the laptop, it says the wired connection is established.  But I do not see Places/Connect to Server in the menu, so it is not finding the LAN.  The device shows up in my router, both wired and wireless (depending upon which connection I choose).

But my best guess is that the OS is not activating the wireless and LAN cards.

lspci shows an Ethernet controller (Realtek PCI Express Gigabyte}, but no wireless card.

---

### Post by merlinus on 2018-08-14
I just did a power-off restart, and the machine says it is connected to my wifi network, but I still cannot access any Internet sites.

However, I can access the laptop from my desktop via the LAN.  So whatever may show (or not) in the laptop lspci, the network card is being found by the new OS.

Very mysterious....

---

### Post by merlinus on 2018-08-16
[FONT=Verdana]Here is how I resolved the problem, in case         anyone else runs into this issue.

[/FONT]

     [FONT=Verdana]$ gksudo gedit         /etc/resolvconf/resolv.conf.d/base
        
        Then put your nameserver(s) in like so:
        
        nameserver 8.8.8.8
        
        $ gksudo gedit /etc/resolvconf/resolv.conf.d/head
        
        nameserver 8.8.8.8
        
        Then update resolvconf:
        
        $ sudo resolvconf -u

[/FONT]

     [FONT=Verdana]Clearly the computer was not picking up the         nameservers placed in the connections dialog boxes for wired and         wireless, and therefore could not connect to any internet sites,         including email servers.[/FONT]

And many thanks to all those who responded, especially the moderators who took time to research this issue -- **[COLOR=#ff0000]NOT!!!!!![/COLOR]**

---

### Post by geoff20 on 2018-08-18
Same problem here. Tried your suggestion gksudo does not work so tried sudo. This allowed me to make the changes but when I rebooted the GRUB gave me error messages about corrupt files.
Had to run fsck which then allowed me to reboot ubuntu and get an internet connection.
However I could not apply my smart DNS settings. It seems that I now have two sets of DNS settings 8.8.8.8,8.8.4.4 plus my smart DNS values.
Perhaps a downgrade to 16.04

---

### Post by merlinus on 2018-08-27
All I can say is that my "solution" is still working perfectly on all three computers which I upgraded to 18.04 from 16.04.

I understand that gksudo has been deprecated, but it still works fine for me.  No doubt just using sudo will work.

I do not know anything about smart DNS settings, however.

---


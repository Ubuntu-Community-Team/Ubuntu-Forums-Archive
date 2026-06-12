---
title: "Wi-Fi Disconnects Frequently"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by sappho+ on 2016-12-29
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Hithere![/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I’vebeen having some wireless connectivity problems on my Lenovo G50 i7.I’ve looked through the threads as much as I could and applied someof the offered solutions but I have not yet been able to fix thatproblem. I’m hoping I could get the help I need here.[/FONT]


[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Here’swhat’s going on:[/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I'm [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]connected as soon as I boot and I stay [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]connectedfor 2-3 hours, [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]but[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]then my connection freezes. I turn a[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]ero[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]planemode on and then off [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]so[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I can reconnect. After the first freeze, it's an hour later and thenit's another freeze. I fix it again with [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]a[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]ero[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]plane[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]mode, and then it's 30 minutes and so on until eventually, my Wi-Finetworks can't read or find any routers around the area (sometimes that happens from the first freeze) and I have toreboot to use the internet again. And the cycle repeats itself. [/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Athome, I can use [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]theEthernet cable [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]andof course, [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]itworks just fine. But whenever I travel or take my laptop with meanywhere else, I have that problem. [/FONT]


[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Thisis my wireless script information:[/FONT][/COLOR][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]
[/FONT][[COLOR=#dd4814][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]https://paste.ubuntu.com/23646908/[/FONT][/COLOR]]("https://paste.ubuntu.com/23646908/")


[COLOR=#000000][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Muchobliged [/FONT][/COLOR]:)

---

### Post by praseodym on 2016-12-29
Hi,

please try:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=[COLOR="#FF0000"]1[/COLOR]" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. Not better? Try "2" (in red)

---

### Post by sappho+ on 2017-01-06
This seems to have worked. I haven't had any problems since. Thanks!

---


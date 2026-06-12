---
title: "Linux cannot find my wireless system"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by nitestar on 2008-12-25
I have a dual boot  in my laptop. I choose which OS to use on startup. I prefer Linux as I am trying to wean myself from IE and Windows XP Pro.     The oldest son tried for a couple of hours last night to get  Linux in the laptop to see the wireless. Still No go.


My question is
It will not recognize my wireless  system for the house.I can get on the internet . No matter how many times we install the code, passwords and other stuff it asks for or reboot it will not recognize it. We have downloaded all the updates for it and still no go .Over 70 updates last night. I think today we will wipe it out  and reinstall the Linux.
I am trying to get away from IE and go 100% Linux.
I think there is a 10 something version and will try to down load that.
Do any of you have any suggestions that may help or ease the pain ?

Second question.
Will  Linux see the CD from the HP printer if I try to install it on the Linux system in my laptop. ?

This is  getting frustrating no end.

---

### Post by shifty_powers on 2008-12-25
the latest version, 8.10, is better for wireless.

when you have it installed, give us the output of

```
sudo iwlist scan
```

and

```
lspci
```

both entered into terminal, applications>accessories>terminal

also, have you checked system>administration>hardware drivers to see if there are any closed source drivers for your wireless?

---

### Post by mapes12 on 2008-12-25
If the above fails then give [WICD]("http://wicd.sourceforge.net/") a go.

---

### Post by ugm6hr on 2008-12-25
> **shifty_powers said:**
> both entered into terminal, applications>accessories>terminal
The details from this are useful too:
```
lshw -class network
```

And confirm which version of Linux you are using.

---

### Post by nitestar on 2008-12-25
To clarify a bit.
 I am using Ubuntu 8.4

It is getting on the internet just fine.
 It  is the wireless that isn't working, such as wireless printing to my HP printer.

Thank you for the help

---

### Post by igknighted on 2008-12-25
HP drivers should all be included.  Just plug it in and it should work.

Here is a list if you want to double check: [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)

---

### Post by ugm6hr on 2008-12-25
> **nitestar said:**
> To clarify a bit.

If you want help with wifi, try reading and responding to the previous posts fully.

The link below about How to get help here might be useful too.

---

### Post by igknighted on 2008-12-25
> **ugm6hr said:**
> If you want help with wifi, try reading and responding to the previous posts fully.

+1... unless we know exactly what hardware you have, and some information about how it is currently configured (the outputs of the commands people have asked for), we really cannot begin to help you.

---

### Post by PembyR6er on 2009-01-04
Not to thread hijack, but I'm having the same issue.  This is what I got when I ran "sudo iwlist scan."  It looks like it's detecting a network?
Ubuntu 8.10
Gateway 450ROG notebook (~4 years old....as old as the moon in computer world)

matt@matt-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:C8:1B:00
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-25 dBm  
                    Extra: Last beacon: 16ms ago
          Cell 02 - Address: 00:19:E4:39:C3:E1
                    ESSID:"JESSE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-52 dBm  
                    Extra: Last beacon: 56ms ago
          Cell 03 - Address: 00:1C:F0:C0:8A:0B
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 52ms ago
          Cell 04 - Address: 00:02:6F:47:B2:00
                    ESSID:"basewireless_Pemberton122-01"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=59/100  Signal level=-65 dBm  
                    Extra: Last beacon: 248ms ago

pan0      Interface doesn't support scanning.

REsul;ts of "lspci" in terminal

---


---
title: "wireless"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by davellew69 on 2009-04-27
help!!! how on earth do I set up wireless on ubuntu, I have read different postings..and am lost!

---

### Post by Sprut1 on 2009-04-27
Those who read this are also lost...

First show output of "iwconfig" to check if there are any interfaces at all. The problem could be anything based on what you tell us.

---

### Post by davellew69 on 2009-04-27
now i am really lost? what does the above mean?

---

### Post by Sprut1 on 2009-04-27
Do you know how to use the terminal?

From menu Programs > Accessories > Terminal

Type "iwconfig" and print the output here.

---

### Post by Roadbloc on 2009-04-27
im not sure what you mean exactly....
are you having trouble connecting to your wireless hub or just getting ubuntu to recognise your wireless card?

---

### Post by 3rdalbum on 2009-04-27
Go to a terminal (Applications > Accessories > Terminal), type in this:

```
iwconfig
```

Copy and paste the result into a new post so we can see what network devices have been recognised on your computer.

Also click the network manager (it's one of the icons in the top panel on your screen, could be a picture of two computers) to see if your card is running and detecting networks.

---

### Post by davellew69 on 2009-04-27
eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=-72 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8190   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=-72 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8190   Missed beacon:0

---

### Post by davellew69 on 2009-04-27
I don`t seem to be able to find network manager?

---

### Post by Roadbloc on 2009-04-27
In that case id say ubuntu does not recognise your wireless card. Do some hunting for a driver for ubuntu on the web, and if no luck, there is an app that lets you use windows drivers for ubuntu. :)

---

### Post by davellew69 on 2009-04-27
there is some bar icon, when i stick the card in  i brings up all avalible conections? is that network manager

---

### Post by Sprut1 on 2009-04-27
sound like it, is your wireless router showing there? Click on it

---

### Post by davellew69 on 2009-04-27
ok i click on my homeconnection and i get a blue arrow going round a globe

---

### Post by Sprut1 on 2009-04-27
And when that stopped did you get a message? Do you have internet connection now?

---

### Post by davellew69 on 2009-04-27
no connection made? the arrow just turns, i type my code in and all stops. thats where i get lost.

When I ran windows on wirless at home i got a message about the card being wep, and not being compatible with my routor, but at work i could connect with out a problem? could this be an issue?

---

### Post by Sprut1 on 2009-04-27
> **davellew69 said:**
> no connection made? the arrow just turns, i type my code in and all stops. thats where i get lost.

When I ran windows on wirless at home i got a message about the card being wep, and not being compatible with my routor, but at work i could connect with out a problem? could this be an issue?

You are not making too much sense.

If no connection was made and you typed the correct password trying to connect to correct connection, it's probably a driver problem of some sort. Could you connect at work using Ubuntu? Or was that Windows too?

---

### Post by davellew69 on 2009-04-27
am i correct in thinking , if I know the pass key I just enter it and i should connect? if so I may try it at work and see if it connects

---

### Post by davellew69 on 2009-04-27
I could connect at work on windows, not tried ubuntu at work, I have another laptop which runs windows and connects wireless at home , but it is a newer one and the card is built in

---

### Post by Sprut1 on 2009-04-27
> **davellew69 said:**
> am i correct in thinking , if I know the pass key I just enter it and i should connect? if so I may try it at work and see if it connects

Yes, have you tried connecting to same router using a Windows machine? Do you know FOR SURE, that the router is working? I'm just trying to rule out what might be the problem here. If you type in the wrong password, installing new drivers won't work...

---

### Post by ndefontenay on 2009-04-27
My god. I have no idea. For the first time ever it worked directly after a fresh install of ubuntu 9.04 on a vaio!!!

no ndiswrapper, no crappy windows driver, all native. So cool.

Install 9.04 :)

---

### Post by davellew69 on 2009-04-27
my machine is a viao and i run 9.04? al  i can think to do is try it at work?

---

### Post by Sprut1 on 2009-04-27
> **davellew69 said:**
> my machine is a viao and i run 9.04? al  i can think to do is try it at work?

Yep, good luck to you

---

### Post by davellew69 on 2009-04-27
thanks for the help

---

### Post by Roadbloc on 2009-04-27
the network manager should look like 2 computer monitors, one behind the other, like in ms-windows. Although it does depend on what theme you have installed.

---


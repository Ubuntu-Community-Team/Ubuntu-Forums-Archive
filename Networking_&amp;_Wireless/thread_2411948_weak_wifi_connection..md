---
title: "weak wifi connection."
date: 2019-02-05
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2019-02-05
Hello All

What can I do to trouble shoot a weak wireless computer and or, a weak wireless router

My Net Gear wireless G router worked fine for the last year.  Today at noon I first had problems with my wireless HP printer not responding.  I deleted and reloaded the printer and it worked.  This evening I could not get my HP 15-r031ds lap top computer to hook up to the internet unless I moved my computer next to the Net Gear wireless G Router.  The router and computer worked fine for the last year.

A second computer we have works the same with this Net Gear router.

Gordon33

---

### Post by gordon33 on 2019-02-05
gordon@HP-15-Notebook-PC:~$ lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
gordon@HP-15-Notebook-PC:~$

---

### Post by gordon33 on 2019-02-06
gordon@HP-15-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Time0415"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:05:D5:80   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:52   Missed beacon:0

---

### Post by chili555 on 2019-02-06
> Link Quality=38/70 This and the sudden nature of the occurence suggests that one or both of the antenna connections is loose. Can you please check?

---

### Post by gordon33 on 2019-02-06
Hello chili555

The Antenna on the router looks the same as I remember it.  What is "Link Quality=38/70 "

gordon@HP-15-Notebook-PC:~$ Link Quality=38/70 

Command 'Link' not found, did you mean:

  command 'ink' from deb ink
  command 'dink' from deb freedink-engine
  command 'link' from deb coreutils

Try: sudo apt install <deb name>


Gordon33

---

### Post by chili555 on 2019-02-06
> wlan0 IEEE 802.11 ESSID:"Time0415" 
Mode:Managed Frequency:2.462 GHz Access Point: 00:24:B2:055:80 
Bit Rate=48 Mb/s Tx-Power=20 dBm 
Retry short long limit:2 RTS thrff Fragment thrff
Power Managementn
[COLOR="#FF0000"]Link Quality=38/70[/COLOR] Signal level=-72 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:45 Invalid misc:52 Missed beacon:0My quote above is simply a repeat of the data you provided in your question. It is not a command or intended to fix your issue.

My router is in a closet and I am sitting about 8 meters away. I get:> 
Link Quality=61/70
I was referring to the antennae on your wireless card; not your router. Please check or, if you do not feel comfortable opening the laptop with a screwdriver, get qualified technical assistance.

[IMG]https://img.wonderhowto.com/img/57/10/63471035847291/0/change-wireless-card-dell-inspiron-e1505-laptop.w1456.jpg[/IMG]

---

### Post by gordon33 on 2019-02-06
Hello chili555

Thank you for making that clear to me.  

I will open up the bottom of my lap top later tonight and report back.

Gordon33

---

### Post by chili555 on 2019-02-06
> **gordon33 said:**
> Hello chili555

Thank you for making that clear to me.  

I will open up the bottom of my lap top later tonight and report back.

Gordon33On many laptops, including mine, there is a little door giving access to the wireless card. Be certain to shut down the computer, detach the power supply and remove the battery before you go further.

---

### Post by jeremy31 on 2019-02-06
Gordon, I would do a search on your HP model and see if there are youtube videos or other tutorials on how to access the wifi card.  On my new hp laptop, 2 screws were hidden by the battery and 4 were hidden my the non slip rubber feet on the bottom, then the bottom cover still needed to be unsnapped from the thing

---

### Post by gordon33 on 2019-02-06
Hello chili555 and jeremy31

The antenna connection looked to be good.  I am guessing the next step is to replace the card?

No access door on my lap top.  I did  use the you tube to find the location (on top, under key board cover) and the method to access the antenna card.

Gordon33

---

### Post by chili555 on 2019-02-06
> The antenna connection looked to be good. 
Was there one or two? Did both look good?

If you are going to replace the card, I wouldn'y suggest a Realtek. I love my Intels, assuming you have no whitelist issue (Google!).

I suspect Jermey may have another suggestion.

---


---
title: "Netgear WG511U Installation Problem"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Lux9698 on 2006-10-20
Hello Folks,

I followed seens Days this forum.
But I can't figuring out, what Im doing wrong. Ubuntu N00b.
[http://ubuntuforums.org/images/smilies/rolleyes.gif](http://ubuntuforums.org/images/smilies/rolleyes.gif)
:rolleyes:

Here is what I have.

Fujitsu Siemens Laptop with a wireless PCMCIA Card (Netgear 511U).
Network Mangaer is uninstalled. for sure.
Ndiswrapper is installed with the right driver for my Wireless Card.
Checked over ifconfig, and It shows me as well my wireless card.
Over iwconfig, still everything looks good.
iwlist scan: Failed to read data: Resource temporarely unavailable.

I checked the whole other configuration what you guys suggested, looks good to me.
Any Ideas out there, It would be highly appreciated.
I wonna go away, so badly, from this Micros....:rolleyes:

---

### Post by wieman01 on 2006-10-20
First thing:
> ndiswrapper -l
Please post the output.

Also post the contents of this one:
> sudo gedit /etc/modprobe.d/ndiswrapper

And that one:
> sudo gedit /etc/network/interfaces

---

### Post by Lux9698 on 2006-10-21
OK,
Here are the outputs

name@name-laptop:~$ ndiswrapper -l
Installed ndis drivers:
netwg51u      driver present, hardware present

sudo gedit /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

sudo gedit /etc/network/interfacesThis 1 is clear, nothing in it


Greetings Lux

---

### Post by wieman01 on 2006-10-21
> **Lux9698 said:**
> 
> sudo gedit /etc/network/interfaces

This 1 is clear, nothing in it
Are you sure? Then we need to set it up for you. No problem.

---

### Post by wieman01 on 2006-10-21
This is what "interfaces" should look like:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
Please copy this & past it into the "interfaces" file & save. Then do another scan:
> iwlist wlan0 scan
What's the output?

That done, please let me know more about your network environment: E.g. DHCP or Static IP, encryption (e.g. WEP), ESSID.

---

### Post by Lux9698 on 2006-10-21
Done.
I copied that into "interfaces"

Result from iwlist wlan0 scan
wlan0 Interface doesn't support scanning

My net wort DHCP

---

### Post by wieman01 on 2006-10-21
Oh, after you have updated the "interfaces" file you need to restart the network or computer... Forgot to mention that. To restart the network, do this:
> sudo /etc/init.d/networking restart
Don't worry if it hangs... Just open another terminal window and scan once again:
> iwlist wlan0 scan

---

### Post by Lux9698 on 2006-10-21
> **wieman01 said:**
> Oh, after you have updated the "interfaces" file you need to restart the network or computer... Forgot to mention that. To restart the network, do this:

Don't worry if it hangs... Just open another terminal window and scan once again:



OK restart the network, but still the same result from the scan

---

### Post by wieman01 on 2006-10-21
Just to reconfirm: Are you sure you have got the right driver? I have seen a similar problem and it involved a driver with a wrong version number. Does the driver you are trying to use now work in Windows? Can you confirm that?

---

### Post by wieman01 on 2006-10-21
Plus... Let's restart the computer to be on the safe side.

---

### Post by wieman01 on 2006-10-21
AND: Please do another "iwconfig" & tell me what it says.

---

### Post by Lux9698 on 2006-10-21
> **wieman01 said:**
> Plus... Let's restart the computer to be on the safe side.

Yes, this driver works under Windows, for sure.
I restart the Laptop right now

Thanks by the way for your pasions

---

### Post by Lux9698 on 2006-10-21
After reboot of the Laptop, same negative result
](*,)

---

### Post by wieman01 on 2006-10-21
OK, I need to get back to you later. Need to do some errands, but check on you later today.

Last 2 questions for now:

1. What does "iwconfig" say?
2. Is the adapter LED lit? Is it active?

---

### Post by Lux9698 on 2006-10-21
> **wieman01 said:**
> OK, I need to get back to you later. Need to do some errands, but check on you later today.

Last 2 questions for now:

1. What does "iwconfig" say?
2. Is the adapter LED lit? Is it active?

to number 1: It gives me tons of technical details from my wireless                         card.

Yep to number 2. The 2 LED flashing normally.

Im so lost, at the moment  :)
waiting then till later

---

### Post by wieman01 on 2006-10-21
When you do "iwconfig" is "wlan0" listed? And what about "ifconfig"? Do those at least list your card & a few other technical details?

_**EDIT:**_
You can also contact me by AIM if you'd like to. May be easier...

---

### Post by Lux9698 on 2006-10-21
OK, I set up an AIM Account,
Lx9698JAK is my Username there.

Hope talk to you soon    :)

---

### Post by wieman01 on 2006-10-21
> **Lux9698 said:**
> OK, I set up an AIM Account,
Lx9698JAK is my Username there.

Hope talk to you soon    :)
Ok, let's do that tomorrow. In the meantime take a look at this thread & see if you have left anything out: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Somehow the card has not been installed correctly.

---

### Post by wieman01 on 2006-10-22
Hello Lux, 

Please try to test your PCMCIA slot. There is a chance that something is wrong there.

---


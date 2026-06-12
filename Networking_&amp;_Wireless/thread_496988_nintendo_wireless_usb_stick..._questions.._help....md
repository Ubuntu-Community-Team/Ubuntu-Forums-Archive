---
title: "nintendo wireless usb stick... questions.. help..."
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by deezay on 2007-07-09
first off, i'm very newbish.. i've looked at every relevant post about this subject and there are still no nailed down instances of this actually working in edgy. most of what i've read all concerns dapper. but here's the plot..

i've got a hardwired connection from my ubuntu box, and a wireless dongle for the wii/ds to connect out on.
 
[http://masscat.afraid.org/ninds/rt2570.php]("http://masscat.afraid.org/ninds/rt2570.php")

supposedly the nintendo wireless adapter can use the above hacked driver for a rt2570. i've installed this to the exact directions. all the commands for looking at the wireless connection show it as active. on 2 instances i've gotten it to light up somehow and my ds can SEE the dongle but it is unable to connect.

i've installed firestarter, and when i go to run it it says the usb dongle is 'busy' and i can't get any further that that with it.

i've also tried virutalbox, but when i put in all of the info for the dongle and go to load xp through virtualbox it just freezes up and i have to reboot the entire computer.

i desperately need help with this. either some way to make ubuntu stop trying to use this thing so i can just use it through virtualbox, OR make ubuntu be able to see and use it. if anyone has any ideas please post... this is my ONLY gripe so far.

here's the contents of the 'iwconfig'

-------------------------------------------------------
```
andrew@andrew-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ninusb0   RT2500USB WLAN  ESSID:"andrew"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-211 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
------------------------------------------------------------------

and under system > admin > networking it is showing the wireless and it is checked and i think it is setup correctly. hope this is enough info. and like i said... please post. thanks.

-andrew

---

### Post by deezay on 2007-07-10
bump... no one knows anything? i actually got it to stop trying to recognize the card in ubuntu... still need some assistance

---

### Post by deezay on 2007-07-11
bump. someone has to know something.

---

### Post by t4thfavor on 2007-07-11
Your trying to use it as an AP? so that the ds can connect to your pc. Is that correct?

If so you have to set the adapter in Master mode instead of Managed mode.

Your driver may not support this mode, but in order to do it issue this command

"sudo iwconfig  ninusb0 mode master"

---

### Post by deezay on 2007-07-12
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ninusb0 ; Invalid argument.



yup, no go on that one. i can't get the lights to even light up on the dongle. anyone want to assist in some ndiswrapper setup?

---


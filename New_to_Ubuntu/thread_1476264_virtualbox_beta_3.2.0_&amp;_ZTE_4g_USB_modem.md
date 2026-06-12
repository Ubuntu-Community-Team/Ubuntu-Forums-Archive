---
title: "virtualbox beta 3.2.0 &amp; ZTE 4g USB modem"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Rowanmf on 2010-05-07
please can someone shed some light for me .

I have done a upgrade to 10.4 lucid , and i wanted to get away from dualboot , XP is used ONLY to use the ZTE tu25 4g usb modem ..so i am trying virtualbox , i had to get beta 3.2.0 as it has USB support ..

Firstly please note ubuntu sees the modem -

rowan-laptop kernel: [25210.452109] usb 2-1: new high speed USB device using ehci_hcd and address 35
May  7 22:51:47 rowan-laptop kernel: [25210.585234] usb 2-1: configuration #1 chosen from 1 choice
May  7 22:51:47 rowan-laptop kernel: [25210.585491] option 2-1:1.0: GSM modem (1-port) converter detected
May  7 22:51:47 rowan-laptop kernel: [25210.585670] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0

but does nothing with it !!

config in virtualbox sees the ZTE modem adds the filter and everything 
but when in the virtualbox and i run the ZTE modem software it says no device , in the top of VB under usb the ZTE modem is seen but it's greyed out .

in groups i am a member of vboxusers ..

I am now stumped ...

i have just got a new HDD so i am gonna do a fresh 10.4 install and get back to virtualbox etc then see from there but PLEASE if you have any input please let me know .

Thanks

---

### Post by madjr on 2010-05-07
am not sure if someone has had a similar problem, but you can also try the virtualbox site and see if you can find any info regarding

also ubuntu guide is constantly updated with new info and problem solving howtos

[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Rowanmf on 2010-05-08
well i have done a fresh 10.4 install , a fresh virtualbox 3.2.0 beta , and it's still doing the same .
I can see any other usb device , no problem , but this frigging modem is driving me around the wall , the virtualbox sees the modem , but it's greyed out .. 
i have now read everything in the ubuntu guide and virtualbox docs , and i have googled and read the virtualbox forum ... i am now well and trully stumped .

Any advice is welcome ..

---

### Post by Rowanmf on 2010-05-10
solved , a guy in the VB forums told me to :
sudo hald 
sudo VirtualBox 
and hey presto it worked , i had been launching VB without the sudo command ..

---


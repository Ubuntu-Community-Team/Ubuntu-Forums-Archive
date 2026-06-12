---
title: "Migrating to 9.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by gogic on 2009-04-23
I curently have ubuntu 8.10 i would like to change to ubuntu 9.04 but i would like to do a clean install. 

1. I will backup most data from home folder to dvd, is there any other important things that i need to backup ( from some system folders ) ?

2. I would like to back up all the libs that ubuntu download with package manager what would be the best way to do this ? Are the old libs useful in new ubuntu ?

3. Before when i used windows i would formate my hard drive ( partition ) with win cd, how can i format with ubuntu or is there way to format all from ubuntu install process cos i wont new ext4 file system ?

4. Is there way to install ubuntu with minimum applications ? Cos i dont need most of defaults like amok, gimp etc

5. Is there a way to install form flash drive ? Cos i seen some other distros have suport for that, is there easy way to boot form usb ( i have p4 and asus mb )

thx

---

### Post by clive littlewood on 2009-04-23
Hi

Just backup your /home directory and you will keep all your settings for things like firefox,contacts etc.

Don't forget to include hidden files in your backup.

Clive

---

### Post by anjilslaire on 2009-04-23
> **gogic said:**
> I curently have ubuntu 8.10 i would like to change to ubuntu 9.04 but i would like to do a clean install. 

1. I will backup most data from home folder to dvd, is there any other important things that i need to backup ( from some system folders ) ?

2. I would like to back up all the libs that ubuntu download with package manager what would be the best way to do this ? Are the old libs useful in new ubuntu ?

3. Before when i used windows i would formate my hard drive ( partition ) with win cd, how can i format with ubuntu or is there way to format all from ubuntu install process cos i wont new ext4 file system ?

4. Is there way to install ubuntu with minimum applications ? Cos i dont need most of defaults like amok, gimp etc

5. Is there a way to install form flash drive ? Cos i seen some other distros have suport for that, is there easy way to boot form usb ( i have p4 and asus mb )

thx

1. /home is usually sufficient
2. No need, and no they're not useful in the new OS
3. Yes, you can format during the new install process. It's recommended.
4. Download and install with the Server ISO, selecting no additional services or options. You will have a bare OS with only a command prompt. Install your GUI and applications as needed.
5. Yes. From your 8.10 installation, use the Create a USB Startup disk application included in Intrepid, point it at your new 9.04 ISO, and your usb stick as the destination, and let it copy. When complete, just boot from the usb stick into the Ubuntu installer.

---


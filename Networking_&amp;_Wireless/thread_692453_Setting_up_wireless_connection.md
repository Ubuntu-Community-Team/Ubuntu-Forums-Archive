---
title: "Setting up wireless connection"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by LindaWu on 2008-02-09
Hi,

I know there are similar threads out there but I couldn't solve my problem reading them. All the HOW TO threads are confusing as well. It's probably due to my novice understanding of Linux. Anyway, on to the problem.

I installed ubuntu 7.1 and was giddy when my laptop loaded ubuntu. Then I thought my wireless would automatically appears but sadly, it didn't.

I read about networt-manager-gnome but besides knowing that it is already installed in my system, I do not know what to do. Also, what is the run command in linux? Just type the program's name?

My laptop is Vostro 1700 with the Broadcom brand and eth0. I do not know what to do next. Please write down a list of programs I have to install and the commands I have to execute.

Thank you so much!
Linda.

---

### Post by Hightide on 2008-02-10
HI Linda

lets see what we can find out.

can you post the output of 

lshw -C network

iwconfig

go to Applications\accessories\terminal

regards

:)

---

### Post by LindaWu on 2008-02-10
> **Hightide said:**
> HI Linda

lets see what we can find out.

can you post the output of  

lshw -C network

iwconfig

go to Applications\accessories\terminal

regards

:)
Hi Hightide! Thanks for your help.

linda@linda-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:bf:54:9f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.4 latency=64 module=b44 multicast=yes

----------------------------------------------

linda@linda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

-----------------------------------------------

---

### Post by Hightide on 2008-02-13
HI lindaWu

Apologies for not replying.

Your  post  '*-network UNCLAIMED' indicates that there is a  driver problem with your Broadcam card.

Try this Broadcom [thread]("http://ubuntuforums.org/showthread.php?t=197102") 

And for general wireless knowledge try Kevdog's [tutorial]("http://ubuntuforums.org/showthread.php?t=571194")

regards

:)

---


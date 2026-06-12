---
title: "Ubuntu 20.04 - Ethernet not being recognized"
date: 2021-07-03
forum: Networking &amp; Wireless
---

### Post by tbyrd3935 on 2021-07-03
Hi all,

I'm very new to linux and am trying to get my ethernet to work, but I'm having trouble. I have Windows 10 as my primary OS and Ubuntu 20.04 dual-booted with it. Ethernet works perfectly fine on Windows, but not Linux for some reason. Also, Wifi works fine on linux.

I have several screenshots attached showing my networks and drivers that I hope will be of some help. Because I'm not too familiar with Linux, I'm not sure what the problem could be here - possibly the driver not being recognized? Also, it appears from the "sudo lshw -C network" command that the network for my ethernet is "unclaimed"...is there a way to claim it?

Let me know if there is any other information I need to provide.

My specs are as follows:

CPU: AMD Ryzen 5 3600X 6-Core Processor
Motherboard: GIGABYTE X570 UD Motherboard
GPU: NVIDIA GeForce GTX 1070
RAM: G.skill TridentZ DDR4 16GB Ram sticks
Hard Drives: Western Digital 500GB SSD, Western Digital 1TB HDD  

Thank you very much!

---

### Post by curts on 2021-07-03
Welcome to newish AMD CPU motherboard chipsets with the Realtek RTL8125 2.5GbE NIC. I have one of these as well:
$ inxi -Nxz
Network:
  Device-1: Realtek RTL8125 2.5GbE vendor: Micro-Star MSI driver: r8125 
  v: 9.005.04-NAPI-RSS port: f000 bus ID: 2a:00.0 

I really wish Ubuntu would add support for this hardware to the 20.04 LTS (hint, hint).

The current solution is to manually download and build the required kernel driver. You have to manually re-install it after each kernel update, so make certain you keep these files accessible on a local drive partition.

See this thread for the install instructions: [https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04](https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04)

---

### Post by tbyrd3935 on 2021-07-03
Okay, great. I'll take a look - thank you!

---

### Post by curts on 2021-09-05
It looks like the 5.11.0-27-generic #29~20.04.1-Ubuntu kernel includes a new r8169 module that supports the Realtek RTL8125 2.5GbE NIC.

---


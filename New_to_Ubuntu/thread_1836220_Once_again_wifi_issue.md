---
title: "Once again wifi issue"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by roya2416 on 2011-08-30
Im currently deployed and just started using ubuntu for my buddies who's computers have crashed and needed erased(and dont want to buy windows all over again). I cant seem to get there wifi connected out here. we use a sat through wireless routers. any way you guys can help us out?

---

### Post by ubudog on 2011-08-30
Hi, what happens when you try to connect?  Do you see the wireless network?

---

### Post by x C0MMAND0 x on 2011-08-30
If possible, wire the laptop directly into a router, so it has a live internet connection, and then go to System > Administration > Additional Drivers or Hardware and see if there is a wi-fi driver that can be installed.  I have had to do that on a number of systems.

---

### Post by roya2416 on 2011-08-30
No we dont have access to the routers. In windows you connect to the router then connect to a seperate broadband connection with username and password

---

### Post by roya2416 on 2011-08-30
I've noticed mac users connect a different way than Win users. It gives them the option to put username and password in. I tried all the different Secuirty but no go. On my windows it says its a WAN miniport (pppoe). dont know if that helps. Man i need to take a networking class.

---

### Post by ubudog on 2011-08-30
Have you installed any drivers via "Addtional Drivers"?

---

### Post by roya2416 on 2011-08-30
Nope no additional drivers

---

### Post by ubudog on 2011-08-30
Can you see any drivers if you open "Additional Drivers"?

---

### Post by roya2416 on 2011-08-30
that is a negitive just a message with no propietary drivers are in use of this system

---

### Post by ubudog on 2011-08-30
Hmm, can you see the wireless network if you click on the signal bars at the top of the screen?

---

### Post by roya2416 on 2011-08-30
i guess that means i would have to add the driver for the wifi is that correct?

---

### Post by roya2416 on 2011-08-30
yes says wireless device not managed

---

### Post by ubudog on 2011-08-30
You can probably download the drivers from the manufacturer's website.  Could you please copy and paste this into a terminal, and post the output?

```
lspci
```

That will tell us what wireless card you have.

---

### Post by roya2416 on 2011-08-30
Newtork controller: Intel Corportaion centrino advanced -N + Wimax 6250 (rev 5f)
Ethernet controller: Realtek Semiconductor Co. Ltd RTL8111/8168B PCI express gigabit ethernet controller (rev 6)

---

### Post by alphacrucis2 on 2011-08-30
> **roya2416 said:**
> Newtork controller: Intel Corportaion centrino advanced -N + Wimax 6250 (rev 5f)
Ethernet controller: Realtek Semiconductor Co. Ltd RTL8111/8168B PCI express gigabit ethernet controller (rev 6)

What does 

```
ifconfig
```


say?

---

### Post by roya2416 on 2011-08-30
just gives info on each settting as far as packets and errors droppeds and overruns

---

### Post by alphacrucis2 on 2011-08-30
> **roya2416 said:**
> just gives info on each settting as far as packets and errors droppeds and overruns

Yeah but does wlan0 show up in the list of interfaces. Typically you should have three interfaces listed. lo for loopback, eth0 for the first ethernet port, wlan0 for the first wireless port.

Another useful command is:

```
sudo lshw -C network
```

That will show all the network devices and if they are claimed by any driver.

---

### Post by roya2416 on 2011-08-30
Just a quick overview. Im curretly deployed and a couple of my soldiers computers have crashed (or broken harddrives) I installed ubuntu 11.04 on mine and two ohters but need to get updated for plug in but can not. I am running dual OS with Windows. I can connect with windows but unable to connect with Ubuntu. Please help. thanks

---

### Post by roya2416 on 2011-08-30
yes it has showed up this there something speical you are looking for

---

### Post by alphacrucis2 on 2011-08-30
> **roya2416 said:**
> yes it has showed up this there something speical you are looking for


Can you list here the output of the wlan0 section of the ifconfig output and also the information about the wireless card from

 ```
sudo lshw -C network
```

---

### Post by lkraemer on 2011-08-30
Will you open a Terminal Window (Console) and post the output of:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modules
iwconfig

```


lk

---

### Post by roya2416 on 2011-08-31
haveing to use a different computer to use forum cant copy and paste. Is there a speical line you are looking for i can type for you.

---

### Post by roya2416 on 2011-08-31
I have been looking at my replys and noticed i've been very simple in my answer.
 
Im deployed. We use a commerical based internet through the aafes system. You pay for your package and they give you a username and password. Wireless routers are set up all over base. Now with Windows you have to use a broadband connection so you can enter the username/Password. Apple gives you an option to enter the info. My computer has ubuntu so i can learn how to use it and help out my soldiers with computer issues where they need new OS. Im new at Ubuntu but need to LEARN how to set up plug ins and connect drivers. I know each computer is different. Im trying to understand the difference the between window/apple and ubuntu conections. i see the network appliction but dont know why it wont let me choose to enter a login info. Thanks

---

### Post by lkraemer on 2011-09-02
If you must use a US Government PIV card, you may want to try:

[http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm)

[http://distrowatch.com/table.php?distribution=lps](http://distrowatch.com/table.php?distribution=lps)


From a Terminal use:
```

lshw -C network > mylog.txt
lsmod >> mylog.txt
ndiswrapper -l >> mylog.txt
cat /etc/modules >> mylog.txt
iwconfig >> mylog.txt

```
then post mylog.txt.............We need to see the information.


lk

---


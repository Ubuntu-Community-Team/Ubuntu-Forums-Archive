---
title: "network connection problems. Ubuntu 18.04"
date: 2019-09-12
forum: Networking &amp; Wireless
---

### Post by jmgmayo on 2019-09-12
When I am downloading files such as ubuntu distributions I drop the network connection. I lose all the LAN settings and I have to restart the computer.


I have a newly installed 18.04 distribution (I thought it was a version issue).


Any idea how to analyze what can happen? The problem does not appear from a Windows computer connected to the same lan.


regards

---

### Post by mörgæs on 2019-09-13
If you download using **wget** from the command line do you get any error messages?

---

### Post by jmgmayo on 2019-09-14
Hi, using wget it is the same behaviour

***wget [http://releases.ubuntu.com/19.04/ubuntu-19.04-desktop-amd64.iso](http://releases.ubuntu.com/19.04/ubuntu-19.04-desktop-amd64.iso)***

Start the download and after maybe 2 min the velocity decrease and lost the connectivity. I have another pc with windows running in the same LAN and this pc works fine. I have install 16.04 LTS and the problem it is the same. 

Can i check if there is any problem with the network card?

Thanks a lot for your help

---

### Post by mörgæs on 2019-09-15
I don't know much about network problems but other people here do.
They would probably prefer if you began with the [guide for troubleshooting]("https://ubuntuforums.org/showthread.php?t=370108").

---

### Post by jmgmayo on 2019-09-15
Thanks a lot for the information. The information is about Wireless connection. My problem is in PC (no laptop) and using LAN (wired conecction) conection. Is there any information similar to indetify problems with wired conection?

Regards

---

### Post by mörgæs on 2019-09-16
I am aware that the script is mainly for solving wireless problems but since we don't have any data at all we can only hope that it might show something of interest.

---

### Post by SeijiSensei on 2019-09-16
You're not trying to have both a wired and a wireless connection from the same machine, are you?  That can cause problems with packet routing.  Just use the wired connection and disable the wireless.

---

### Post by jmgmayo on 2019-09-19
Hi, it is a desktop machine. There is no wireless connection. Only wired card. 

There is any script to monitor wired activity?

Regards.

---

### Post by #&amp;thj^% on 2019-09-19
Sure all sorts: [https://askubuntu.com/questions/257263/how-to-display-network-traffic-in-the-terminal](https://askubuntu.com/questions/257263/how-to-display-network-traffic-in-the-terminal)

---

### Post by jmgmayo on 2019-09-20
Thanks a lot for your response.  I have installed bmon y tcptrack. I can not find the correct ethernet interface.  When i launch bmon process only display interface 

enp0s5 

This interface increase the velocity up 11Mb/s (when i start to download the ubuntu image) and after a few minutes decrease to 0 and i can not  connect to internet. I need to restart the computer to access to internet. Any idea how t identify the problem?

Regards.

---

### Post by jmgmayo on 2019-11-04
i just solved the error. The pci netword card doesn't work correctly.  I installed other gigabit PCi and all is ok.

Thanks a lot.

---

### Post by mörgæs on 2019-11-04
Good that you got it solved. Please mark the thread solved.

---

### Post by johnarnold on 2019-11-05
> **jmgmayo said:**
> When I am downloading files such as ubuntu distributions I drop the network connection. I lose all the LAN settings and I have to restart the computer.


I have a newly installed 18.04 distribution (I thought it was a version issue).


Any idea how to analyze what can happen? The problem does not appear from a Windows computer connected to the same lan.


regards

What exactly happens when you 'lose all the LAN settings'? Can you ping your default gateway? Is the interface still up (perform an ifconfig on the interface)?

---

### Post by johnarnold on 2019-11-05
Ah just saw your last post. Glad that you got it resolved.

---


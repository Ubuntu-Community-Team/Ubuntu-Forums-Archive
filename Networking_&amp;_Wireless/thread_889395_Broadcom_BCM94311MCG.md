---
title: "Broadcom BCM94311MCG"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by MarlonDean on 2008-08-14
Hey everyone,

I have been on a mission for the last couple of days to get my broadcom wifi working with kismet. I am sure that it is possible, because i read that there are drivers available for bcm43xx that do support monitoring.

anyway, I used lspci to get the exact version of my card and it says i have a  Broadcom Corporation BCM94311MCG. Is this the same as a bcm43xx? Does anyone have a suggestion on what to do to get kismet working on  Broadcom Corporation BCM94311MCG? I am at my wits end!

Thank you in advance!

---

### Post by souljahh2050 on 2008-08-14
I am having the same problem. And have spent about 8 hours pulling my hair out trying to get this to work. Please keep in mind that I am new to linux.

I followed the instructions here [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
But when I get to the step 

sudo vim /etc/modules
add this line &#8220;ndiswrapper&#8221; (without &#8220;&#8221;)

I am unable to save the file.

Not sure if that step is needed but after following the rest of the instructions I am still unable to connect to the internet via wireless.

Also once I am finally successfull with this will I be able to view wireless networks like in windows.

Thx,

---

### Post by rizitis on 2008-08-14
first try this [http://ubuntuforums.org/showpost.php?p=5524663&postcount=1](http://ubuntuforums.org/showpost.php?p=5524663&postcount=1)
to see if its working...

or try this [http://zugaldia.wordpress.com/2008/04/30/setting-up-the-broadcom-bcm94311mcg-in-ubuntu-804/](http://zugaldia.wordpress.com/2008/04/30/setting-up-the-broadcom-bcm94311mcg-in-ubuntu-804/)

---

### Post by souljahh2050 on 2008-08-14
I still cannot connect to my router. How do i save the file I mentioned earlier?

---

### Post by rizitis on 2008-08-14
open the terminal and give
```
sudo apt-get remove ndiswrapper
```
then open synaptic and apply these 
```
ndisgtk 0.83-1
ndiswrapper-common 1.50
ndiswrapper-utils-1.9
b43-fwcutter 1:011-1 
```

then command at terminal
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

then take the driver from [here]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html")

now you have to unzip the file
so do right click to the file and chose "unzip here" 
you will see a file "WLANBroadcom"
in there is a file "bcmwl5.inf"
that is what you need , so open ndiswrapper and apply it.
then command 
```
ndiswrapper -l
```
if the answer is something like this
```
Installed ndis drivers:
{name of driver}* driver present, hardware present
```

command
 ```
sudo depmod -a
sudo modprobe ndiswrapper
```
```
gksu gedit /etc/modules
```

add at the end of the text the word
```
ndiswrapper
```
save and exit.

Then follow these steps:
Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked.
1.Click the Network Manager icon (computers icon in the top right corner of system tray), your network ESSID should be shown in the drop-down list. Select your network by clicking on it.
2.If the Network requires any further configuration (eg WEP key), a dialog should appear, select the correct settings and paste in your key.
Now you reboot and you are ready...
good luck

---

### Post by MarlonDean on 2008-08-14
Ok, the i would like to point out that this thread is about broadcom and kismet. kismet will not work if you use ndiswrapper. Please advise

---

### Post by bdfoster on 2008-08-14
> **MarlonDean said:**
> Ok, the i would like to point out that this thread is about broadcom and kismet. kismet will not work if you use ndiswrapper. Please advise

Using ndiswrapper worked for my broadcom wireless. The instructions above are similar to the ones I used to get mine working. Do you have an HP laptop? If so, this will probably work. I don't know about the kismet issue, but all you need is ndiswrapper.

---

### Post by souljahh2050 on 2008-08-14
> **rizitis said:**
> open the terminal and give
```
sudo apt-get remove ndiswrapper
```
then open synaptic and apply these 
```
ndisgtk 0.83-1
ndiswrapper-common 1.50
ndiswrapper-utils-1.9
b43-fwcutter 1:011-1 
```

then command at terminal
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

then take the driver from [here]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html")

now you have to unzip the file
so do right click to the file and chose "unzip here" 
you will see a file "WLANBroadcom"
in there is a file "bcmwl5.inf"
that is what you need , so open ndiswrapper and apply it.
then command 
```
ndiswrapper -l
```
if the answer is something like this
```
Installed ndis drivers:
{name of driver}* driver present, hardware present
```

command
 ```
sudo depmod -a
sudo modprobe ndiswrapper
```
```
gksu gedit /etc/modules
```

add at the end of the text the word
```
ndiswrapper
```
save and exit.

Then follow these steps:
Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked.
1.Click the Network Manager icon (computers icon in the top right corner of system tray), your network ESSID should be shown in the drop-down list. Select your network by clicking on it.
2.If the Network requires any further configuration (eg WEP key), a dialog should appear, select the correct settings and paste in your key.
Now you reboot and you are ready...
good luck

Thank you your instructions worked perfectly for my Compaq Presario F555US

---

### Post by rizitis on 2008-08-14
:)

I just want to say that the first command 
```
sudo apt-get remove ndiswrapper
```
will not be useful for other people,  they have to ignore this command and start from the second. 
you needed this command because probably  you had the old version of ndiswrapper, thats because you followed  this [link]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/") which is very ,very usefully but old.

---


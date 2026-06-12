---
title: "Getting Intel 5100 wireless to work with ndiswrapper"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Valkyria on 2009-02-28
I just installed Ubuntu 8.10 yesterday on my Acer Aspire 6930G and the wireless isnt working.  I did a bit of reading from some links that marco123 showed me but still didnt quite understand how to use ndiswrapper.  I perfer to use wireless because i use the ethernet cable i have currently hooked in my lappy for internet to my Xbox360 and PS3 so i can play online

---

### Post by shane8002 on 2009-02-28
For ndiswrapper basically just download the program then you gotta get the .inf driver for the wireless card.

---

### Post by Valkyria on 2009-02-28
> **shane8002 said:**
> For ndiswrapper basically just download the program then you gotta get the .inf driver for the wireless card.

Ok i got the program downloaded and i have the driver downloaded. I remember in a link that marco123 showed me it talked about a driver folder being in the home directory, and when i looked there i didnt see a driver folder so i made one and just put the .zip file in the folder.  Is that wrong? Do i just extract the files into the drivers folder or do i just put the .inf file in it.

---

### Post by abyssius on 2009-02-28
> **Valkyria said:**
> Ok i got the program downloaded and i have the driver downloaded. I remember in a link that marco123 showed me it talked about a driver folder being in the home directory, and when i looked there i didnt see a driver folder so i made one and just put the .zip file in the folder.  Is that wrong? Do i just extract the files into the drivers folder or do i just put the .inf file in it.

You'll need to extract the .inf file _AND_ the .sys file, which is the actual driver. The .inf file alone won't do it. 

It doesn't really matter where you put these files as long as you know how to direct ndiswrapper to them. Ndiswrapper will make copies and place them in its own directory. 

BTW, are you intending to use ndiswrapper via the command line interface, or use the graphic [Windows Wireless Drivers] menu?

---

### Post by Valkyria on 2009-02-28
> **abyssius said:**
> You'll need to extract the .inf file _AND_ the .sys file, which is the actual driver. The .inf file alone won't do it. 

It doesn't really matter where you put these files as long as you know how to direct ndiswrapper to them. Ndiswrapper will make copies and place them in its own directory. 

BTW, are you intending to use ndiswrapper via the command line interface, or use the graphic [Windows Wireless Drivers] menu?

Im using the Windows Wireless Drivers interface

Edit: Actually both kinda i guess

---

### Post by abyssius on 2009-02-28
> **Valkyria said:**
> Im using the Windows Wireless Drivers interface

Edit: Actually both kinda i guess

Trust me - use the Windows Wireless Drivers menu first. After you've successfully installed the drivers, click on [Configure Network]. If this contrl works you're all set. If you get an error message, like "Can't find a network configuration tool", let me know.

---

### Post by Valkyria on 2009-02-28
> **abyssius said:**
> Trust me - use the Windows Wireless Drivers menu first. After you've successfully installed the drivers, click on [Configure Network]. If this contrl works you're all set. If you get an error message, like "Can't find a network configuration tool", let me know.

I got the error:(

---

### Post by Valkyria on 2009-02-28
what should i do now

---

### Post by abyssius on 2009-02-28
> **Valkyria said:**
> what should i do now
 Some terminal commands will give hints as to how to proceed. You will need to know the IP address, ESSID and operating channel of your router. You'll also have to know how your wireless security is set up, if you're using any. The following instructions assume that you're not using wireless security right now.

Open a terminal and type:
```
sudo -s
```
Enter your password to become root. Next:
```
iwconfig
```
This will list your available interfaces. If you have wlan0 listed then you are good to go (if you don't then please post the output of the iwconfig command).

If wlan0 is listed. then:
```
gedit /etc/network/interfaces
```.

Your interfcaes file should look like this:
```

auto lo
iface lo inet loopback

```
Add the following lines to the interfaces file (this assumes your not using wireless security):
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid **type the name of your router's essid here**
wireless-channel **add your channel here**
wireless-mode managed
gateway **type the IP address of your router here**

auto wlan0

```
Here's an actual file to show you what it should look like:
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid linksys
wireless-channel 6
wireless-mode managed
gateway 192.168.1.1

auto wlan0

```

If you've gotten this far, then save the file.
Next, enter the code:
```

/etc/init.d/networking restart

```
Then check to see if you're online. Remember to close the root terminal as soon as you're done with it.

---

### Post by Valkyria on 2009-02-28
> **abyssius said:**
> Some terminal commands will give hints as to how to proceed. You will need to know the IP address, ESSID and operating channel of your router. You'll also have to know how your wireless security is set up, if you're using any. The following instructions assume that you're not using wireless security right now.

Open a terminal and type:
```
sudo -s
```
Enter your password to become root. Next:
```
iwconfig
```
This will list your available interfaces. If you have wlan0 listed then you are good to go (if you don't then please post the output of the iwconfig command).

If wlan0 is listed. then:
```
gedit /etc/network/interfaces
```.

Your interfcaes file should look like this:
```

auto lo
iface lo inet loopback

```
Add the following lines to the interfaces file (this assumes your not using wireless security):
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid **type the name of your router's essid here**
wireless-channel **add your channel here**
wireless-mode managed
gateway **type the IP address of your router here**

auto wlan0

```
Here's an actual file to show you what it should look like:
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid linksys
wireless-channel 6
wireless-mode managed
gateway 192.168.1.1

auto wlan0

```

If you've gotten this far, then save the file.
Next, enter the code:
```

/etc/init.d/networking restart

```
Then check to see if you're online. Remember to close the root terminal as soon as you're done with it.

I do have security, i believe 128 bit WEP, and would that be why the interfaces window that i opened with gedit didnt list anything

---

### Post by abyssius on 2009-02-28
The interfaces file must have something in it. You probably didn't open it. Gedit will create a new file called interfaces if it doesn't find an existing one. Try these commands:

```
cd /etc/network
```
Enter.
```
cat interfaces
```
Enter.

This will display the existing interfaces file. If it responds that it couldn't find the file, then interfaces is indeed missing. You should still create an interfaces file anyway. Since you should be in the /etc/network directory, if you know all the parameters and you want to create an new interfaces file, you could use gedit like this:
```
gedit interfaces
```

As for the WEP, this wouldn't affect anything thus far, you'll have to add some additional steps to enter your key.



The

---

### Post by Valkyria on 2009-02-28
> **abyssius said:**
> Some terminal commands will give hints as to how to proceed. You will need to know the IP address, ESSID and operating channel of your router. You'll also have to know how your wireless security is set up, if you're using any. The following instructions assume that you're not using wireless security right now.

Open a terminal and type:
```
sudo -s
```
Enter your password to become root. Next:
```
iwconfig
```
This will list your available interfaces. If you have wlan0 listed then you are good to go (if you don't then please post the output of the iwconfig command).

If wlan0 is listed. then:
```
gedit /etc/network/interfaces
```.

Your interfcaes file should look like this:
```

auto lo
iface lo inet loopback

```
Add the following lines to the interfaces file (this assumes your not using wireless security):
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid **type the name of your router's essid here**
wireless-channel **add your channel here**
wireless-mode managed
gateway **type the IP address of your router here**

auto wlan0

```
Here's an actual file to show you what it should look like:
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid linksys
wireless-channel 6
wireless-mode managed
gateway 192.168.1.1

auto wlan0

```

If you've gotten this far, then save the file.
Next, enter the code:
```

/etc/init.d/networking restart

```
Then check to see if you're online. Remember to close the root terminal as soon as you're done with it.

After doing the two commands i got this
```
eric@eric-linuxlappy:~$ sudo -s
[sudo] password for eric: 
root@eric-linuxlappy:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
Is this correct?

---

### Post by abyssius on 2009-02-28
> **Valkyria said:**
> After doing the two commands i got this
```
eric@eric-linuxlappy:~$ sudo -s
[sudo] password for eric: 
root@eric-linuxlappy:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
Is this correct?

The wlan0 output is missing the ESSID parameter. This is the name you gave your router. Because of this you are not associated with your access point (router). It apppears your adapter is recognized and working. The next step is to get the adapter to connect to your router. The two key parameters need for this is your (a) router's ESSID and (b) the channel (frequency) that the router is operating on. Right now, your wlan0 is set to 2.412 GHz. This corresponds to channel 1. The most common channel for wireless routers is channel 6 (or 2.437 Ghz). I'd check this parameter out. These parameters are set in the interfaces file. You can also set these parameters using the iwconfig command, like this:

```
iwconfig wlan0 essid "***your_router_name***"
```
```
iwconfig wlan0 channel *n*
```
Where, *n* is the channel number your router is set to.

Then type ```
iwconfig wlan0
``` to see if it accepted the parameters.

---


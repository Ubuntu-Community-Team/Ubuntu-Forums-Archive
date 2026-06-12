---
title: "wireles USB and root permissions"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by drumstik102 on 2009-09-24
ive been following some directions from another thread on how to install drivers for a wireless usb stick. i have a belkin F5D8055 v2.

one of the instructions was to extract the zipped driver folders to /usr/src but i get a message saying i don't have the right permissions to extract to that folder. i cant get past that step

if anyone can take the time and explain step by step how to get my usb stick working that would be greatly appreciated. im not quite sure how to handle the "sudo make" and "sudo make install" step im reading everywhere.

i am days old in the Linux OS so please excuse my lack of knowledge.

---

### Post by nothingspecial on 2009-09-24
I think I`ve found the instructions you`re following. It doesn`t actually matter where you extract the folder to.

Just extract them to your Desktop or Home directory.

Anything else you don`t understand, post back.

---

### Post by drumstik102 on 2009-09-24
oh ok cool. yeah i ended up just extracting it to my desktop. ive done every step until the 'sudo make' and 'sudo make install' part. how exactly am i supposed  to carry out this step?

---

### Post by nothingspecial on 2009-09-24
You need to change your working directory to the extracted folder.
```

cd Desktop/name_of_extracted_file
```
```
make
```
```
sudo make install
```

---

### Post by drumstik102 on 2009-09-24
Ok looks like I did that part right. Thanks. But now after I enter th command 'sudo modprobe rt2870sta' nothing happens. . . 
I thinks its supposed to start scanning for networks?

---

### Post by nothingspecial on 2009-09-24
> **drumstik102 said:**
> Ok looks like I did that part right. Thanks. But now after I enter th command 'sudo modprobe rt2870sta' nothing happens. . . 
I thinks its supposed to start scanning for networks?

That command loads the module (driver) into the kernel.

You have to use network manager (or whatever you are using) to do the scanning.

---

### Post by drumstik102 on 2009-09-24
Well I must be doing something wrong then. I can't get my usb to work. Can't find the network manager to do the scanning. 
Thanks for your help

---

### Post by nothingspecial on 2009-09-24
```
3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */
```

How did you go about doing this bit.

---

### Post by drumstik102 on 2009-09-24
Actually I wasn't able to delete the already installed rt2870sta because I would get a message I don't have the right permission to do so.
The next steps after that I used gedit to change and input values.

---

### Post by nothingspecial on 2009-09-24
To be honest, it`s not a good idea to delete those sort of things anyway. Move (rename) it instead.

```
sudo mv /lib/modules/2.6.31-9-generic/kernel/drivers/staging/RT2870 ~/RT2870
```

Then try again.

This assumes your kernel is 2.6.31-9-generic.

Type ```
uname -a
``` to find out and modify that command if necessary.

This will put that driver in your home folder, of course, you can put it where you like.

---

### Post by nothingspecial on 2009-09-24
You may then have to cd into that extracted file again and issue

```
make clean
make
sudo make install
```

if it doesn`t work

---

### Post by drumstik102 on 2009-09-25
ok im getting further each time. . .
so now it appears the driver is installed and it shows up in iwconfig as ra0 but it looked like the device still wasnt active yet so i tried
```
ifconfig ra0 up
```then the little blue light on my stick started blinking.
ive gotten this far but still no internet connectivity.

---

### Post by nothingspecial on 2009-09-25
Does ```
sudo iwlist ra0 scan
``` show your network

---

### Post by drumstik102 on 2009-09-25
it said > ra0         no scan results

---

### Post by nothingspecial on 2009-09-25
What does ```
iwconfig
``` say?

---

### Post by drumstik102 on 2009-09-25
i got```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by nothingspecial on 2009-09-25
Try

```
sudo iwconfig ra0 essid *[COLOR="Red"]your_network_name[/COLOR]*
``` ```
sudo iwconfig ra0 key *[COLOR="Red"]your_key[/COLOR]*
```

then ```
sudo dhclient
```

---

### Post by drumstik102 on 2009-09-25
after entering the first command i got```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "*******".

```substitute ******* with my key

---

### Post by nothingspecial on 2009-09-25
Try the commands seperated.

I`ve edited my post above.

---

### Post by drumstik102 on 2009-09-25
i got the same error message after the command with my key

---

### Post by nothingspecial on 2009-09-25
Before we go investigating your wireless card further - after all I have no experience with this card, I was just helping you follow instructions ;) - lets just start from the beginning one more time.
```

sudo ifconfig ra0 down
```
```

sudo modprobe -r rt2870sta
```
```

sudo modprobe rt2870sta
```

```
sudo ifconfig ra0 up
```
```

sudo iwconfig ra0 essid *[COLOR="Red"]network_name[/COLOR]*
```
```

sudo iwconfig ra0 key *[COLOR="Red"]key_here[/COLOR]*
```
```

sudo dhclient
```

---

### Post by drumstik102 on 2009-09-25
Error message yet again after the key command.

---

### Post by nothingspecial on 2009-09-25
b*****r

Well, having removed a faulty module, compiled a new one, and inserted it into the kernel we`re still no further.

I`ll have to have a look.

---

### Post by drumstik102 on 2009-09-25
Well thank you for your help, you must be as frustrated as I'm am.  Its a shame we got this far and yet no solution.

---

### Post by nothingspecial on 2009-09-25
Right, apparently some people have had success with ndiswrapper.

```
sudo apt-get install ndiswrapper-gtk
```

Insert the install disk that came with your wireless thingy and find the .inf file. It may be in installfiles/winxp.

Copy it to your Desktop.
```

sudo ndiswrapper -i ~/Desktop/drivername.inf
```

check it woked   ```
ndiswrapper -l
```

```
sudo ifconfig ra0 down
```
```

sudo modprobe -r rt2870sta
```

```
sudo /etc/init.d/networking restart
```

```

sudo depmod -a
```

```
sudo modprobe ndiswrapper
```

---

### Post by nothingspecial on 2009-09-25
Then you`ll have to do all that ifconfig/iwconfig stuff again, starting with ```
sudo ifconfig *[COLOR="Red"]interface [/COLOR]*up
```

However you`ll have to run iwconfig again before you do to check your wireless interface, it may not be ra0, it`s probably wlan0.

If that`s the case substitute ra0 for whatever it is in all those commands

---

### Post by drumstik102 on 2009-09-25
ok before i try all that let me explain what exactly is going on now.

i rebooted and ran```
sudo modprobe rt2870sta
sudo ifconfig ra0 up
```the stick lit up, and then i right clicked on the network bars on the top right of my screen and a new line was there 'wireless networks', which i hadnt seen before.

to me it looks like the stick is working but the only problem is locating my network. . .or should i try the procedure above?

---

### Post by nothingspecial on 2009-09-25
Perhaps if I explained things instead of just spewing line of code at you .....

ndiswrapper is a utility that tries to get windows wireless drivers working with linux. It is treated as a driver in itself.

modprobe loads a module (driver) into the kernel

modprobe -r removes one

So you can ```
modprobe -r rt2870sta && modprobe ndiswrapper
``` or ```
modprobe -r ndiswrapper && modprobe rt2870sta

```

All day long.

It will not effect what we have already done.

Having said that, it is worth using google to try and get rt2870sta to see your network.

---

### Post by drumstik102 on 2009-09-27
i have exhausted my options and cant get anything to work. ndiswrapper didnt work. the furthest i got was getting the stick to light up by installing the ralink driver but it cant find my network.
looks like im gunna have to go back to windows for internet.

thank you so much for all your help.

---


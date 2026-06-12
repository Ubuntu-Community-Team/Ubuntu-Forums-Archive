---
title: "Freshly installed Ubuntu (dualboot with win7), wifi is not working, acer laptop"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by j.winkler.15 on 2015-09-27
**&#8203;**Hey there,
I would be very, very happy if someone knew the solution to my problem.
I just installed Ubuntu on my laptop. My laptop is Acer Aspire 5755G. Additionally, I have Windows 7 running on this laptop, where my wifi works perfectly.

I think there is something wrong with my wifi. When I type "sudo rfkill list" in the terminal, the answer is something saying that the "acer-thing" is neither hard blocked nor soft blocked.
Networking is also enabled.

I googled this problem with my mobile phone, and some of the users said that you had to set acer_wmi on the blacklist. However, in these cases, the person with the problem had no acer laptop. I have an acer laptop, so I did not try this. 

When I tried to use other strings in terminal, an error message told me that device "wlan0" could not be found. 

Could you please tell me what else I could try to make it work and, if you type in something to write in terminal, please explain what this does? I would like to really learn what the issue was.

Thank you very much!

---

### Post by Bucky Ball on 2015-09-27
Welcome. Please be very careful of using 'other strings' and any other commands in a terminal if you have no idea what they are doing. You could be further confusing the situation mildly or severely breaking the system. Best to ask if you are unsure. :)

First off, open a terminal and copy this in:

```
sudo lshw -C network
```

Post the output back here please between code tags (see last link in my signature).

---

### Post by j.winkler.15 on 2015-09-27
thank you! yes, I will do so. therefore, I thought it would be useful to ask someone here, who really knows about the terminal.
I am not able to copy the code, because I have really no network working on linux, so I cannot connect to the internet. thus, I restart the laptop new everytime to answer here. I can only make screenshots of the outcomes of the terminal, such as here:


. [ATTACH=CONFIG]264691[/ATTACH]

---

### Post by Bucky Ball on 2015-09-27
You can't get this machine online with a cable? In any case, you have the Broadcom BCM43227 wireless chip in there and it is detected fine and everything seems to be happening but unsure about the driver. It looks like it is supposed to be recognised 'out of the box'. A cable would be handy before going much further as you may need to install things to get this up.

If you can get online, try these three commands in a terminal, one after the other and hitting enter after each:
```

sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by j.winkler.15 on 2015-09-27
Unfortunatley, it is not possible for me to go online with a cable, because I have none.
Is there any other way to fix this problem? 
I am not at my home country, because I am spending my semester abroad right now. Therefore, I have no possibilty to get a cable connection soon. However, I will need Ubuntu to work properly until Tuesday.

---

### Post by jeremy31 on 2015-09-27
Anything in dmesg about firmware ```
dmesg | grep -i firmware
``` and what kernel ```
uname -a
```

---

### Post by j.winkler.15 on 2015-09-27
[ATTACH=CONFIG]264698[/ATTACH]


as a result, terminal printed this out.

---

### Post by jeremy31 on 2015-09-27
If you have a thumb drive download [https://www.dropbox.com/s/88moe426k6app3u/ucode30_mimo.fw?dl=0](https://www.dropbox.com/s/88moe426k6app3u/ucode30_mimo.fw?dl=0) and transfer it to your Ubuntu in the home folder
Then ```
sudo mkdir /lib/firmware/b43
sudo cp ucode30_mimo.fw /lib/firmware/b43/ucode30_mimo.fw
```

Reboot and see if it works or if there are other error reported from ```
dmesg | grep firmware
```

---

### Post by j.winkler.15 on 2015-09-27
i copied the file as you said using cp, and then used the second part. the answer was: 


[ATTACH=CONFIG]264699[/ATTACH]

---

### Post by jeremy31 on 2015-09-27
So what is the result of ```
ls /lib/firmware/b43/
```

It is hard to tell from the picture, but does it say ucode30_mimo.fw in the error message?

---

### Post by j.winkler.15 on 2015-09-27
if I type in cd and the path you just typed in where the file had to be copied, and then type in ls, it just shows me the file that was copied there, so it is definitely there. also the name is written correctly, i checked it two times

---

### Post by j.winkler.15 on 2015-09-27
i think my answer was not shown here.
the result of changing the directory and showing the files was that the file which i had to copy the step before was there. it was also written correctly there and in the terminal, i checked it twice.

---

### Post by jeremy31 on 2015-09-28
[http://www.lwfinger.com/b43-firmware/no_net_install_bcm43xx_firmware.tar.bz2](http://www.lwfinger.com/b43-firmware/no_net_install_bcm43xx_firmware.tar.bz2) and put it on the Ubuntu machine, after extracting view the readme file for instructions

---

### Post by j.winkler.15 on 2015-09-28
sorry, but I do not know what you mean by putting it on the machine. just copying it into the home folder? or where does it have to be? :D

---

### Post by jeremy31 on 2015-09-28
You can copy it into the home folder, then right click on the file and choose extract here

Or use terminal and
```
[COLOR=#333333][FONT=UbuntuMono]tar xfvj broadcom-wl-5.100.138.tar.bz2
[/FONT][/COLOR]sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
```

---

### Post by j.winkler.15 on 2015-09-28
i have manually extracted the files and put the command described in the readme into the terminal. 
then the installation failed.
i do not know why nothing works.. what do i have to do now?

---

### Post by nknwn on 2015-09-28
Pardon me for jumping in but while you wait try this in the terminal:
sudo nmcli dev wifi connect **yournetworkssid** password [B]yourwifipassword


[/B]**DESCRIPTION**
       **nmcli** is a command-line tool for controlling NetworkManager

---

### Post by jeremy31 on 2015-09-28
My commands were wrong for that download, change directory in terminal if you extracted the files to something else than home then
```
cd bcm43xx_firmware
sudo sudo ./install_bcm43xx_firmware_no_net
```

And see if it works after a reboot

I would also check ```
sl -l /lib/firmware/ | grep b43
```

To see if permissions are correct, it should be
```
drwxr-xr-x  2 root root    4096 Sep 28 05:19 b43
```

If it doesn't work, you will have to try to install the Broadcom STA driver using these instructions
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

The open source drivers bcma and b43 are supposed to work with your card in kernels 3.17 and up with the firmware but the Broadcom STA should work if you can get it installed with those directions

---


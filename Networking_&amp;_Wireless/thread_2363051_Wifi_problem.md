---
title: "Wifi problem"
date: 2017-06-05
forum: Networking &amp; Wireless
---

### Post by babak67 on 2017-06-05
Hi everyone

I have just installed Unbuntu and the wifi icon says i'm connected to my home wifi network.
iwconfig shows my wlo1 with essid= my home wifi, ifconfig shows _wlo1_ connected with an ip associated and everything seems to be ok, but I can ping no other ip. and Firefox does not work.

What happened to my good old wlan0 ? Where does this wlo1 come from ? and why the hell it is not working ?

I appreciate any help.

Thanks

---

### Post by wildmanne39 on 2017-06-05
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by babak67 on 2017-06-05
here you are
[https://pastebin.com/6deVVuXD](https://pastebin.com/6deVVuXD)

Thanks in advance

---

### Post by wildmanne39 on 2017-06-05
There are several things that look strange but let's start with you editing a file that needs editing for several wifi devices to work in 17.04.

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

---

### Post by babak67 on 2017-06-06
Hi

Still the same.

---

### Post by Hadaka on 2017-06-06
Hi, please open a terminal..ctrl/alt/t..then Copy and paste
one line at a time..
```
sudo iw reg set FR
sudo sed -i 's/=.*/=FR/' /etc/default/crda
echo "options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```
boot and test wireless.
*If you still cannot connect,please post a new wireless diagnostic report.
Thanks.

---

### Post by babak67 on 2017-06-07
It is not working Hadaka

[http://paste.ubuntu.com/24800085/](http://paste.ubuntu.com/24800085/)

---

### Post by Hadaka on 2017-06-07
Hi please open a terminal then copy and paste
```
echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rf rtl8723be
sudo modprobe -v rtl8723be
```
remove the wired connection,boot and test wireless
Thanks.

---

### Post by babak67 on 2017-06-07
Thanks man it works ! 

i did

echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rf rtl8723be
sudo modprobe -v rtl8723be

Before I boot, it worked. I booted and it stopped finding the network.
I did so
sudo modprobe -rf rtl8723be
sudo modprobe -v rtl8723be

and it works again.

Should I write a script to do it automatically :) ?
Will you please tell me what was wrong and how you fixed it please ?

---

### Post by wildmanne39 on 2017-06-07
Please do:
```
sudo su 
echo rtl8723be >> /etc/modules 
exit
```
Reboot

---

### Post by Hadaka on 2017-06-07
Hi ,as Wildmanne39 stated, there were a few things noted in your
 wireless diagnostic report that needed attention.

 The wireless card rtl8723be,Ubuntu 17.04 requires this parmater to functon correctly
in the # /etc/NetworkManager/NetworkManager.conf # file
```
 #[device]
#wifi.scan-rand-mac-address=0
```

The country code was not set, this can cause drops and other issues, it was corrected with.
```
 #sudo iw reg set FR
 #sudo sed -i 's/=.*/=FR/' /etc/default/crda
```

Lastly, the rtl8723be wireless card has 2 physical connection points for the antenna
and the ability to use either point by moving the antenna wire or by issuing a parameter
command to # /etc/modprobe.d/rtl8723be.conf.  The default value is 0 ,which means let the
computer os software figure out what to set the parameter to. Windows has the ability to do
this, Ubuntu does not. We first set the paramater to a value of "2" and it failed. The parameter
was then set to " 1 ' and the card functioned correctly.
```
 #echo "options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf- *FAIL
```
```
 #echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf- *CORRECT !
```

To load the module on every boot, please do..
```
sudo su 
echo rtl8723be >> /etc/modules 
exit
``` 
~     OR    ~
```
echo rtl8723be |sudo tee -a /etc/modules
```

*Please take the time to mark your thread Solved
by going to your thread then clicking Thread Tools and then choose Solved.
Thanks.

---

### Post by babak67 on 2017-06-08
Thank you very much guys.
You can consider this case as SOLVED :p

---

### Post by wildmanne39 on 2017-06-08
Your welcome!
Enjoy!

---


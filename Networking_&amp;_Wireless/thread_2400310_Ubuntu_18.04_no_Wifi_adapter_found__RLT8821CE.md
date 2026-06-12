---
title: "Ubuntu 18.04 no Wifi adapter found  RLT8821CE"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by mitchubishi21 on 2018-09-04
sorry to bother you all,  I just cant seem to find the answer. I have an HP pavilion x360 I just finished installing Ubuntu. I really like it but I cannot get the wifi working for the life of me. 

The network controller is Realtek semiconductor RLT8821CE 80211ac pcie wireless network adapter. Please help!!:(

---

### Post by chili555 on 2018-09-04
Please check here: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336)

---

### Post by mitchubishi21 on 2018-09-04
when I try this code it works until I get to the chmod lines of code
nothing happens when I hit enter. I type chmod +x dkms -install.sh and the terminal doesnt do anything

---

### Post by mitchubishi21 on 2018-09-04
Sorry, I am pretty linux illiterate:/

---

### Post by chili555 on 2018-09-05
In this context, no response means, roughly, “Command executed as ordered. I have no errors or warnings to report. Next?”

Please proceed. You are doing fine so far.


**EDIT**: For your benefit and others that may browse this thread, this command:```
 chmod +x dkms -install.sh 
```Means, roughly, 'change the mode of the file to make it executable' that is, so it can run and do things.

For an example, let's list all the attributes of some file:```
chili@T440p:~$ ls -al some_file
-rw-r--r-- 1 chili chili 13 Sep  5 09:28 some_file

``` Now let's make the file executable:```
chmod +x some_file
```And when we check its attributes again, we see:```
-rwxr-xr-x 1 chili chili 13 Sep  5 09:28 some_file

```Previously, the file was readable and writeable; now it is readable, writable and executable. That's the meaning of the x's in the attributes.

The change in mode is required for the file dkms-install.sh because you are, in the next steps, going to ask it to do something important; install your driver!

---

### Post by mitchubishi21 on 2018-09-05
Chili you are the best! thank you. Now, the wifi networks are getting connected but disconnecting over and over again. any idea how to fix that?

---

### Post by chili555 on 2018-09-05
Let's turn off power saving in Network Manager to see if it helps; from the terminal:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```And restart NM:```
sudo service network-manager restart
```Any improvement?

Quite often, in Linux drivers, the router settings can be tweaked to give better performance.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by mitchubishi21 on 2018-09-05
Its Working now! you are such an amazing help!! How do you know so much?! haha

---

### Post by chili555 on 2018-09-05
Glad it's working!

What little I know, I have gleaned in working with Linux here and on other forums almost every day for only about fifteen years! 

Have fun!

---


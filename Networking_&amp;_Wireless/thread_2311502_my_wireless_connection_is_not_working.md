---
title: "my wireless connection is not working"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by ali131 on 2016-01-27
i installed ubuntu on my new computer dell inspiron 15 3000 series 

before it was windows and wifi worked well on it . 

but on ubuntu it just can't work 

when i type "iwconfig" on terminal here's what i get : 


```
eth0      no wireless extentions.

lo        no wireless extentions.
```

i need help 

Thank you

---

### Post by mörgæs on 2016-01-27
Please read the sticky notes.

---

### Post by Hadaka on 2016-01-27
Hi, please open a terminal ..ctrl/alt/t..then copy and paste..
```
lspci -n | awk '/14e/{print$3}'
```
post the output
thanks.

---

### Post by ali131 on 2016-02-21
that's the result : 
> 
ali@ali-Inspiron-3543:~$ lspci -n | awk '/14e/{print$3}'
14e4:4365     


note that i fixed the problem using this set of commands : 
> 
apt-get --print-uris --yes install vlc | grep ^\' | cut -d\' -f2 >downloads.list   //save all the download links of all dependencies



wget -i download.list // recursive download

sudo  cp *.deb  /var/cache/apt/archives/  // move them to apt archives

sudo apt-get install <package name> "bcmwl-kernel-source" //install it 

and ubuntu identified wireless connections, the problem is that it isn't stable. 
it get connected then disconnected and loses transfer , sometimes 3000 B/s . it can't stand for half an hour without disconnection .

---

### Post by Hadaka on 2016-02-21
Hi, open a terminal and do..
```
sudo apt-get update
sudo apt get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
boot and test wireless.
*If no improvement then please do..
```
sudo modprobe -rf wl #your wireless will dissconnect
sudo apt-get remove --purge bcmwl-kernel-source #this removes what you loaded
```
Then go here [http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)
and follow the directions for the answer marked 5 - written by chili555
good luck.

---

### Post by ali131 on 2016-02-24
Hadaka 

I did all of that and still the network goes down and ge connected again and sometimes can't be detected 

is there any solution ? :confused::confused::confused::confused:

---

### Post by Hadaka on 2016-02-24
hi, please open a terminal and do..
```
lsmod | egrep "wl|ssb|b43|bcma|iwl|ndis"
```
post the output
thanks

---

### Post by ali131 on 2016-02-24
the output : 

> ali@ali-Inspiron-3543:~$ lsmod | egrep "wl|ssb|b43|bcma|iwl|ndis"
wl                   6365184  0
cfg80211              548864  1 wl

---

### Post by Hadaka on 2016-02-24
Please go here [http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
with a working wired connection
run the wireless diagnostics, it will build a file in your home directory named wireless-info.txt
please post that file.
thanks

---

### Post by ali131 on 2016-02-25
thank you for helping me :) 

the results : 

[http://pastebin.ca/3381654](http://pastebin.ca/3381654)

if the link doesn't work 

[http://textuploader.com/52v0i](http://textuploader.com/52v0i)


thank you

---

### Post by Hadaka on 2016-02-25
Hi, please open a terminal then copy and paste..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
then do..
```
sudo modprobe -rf wl
sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
Also..
your current access point TNCAPA423BF has been configured with
TKIP, if possible,access the router configuration for that connetion and
change the setting to WAP2 AES /CCMP and remove the TKIP
Then .
change your Network Manager configuration IPv6 to IGNORE.
Finally
I am not familure with I-Phone Teathering or Bluetooth attachment,but noticed
you have I-phone routing configured, I dont know if that is adding to your problem
or not, you may want to remove it and test.
thanks

---


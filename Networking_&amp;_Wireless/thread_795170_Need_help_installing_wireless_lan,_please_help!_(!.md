---
title: "Need help installing wireless lan, please help! :(!!!"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by mechanicalmetal on 2008-05-15
Hey guys,

Im a total linux noob. I am so tired of Windows I literally broke all cds in my house and anything that had the word microsoft on it, so if I don't learn to use linux, I will not own a computer. 

Basically I have learned a good bit in the past 2 days that I have installed Ubuntu. I am having a serious problem with getting my wlan drivers installed for ubuntu. I don't even see my wlan card in my laptop as a listing in hardware.

Heres my system,

Toshiba Satellite A205-S5800. The card is a realtek.
The specific model of my Realtek driver is RTL8187B.

Yes I have done google searches, but I don't know how to compile and unpack packages and stuff to make this work. Is there anyone who can guide me in the right direction to show me the link I need to go to to download the driver for linux for my wlan card and show me step by step what I need to do to install this for my system. I would really appreciate it. Please keep in mind I am 2 days old, and I know nothing about navigation of terminal accept how to log into root "su". I am very sorry to have to ask such foolish questions as I feel like a total pain in the rear, I will learn linux though dammit!!!

Based on what I have read on this forum, you guys rock, thats why I am so confident you guys can help me with a solution.

Thank you so much for your time!!!!!!!!!

---

### Post by bluefrog on 2008-05-15
if you have an ethernet connection, use it to update your installation and hopefully you will be proposed restricted drivers to use with your WIFI card.

If not then you can use ndiswrapper: (install it with synaptic, it should be on the cd you installed from - if it's the alternate cd). You need to have access to your windows drivers for this card.

then open a terminal:
sudo ndiswrapper -i /path/to/your/windows/driver.inf
sudo modprobe ndiswrapper
echo ndiswrapper | sudo tee -a /etc/modules

You should have access to your card if lucky enough.

---

### Post by mechanicalmetal on 2008-05-19
nope, dont see anything :(

---

### Post by Eman1955 on 2008-05-19
First things first, relax.



5-16-08



 Re: Wireless in Ubunyu with Dell E1505 - No go

Quote: Originally Posted by Eman1955 View Post





Look these instructions over for wireless configuration.  (If you have one; although not totally necessary)
[http://www.linuxwireless.org/en/user...43andb43legacy](http://www.linuxwireless.org/en/user...43andb43legacy)


Reply from friend:  The instructions look fine. The only thing that I will mention is that if you don't have build-essential installed, you will not be able to compile the b43-fwcutter.



b43-fwcutter should be in the installation CD. To add it from the Terminal:

Code:  sudo apt-cdrom add



It will ask you for the CD. Insert it and it will be added. Then:

Code:   sudo apt-get update



will load the package lists into the system.

Code:  sudo apt-get install b43-fwcutter



It will install the package and then will ask you if you want to have it find the firmware for you. If you DO have an internet connection, say yes and it will install it for you.



If you do NOT have a working internet connection, make sure that you say no or cancel. You will need to download the firmware and place it in your home directory. Here are the files that you need:

[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o)

[http://downloads.openwrt.org/sources...0.53.0.tar.bz2](http://downloads.openwrt.org/sources...0.53.0.tar.bz2)



Once they are in your home directory, go to the Terminal and do the following:

Code:



cd

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

tar xfvj broadcom-wl-4.80.53.0.tar.bz2

sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy



That should do it. It is very similar to the link that you just provided. The difference is that this one will also load the b43legacy drivers also. This is the way that Ubuntu does it. The information above is based on their install script that comes with b43-fwcutter.

Ayuthia is offline Report Post

---


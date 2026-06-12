---
title: "Xubuntu 18.04 - wifi doesn't connect anymore"
date: 2018-08-27
forum: Networking &amp; Wireless
---

### Post by Alexander_O on 2018-08-27
Hi all,

I have a HP 15-ay045ng laptop with a realtek "RTL8723BE" wifi chip. OS is Xubuntu 18.04. Unfortunately, after an update (I did "sudo apt-get update && sudo apt-get upgrade"), I can't connect to my home wifi network anymore. Could you please help me? Tell me what information you need and I'll post it here.


Thanks in advance
Alex

---

### Post by jeremy31 on 2018-08-27
Do ```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github/com/lwfinger/rtlwifi_new
cd rtlwifi_new
make
sudo make install
```
Then reboot
If the next kernel isn't fixed do
```
cd rtlwifi_new
make clean
make
sudo make install
```
Reboot

---

### Post by Alexander_O on 2018-08-29
Hi,

unfortunately I get a few errors when I try these commands:

[https://pastebin.com/ftnDXuLE](https://pastebin.com/ftnDXuLE)

---

### Post by jeremy31 on 2018-08-29
Do ```
cd ~/rtlwifi_new
git pull
make
sudo make install
```
You may have cloned the source before the 4.15 patches where included

---

### Post by Alexander_O on 2018-08-30
Unfortunately same errors:

[https://pastebin.com/jUZx2JqT](https://pastebin.com/jUZx2JqT)

---

### Post by jeremy31 on 2018-08-30
Ok ```
cd ~
sudo rm -rf rtlwifi_new
git clone https://github/com/lwfinger/rtlwifi_new
cd rtlwifi_new
make
sudo make install
```
Reboot

---

### Post by Alexander_O on 2018-08-31
Thanks a lot!

Now everything works again :-)))

---

### Post by Alexander_O on 2018-09-15
Hi,

I had the same problem again, also after a normal update. So I had to do the same procedure and now it works again. Is there a possibility to "protect" the "rtlwifi_new" folder from updating?

Thanks in advance,
Alex

---

### Post by jeremy31 on 2018-09-15
You can use dkms to build the driver when a new kernel is installed
```
sudo apt install dkms
sudo dkms add rtlwifi_new
```
Then you should be set

---

### Post by Alexander_O on 2018-09-15
Thank you =)

---

### Post by Alexander_O on 2018-12-11
Hi again,

the same problem occurs again and again after kernel updates. All I could do in order to solve it till now was your suggestion:

cd ~
sudo rm -rf rtlwifi_new
git clone [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
cd rtlwifi_new
sudo make
sudo make install

reboot



Thanks for this one. I have a question. Is it possible to copy this github content to my hard disk in order to do these commands offline? When I'm at home it's not a problem to connect my notebook with a lan cable to the router/modem and to do these commands above, but when I'm somewhere else and the same problem occurs and I don't have a lan cable around (or access to the router/modem!) then I just cannot get my wifi work again and stay offline. That's why it would be really cool if I could do the same commands-procedure while being offline. Could you please help me to achieve it? Thanks a lot in advance.

---

### Post by jeremy31 on 2018-12-11
You should be able to
```
cd rtlwifi_new
make clean
make
sudo make install
```

---

### Post by Alexander_O on 2018-12-11
Hi,

ok, thanks a lot. I'll try this next time! :)

---


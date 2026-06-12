---
title: "Tutorial for people who has problem with DVD RW Optiarc in Ubuntu Lucid"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-08-30
When i installed first time ubuntu lucid i had 2.6.32 kernel with it the thing is that every time i booted up ubuntu udev pulled nonstop!!!! Optiarc DVD so i had everytime i booted up to restart udev cuz it used 30 to 50% of the cpu but i found solution.

i upgraded kernel from 2.6.32 to 2.6.35.19 and dont have any more any problems with udev and high cpu usage and thats how i did it.

first at all in synaptic u wont find 2.6.35 unless u do :

[LEFT][B]sudo add-apt-repository ppa:kernel-ppa/ppa 

&& sudo apt-get update[/B]

after that open synaptic type linux and install latest kernel linux image and linux headers or just do 
[/LEFT]
[B]
sudo  apt-get install linux-headers-2.6.35-19 linux-headers-2.6.35-19-generic

and than

sudo update-grub2 

and if u have burg installed 

sudo update-burg 

dont remove yet your old kernel restart ubuntu boot up in 2.6.35.19 and see udev doesnt pull optiarc no more.

and one more thing to people who got ati graphic card after every kernel upgrade u need to reinstall catalyst it maybe that when u boot up in 2.6.35 it will boot up in low graphic mode if so reinstall your graphic card. the latest catalyst for ati card is ver 10.8 get it from here 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

if u see everything is ok remove old kernel and again sudo update-grub2 , sudo update-burg

thats all


[/B]

---


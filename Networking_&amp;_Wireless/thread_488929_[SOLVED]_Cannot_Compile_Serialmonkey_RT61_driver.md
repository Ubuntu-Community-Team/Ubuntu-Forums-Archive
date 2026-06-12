---
title: "[SOLVED] Cannot Compile Serialmonkey RT61 driver"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by regomodo on 2007-06-30
[yes a double-post but i thought it'd be more suitable in here, plus i'm getting nowhere]

Hi

I have just installed feisty server onto my T'pad and am now trying to install the drivers for a Ralink RT61 wifi card from serialmonkey. I know this works with a normal install but i cannot for the life of me get the package to compile correctly

I have

$ tar -xvzf rt61.........tar.gz
$ cd ./Module

but when i go to do

$ sudo make

i get
Code:

make: *** /lib/modules/2.6.20-15-server/build: No such file or directory. Stop.
rt61.ko failed to build!
make: *** [module] Error 1

I have installed the build-essential package and was shocked i had to install the make package after the server install.

Please help.What is causing this error?

---

### Post by kevdog on 2007-06-30
I dont know the command off the top of my head but you may also need to install the linux headers for your kernel.  You may need to search the forums or google for the exact syntax.  If that doesnt work, Im not sure what to recommend

---

### Post by regomodo on 2007-06-30
do you mean install kernel headers?

so far i've looked up on how to install linux headers

$ sudo apt-get install linux

that's all i can find and it doesn't work due to the fact the package isn't on the cd. I have no internet connection on the laptop until i get the wifi working

EDIT: doh it should have been linux-headers. trying it now

---

### Post by kevdog on 2007-06-30
Im not saying this will work but its worth a try:

1. Put in Ubuntu installation cd and wait for it to spin up
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install linux-headers-`uname -r`

Hopefully if all that works then try to compile again!

---

### Post by regomodo on 2007-06-30
cheers kevdog

just b4 you posted i did it.

i did

$ sudo apt-get install linux headers-2.6.20-15-server  (from the cd)

then changed directory where the driver was tar'd to

$ sudo make
$ sudo make install

I had already edited my /etc/network/interfaces file and my wifi works perfectly with wpa. For some reason i didn't have to copy over .bin files to folder or do an *ifup*. Did anyway and amazingly still works after a reboot. Did even have to mess around with* route*


Your only idea was all that was needed. Many thanks


[edit] for some reason i had to install *gcc *the 2nd time i did this server install ( i had too many cock-ups i thought i should do a fresh install)

---

### Post by regomodo on 2007-07-01
wow, this must have been a fluke as i haven't been able to do it since.

i tried to do the usual steps onto my quiet hdd but 1st it would never auto start the wifi card. now i cannot sudo ifup the device.

bloody hell this is weird

[edit] forgot to install *build-essential *package

---


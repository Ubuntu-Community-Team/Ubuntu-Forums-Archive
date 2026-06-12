---
title: "scanning issues"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by toosweetnitemare on 2006-08-02
i have Ubuntu with Dapper and in the networking tab i have an icon for eth1, which is my wireless card. I am on a Dell Latitude D600 and have a BCM4306 card. Ubuntu obviously recognizes that the wireless card is there, but i can not connect to anything period, i cant even scan for networks. ive had a few buddies look at it as well and no one know what is going on. please help, if you need more info just ask.

---

### Post by insyzygy on 2006-08-03
Ubuntu appears to include drivers for the bcm4306 chipset and so it will show up without you doing anything. However, before these drivers will work you need to extract firmware. There is a program called bcm43xx-fwcutter you must install using synaptics or apt-get. It will extract firmware which will allow the detected card to work. I'm not sure your level of experience, there is a pretty good doc file that comes with it that might explain the use, otherwise you might want to search here on the forums, I remember I found quite a few forums with detailed instructions on exactly what to do. I did it a while ago so I don't exactly remember the procedure, if you can't find anything let me know and I can look at what I did. 

If you can't get the linux drivers to work you should know there is another option, ndiswrapper. I have found that ndiswrapper works better for me with this chipset. you may wish to try that if you can't get the included driver to work, in case you don't know, ndiswrapper is a (quite cool) program that lets you use windows drivers for wireless cards to make them work in linux. At the moment I'm typing on a dell inpiron connected wirelessly using ndiswrapper.

One thing to note that messed me up for a while is that on many dells turning on the wireless cards antenna must be done with some key combination often Fn-F2. In windows this will cause an led to turn on or off indicating the antenna is active or not. This is something controlled by the bios so in linux the key combination still turns the antenna on and off but the led isn't active (the led is controlled by some custom windows software dell installs I think). For a while I was mystified why things weren't working eventually i tried Fn-F2 and even though no lights went on, wireless worked suddenly. This is annoying as you can't tell whether the wireless is working and the antenna just off or things just aren't working.

---

### Post by toosweetnitemare on 2006-08-04
i tried getting ndiswrapper to work, but once agian i was just lost at how to do it. im going to see if the fn f2 button works


if you need any screen shots just ask

---

### Post by insyzygy on 2006-08-04
We can come back to ndiswrapper, its sometimes tricky to set up. 

For the moment using the native drivers. Did you use the fwcutter tool? I found the instructions I followed they are here 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

get the firmware cutter by

```
sudo apt-get install bcm43xx-fwcutter
```

then use the automated script

```
 sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh 
```
You will probably have to restart then.


One further complication to be aware of, ndiswrapper and the native bcm4306 drivers don't play well together. If you just installed ndiswrapper from synaptic then this won't matter. But if you've a done 'sudo modprobe ndiswrapper', you will have to change one thing so they aren't conflicting.

---


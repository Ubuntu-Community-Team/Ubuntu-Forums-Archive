---
title: "Unified way of starting and stopping Bluetooth serial in Java?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by outleradam on 2010-06-14
I am writing a java program to communicate with my automobile's computer.   

In windows it is simple. I connect the device, and then it asks me for a pin, then it creates a COM port.  Then in Java, I use the built-in serial device selector and it is done. 

In Ubuntu, I have to do the following..
I connect the device, then it asks me for a pin.  Then I have to set some values in /etc/bluetooth/rfcomm.conf.  
```
rfcomm0{
 bind yes;
 device 00:0D:18:B1:09:DA ;
 channel 1;
 comment "Bluetooth Serial"
}
```Then I have to run the following commands.
```
hcitool cc 00:0D:18:B1:09:DA
hcitool auth 00:0D:18:B1:09:DA
rfcomm connect 0 &
stty -F /dev/rfcomm0 speed 9600 ignbrk -raw -brkint -icrnl -imaxbel -opost -onlcr -isig -icanon -iexten -echo -echoe -echok echoctl -echoke time 5 min 1 line 0
ln -s "$myObdComPort" /dev/ttyS5

```Am I doing it wrong? Why is this so complicated?  Why does Ubuntu not create this ttyS5 automatically when it sees my device connected?  How am I supposed to do it?  Any help would be good.

---


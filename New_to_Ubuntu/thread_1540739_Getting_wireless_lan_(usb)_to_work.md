---
title: "Getting wireless lan (usb) to work"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by mojo risin on 2010-07-28
Hi , I have wubi lucid lynx, and have a fritz wlan usb stick. The usb stick is seen in lsusb
```
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 057c:6201 AVM GmbH WLAN USB v1.1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` 
I tried the Athos driver, but either I did something wrong(likely) or it did not work .The athos driver site also mentioned firmware update but I don't know if this needed.
and if it is installed does it find the networks automatically?or do i first have to put credentials in?

---

### Post by mikewhatever on 2010-07-28
If the card has been recognized and is working, you should be able see the networks around you. Obviously, you'll need credentials to connect to secure networks.

---

### Post by mojo risin on 2010-07-28
goodd, took a while till the network manager saw it. and put the credentials in there. (the other manager which oicked my network up first didnt seem  to have a place to put credentials in..)

ok so what I did was. extracting the drivers files(i used my partners laptop for that ) created an inf file according to the german ubuntu wiki. and ndiswrapped it. I hope I don't have anymore problems with it it took me more than a week to figure it out xD

---


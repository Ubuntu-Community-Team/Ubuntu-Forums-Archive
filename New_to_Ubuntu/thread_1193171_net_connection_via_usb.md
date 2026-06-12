---
title: "net connection via usb"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by orky7 on 2009-06-21
hi, i have a broadband connection and in my old PC i don't have a Ethernet card so i connect the modem via usb but when i type pppoeconf it says no interface detected so what is the problem what to do now do i have to install some kind of driver if so then how...
thanks

---

### Post by LewRockwell on 2009-06-21
it's likely that we'll need the computer and modem information

---

### Post by 3rdalbum on 2009-06-21
It might be easier to get an Ethernet card. Very little work has been done on reverse-engineering drivers for all seventeen billion different models of USB ADSL modems, because all those modems work so much better and easier with Ethernet.

If you can't put an Ethernet card in, you should give us the model number of the router, and what version of Ubuntu you have.

You may be able to get the model number of the router via the command:

```
lsusb
```

---

### Post by LewRockwell on 2009-06-21
I didn't go through this post/procedure but thought I would include it here for anyone having problems to give some extra ideas.

[http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html](http://jeysundar.blogspot.com/2009/05/reliance-net-connect-on-ubuntu-kubuntu.html)

---

### Post by DGortze380 on 2009-06-21
> **orky7 said:**
> hi, i have a broadband connection and in my old PC i don't have a Ethernet card so i connect the modem via usb but when i type pppoeconf it says no interface detected so what is the problem what to do now do i have to install some kind of driver if so then how...
thanks

What kind of broadband connection?
What USB Adapter?

It may not be PPPOE.

---

### Post by orky7 on 2009-06-21
sorry guys i am late here is the result:
i omitted the first two device coz they r my mouse and keyboard.so 

**BUS 001 DEVICE 003: ID 0915:0005 Globespan, Inc**

so i think my idvendor is 0x0915
and idproduct is 0x0005 Globespan, Inc

so whats the solution now....

thanks

---

### Post by orky7 on 2009-06-21
i google here and there and find this

[http://eciadsl.flashtux.org/modems.php?lang=en&modem=globespan](http://eciadsl.flashtux.org/modems.php?lang=en&modem=globespan)

vendor-id matches 0915 but the product id i think did not matches as it is 0001,0002 and mine is 0005 i dont know know whether it matters or not so what to do now....

---

### Post by LewRockwell on 2009-06-21
> **LewRockwell said:**
> it's likely that we'll need the computer and modem information.

---

### Post by orky7 on 2009-06-21
@lewrockwell---- ok tell me the commands and i will paste the output

---

### Post by LewRockwell on 2009-06-21
> **orky7 said:**
> @lewrockwell---- ok tell me the commands and i will paste the output

sudo give the guys and gals on the ubuntu forum your computer's make, model, part or build number(if any), installed operating system(s), and any other software or customization, accessories, peripherals, etc

sudo give the guys and gals on the ubuntu forum your modem's make, model, part number, and any knowledge of firmware and/or firmware updates

[center][img]http://imgs.xkcd.com/store/imgs/sudo_square_0.png[/img][/center]

---

### Post by orky7 on 2009-06-21
i have know idea what u just written but if u can give me the commands if u know so that i can give u the output so that it will help u....
thanks

---

### Post by orky7 on 2009-06-21
thanks guys my problem solved i get the drivers and specifically for ubuntu and all the patch :P:P:P:D:D:popcorn:

---


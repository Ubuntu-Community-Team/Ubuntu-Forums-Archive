---
title: "Need Wifi - what USB wireless adaptor is suited ?"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by oygle on 2015-12-13
Found out that a computer wouldn't recognise a wifi connection ( see [http://ubuntuforums.org/showthread.php?t=2306176](http://ubuntuforums.org/showthread.php?t=2306176) ).

The computer was old (2008 vintage) , and simply had no wireless. What USB wireless adaptor is suited for Kubuntu, to be able to connect to the Wifi ? There are some models at [http://www.officeworks.com.au/shop/officeworks/c/technology/networking/wireless-usb-adapters](http://www.officeworks.com.au/shop/officeworks/c/technology/networking/wireless-usb-adapters)

---

### Post by QIII on 2015-12-13
thinkpenguin.com offers [several products]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux") that might suit your needs.

I have heard that some few Dell laptops may not work with the internal cards, but I think that is a small number of models.

---

### Post by oygle on 2015-12-13
> **QIII said:**
> thinkpenguin.com offers [several products]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux") that might suit your needs.

I have heard that some few Dell laptops may not work with the internal cards, but I think that is a small number of models.

Thanks for the penguin link. I have a Dell laptop and the wireless worked out of the box there. Some wireless adaptors at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) , not sure how updated that list is.

---

### Post by oygle on 2015-12-13
Seems these are okay -

TP-Link TL-WN722N
TP-Link TL-WN821N
D-Link DWA-121

Have purchased the TP-Link TL-WN722N.

---

### Post by C.S.Cameron on 2015-12-13
I have had good lick with TP-Link products.

---

### Post by Hadaka on 2015-12-13
Hi, tossing my 2 cents in...any rt73usb flys out of the box.
if you do a search on "usb wifi rt73usb" you will see several at varied prices
that vintage computer may or may not have a problem with the TL-WN727N usb
which requires..
```

sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/porjo/mt7601.git 
cd mt7601/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta

```
and after every linux image update
```
cd ~/mt7601/src
make clean
make
sudo make install
sudo modprobe mt7601Usta
```
and i doubt the 2008 machine will play N speeds anyway.
sooooo..i vote for the known rt73usb b/g kernel has the driver already.
;)

---

### Post by SeijiSensei on 2015-12-14
I'm using a TP-Link adapter on this machine, and it works quite well.

I've used an [Edimax EW-7811Un]("http://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY") with a Raspberry Pi.  It has pretty decent reception given how tiny it is.  I see that TP-Link has also entered this market with the [TL-WN725N](http://www.amazon.com/gp/product/B008IFXQFU) and similar products.  Adapters like this would be my choice on a laptop because of their small size.

---

### Post by oygle on 2015-12-15
Thanks for those replies, and Hadaka thanks for the code also. Adaptor should arrive in the next few days, can then try it out.

---

### Post by oygle on 2015-12-23
> **Hadaka said:**
> Hi, tossing my 2 cents in...any rt73usb flys out of the box.
if you do a search on "usb wifi rt73usb" you will see several at varied prices
that vintage computer may or may not have a problem with the TL-WN727N usb
which requires..
```

sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/porjo/mt7601.git 
cd mt7601/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta

```
;)

Well, as it didn't work "out of the box", I did the installation as outlined above. All went okay with that code. The installation placed everything in the /home/******** path; hope that is okay.

Now I can tick the wireless icon in network Manager. There is some wireless information attached. Wireless USB isn't visible ?? Will hook up a mobile phone tomorrow, and see if anything shows up.

---

### Post by Hadaka on 2015-12-23
Hi , from a working wired connection please open a terminal ctrl/alt/t and
 COPY and paste one line at a time.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo modprobe -rf mt7601Usta
sudo modprobe ath9k_htc
```
*If wireless works then do.
```
echo "ath9k_htc" | sudo tee -a /etc/modules
```
thanks.

---

### Post by oygle on 2015-12-23
Thanks Hadaka. I ran the first command and then noticed "upgrade" in the second command. I'm happy with vers 14.04 , don't want to upgrade.

Have read this also - [http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)

---

### Post by Hadaka on 2015-12-23
Hi, this does NOT upgrade to the next load.
```
sudo apt-get dist-upgrade
```
I would not send the command if it did,
Did you fully read the link you posted above???
no where does it say that it would do something
like "Upgrade" you from 14.04 to 15.10 or any other
load than the one you currenty have.....so if
you are paranoid,skip it and do the others.
thanks.

---

### Post by oygle on 2015-12-23
Okay thanks. I always associated the word "upgrade" == next release

I will bit the bullet and do that command.

---

### Post by oygle on 2015-12-23
Here's what happened ....

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo modprobe -rf mt7601Usta

```

> modprobe: FATAL: Module mt7601Usta not found.

Considering the above fatal msg, decided to use the commands to be run after linux image update

```
cd ~/mt7601/src
make clean
make
sudo make install
sudo modprobe mt7601Usta
```

and then go back to the other commands ...

```
sudo modprobe -rf mt7601Usta
sudo modprobe ath9k_htc
echo "ath9k_htc" | sudo tee -a /etc/modules
```

> ath9k_htc

Took quite a while to get the wireless hotspot going, but that was more a learning curve with me using a smartphone.  lol

Does the wireless now work ??  Sure does, am posting this with the USB wireless adaptor connected.

BIG thanks to Hadaka, and also others who helped get this going.  :)

---

### Post by Hadaka on 2015-12-24
Glad you got it going !

---

### Post by oygle on 2015-12-24
I'm glad **you** got it going  :)

---


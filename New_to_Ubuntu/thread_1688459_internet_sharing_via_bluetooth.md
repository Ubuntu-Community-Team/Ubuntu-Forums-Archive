---
title: "internet sharing via bluetooth"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by mark.markyn on 2011-02-15
hello everyone !!

i am trying to setup internet sharing b/w a windows mobile 6.0 and ubuntu 10.04..
but everytime i setup a dialup networking from the bluetooth manager i end up with the error(file attached) please help..

---

### Post by davidmohammed on 2011-02-15
never done this myself - however this [thread ]("http://ubuntuforums.org/showthread.php?t=1101364")is similar but using an older version of ubuntu.

Hopefully it will give you some ideas...

---

### Post by mark.markyn on 2011-02-15
i use a motorola Q9H windows based mobile..


it would be appreciated if anybody gives a general solution to connect to internet via bluetooth from any device that shows up as a "smart phone" in the bluetooth manager.

---

### Post by mark.markyn on 2011-02-15
> **davidmohammed said:**
> never done this myself - however this [thread ]("http://ubuntuforums.org/showthread.php?t=1101364")is similar but using an older version of ubuntu.

Hopefully it will give you some ideas...


i tried this but in vain..

---

### Post by davidmohammed on 2011-02-15
the only recent thread I found with your phone is [this one]("http://ubuntuforums.org/showthread.php?t=1375575")...

---

### Post by PaulReaver on 2011-02-15
so you want to connect to the internet with your computer by pairing it to your phone?

---

### Post by PaulReaver on 2011-02-15
i suppose this all depends on if your phone has a bluetooth dialup profile.... some mobile networks disable them in firmware to stop people taking advantage of the unlimited smartphone tariffs...

anyway here's how I connect my nokia as a bluetooth dialup modem.


add yourself to the 'dip' group
sudo adduser <your username> dip

and log out and back in


pair your phone with the bluetooth applet on the gnome desktop
then

in a terminal


sdptool browse


it should show your phones' bluetooth address at the top in this format XX:XX:XX:XX:XX:XX   (with numbers and letters instead of just X's)
then below it should list your device's bluetooth channels.
you're looking for the channel that says "dialup".

once you have the bluetooth address and dialup channel

in a terminal

sudo rfcomm bind rfcomm0 <bluetooth address>  <dialup channel>



once you've done this your phone is essentially a dialup modem (on /dev/rfcomm0).... you can then use pppconfig and pon to connect to the net.... 
or alternatively use gnome-ppp... 
you will need to know your mobile networks connection settings...
eg username and password and phone number (usually *#99#)


a bit complicated but if you get stuck just ask....

---


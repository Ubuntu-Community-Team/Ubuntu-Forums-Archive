---
title: "novatel mc930d"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by albert s on 2009-07-12
trying to get a novatel mc930d to work in ubuntu, 
i have had a look here,
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards](https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards)
but am unsure as to what i do after i eject.
the icon is on my laptop, and i can see the .inf files etc. 
please help, Im totally new not only to ubuntu, but computers in general.


[SOLVED]  by having a hard wired connection and getting all the updates prior to trying to do anything else first

---

### Post by shifty_powers on 2009-07-12
what version of ubuntu are you using?

---

### Post by albert s on 2009-07-12
sorry, should have said,
its version 9
i think its 9.04, jaunty

---

### Post by shifty_powers on 2009-07-12
and this is a 3g card for mobile broadband, yes?

---

### Post by shifty_powers on 2009-07-12
if i'm reading the guide properly, you should just be able to eject the card, ~(not physically of course), and then just right click on network manager in your sys tray and select the 3g option to configure it...

---

### Post by albert s on 2009-07-12
yes, its a 3g mobile braodband usb dongle on o2 UK.
it works fine on my windoze laptop, but as i am having problems getting my pc wireless card to work i thought i would use the dongle to get any updated drivers i need for it.
then i could download ndiswrapper if i need to.
thanks, I'll give that a go.

---

### Post by shifty_powers on 2009-07-12
i wouldn't recommend doing updates over a 3g modem, slow and potentially costly...

is the wireless card not working at all? and what type is it? built-in, usb etc?

---

### Post by scorp123 on 2009-07-12
> **albert s said:**
> trying to get a novatel mc930d to work in ubuntu

With the new Ubuntu 9.04 you should be able to insert the Novatel modem, eject it, and then NetworkManager should list a new 3G device, e.g. "Wireless Broadband" or something like that.

You'd then click on it, insert a few settings (e.g. which country you and your provider are from, the name of the provider .... In my case this would be: "Switzerland" + "Sunrise" ...) and that's about it. It should "just work".

---

### Post by albert s on 2009-07-12
built in wireless card, PCI
TP-LINK  TL-WN353G
I have had to unplug it because ubuntu simply refuses to boot up with it plugged in.!
keeps saying some kind of eth0 error, perhaps there is a conflict with the ethernet connector and i should try unplugging that instead.

---

### Post by scorp123 on 2009-07-12
> **shifty_powers said:**
> i wouldn't recommend doing updates over a 3g modem, slow and potentially costly... Not if you have a flat data plan that usually comes with such a modem, e.g. mine is 2 GB per month. For as long as you don't download DVD images you can download whatever Linux updates you need without problems.

---

### Post by shifty_powers on 2009-07-12
ah, here was me thinking you had a laptop...

have you tried putting it in a different pci slot?

---

### Post by shifty_powers on 2009-07-12
> **scorp123 said:**
> Not if you have a flat data plan that usually comes with such a modem, e.g. mine is 2 GB per month. For as long as you don't download DVD images you can download whatever Linux updates you need without problems.

and 2gb really is not a lot, it can disappear very quickly. I've had mobile broadband before.

really depends on the person and how much they use it...

---

### Post by albert s on 2009-07-12
> **shifty_powers said:**
> ah, here was me thinking you had a laptop...

have you tried putting it in a different pci slot?


sorry, my confusion, I do have borrowed an old laptop with mr gates software on it, that i am using now with the dongle,
but i am trying to get my pc working on wireless with ubuntu on it.
perhaps i should plug out the ethernet card and plug the wireless card in that slot?
yes, my dongle is a flat 3gb a month, and in reality i normally never go over 1gb, 
just use it for forums such as this etc, was only going to download the critical drivers i need for my wireless card or ndiswrapper and use the install cd if needed.

---

### Post by albert s on 2009-07-12
right, cant get the dongle to work,
have done all the installation wizard thing and have the icon in top bar, but just says network not connectted.
am going to try changing my wireless card slot.

---

### Post by scorp123 on 2009-07-12
> **shifty_powers said:**
> and 2gb really is not a lot I use it heavily on a daily basis and I rarely go beyond 750 MB per month. So those 2 GB are more than enough if you use it wisely, e.g. I wouldn't want to engage into P2P with a 3G modem, that's for sure. But getting Linux downloads really should not be a problem at all.

---

### Post by scorp123 on 2009-07-12
> **albert s said:**
> right, cant get the dongle to work OK, let's try a few manual methods then.

1.) Remove the Novatel dongle and shutdown your PC - yes I mean it.

2.) Boot it up.

3.) Login

4.) Then please open a terminal window and please give me the output of this command: ```
lsmod
```

5.) Insert the USB dongle, wait until it starts blinking

6.) Give me the output of these two commands: ```
dmesg
lsmod
``` (yes I know: same command. But chances are that the output will now be different ...)

7.) "eject" the virtual CD-ROM device the USB dongle created

8.) Please repeat step #6 and repeat those two commands again. Chances are that the output of both will change now. I want to see those changes.


Other things you could try in the meantime:

[http://ubuntuforums.org/showpost.php?p=3749057&postcount=2](http://ubuntuforums.org/showpost.php?p=3749057&postcount=2)
[http://ubuntuforums.org/showpost.php?p=3805821&postcount=9](http://ubuntuforums.org/showpost.php?p=3805821&postcount=9)

---

### Post by albert s on 2009-07-12
lsmod 
=
 do i really have to type all that out??????
f***** ell

---

### Post by scorp123 on 2009-07-13
> **albert s said:**
> do i really have to type all that out??????
 Ever heard of "copy & paste" ???  :lolflag:

---

### Post by albert s on 2009-07-13
its on a different computer,
I cant get online on my ubuntu PC.

---

### Post by scorp123 on 2009-07-13
> **albert s said:**
> its on a different computer,
I cant get online on my ubuntu PC. You could use a USB stick and copy & paste the output into a text file? If you have a USB stick, that is. They're not so expensive. Even a very small one should do the job. So you'd insert the USB stick into the Ubuntu PC, run the commands, copy & paste the output into text files ... And then come back to the PC with which you can go online, read the content of the stick and attach the files you created on the other PC.

Would this be possible for you? As I said: USB sticks are super cheap these days.

---

### Post by albert s on 2009-07-22
sorted,
got my computer plugged into a wired internet installation and once it had updated then it connected straight off from the usb dongle internet thingie,  :)
next step was to purchase one of these,
[http://www.edimax.co.uk/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44](http://www.edimax.co.uk/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44)
plug and play for linux it said on the box,
and it was right  :)
plugged it in and straight away it found 4 networks, 2 more than my other one found on windoze, :)
new problem tho,,,,,,
I can connect to my neighbours wifi no probs, but i cant connect to my own router,
password invalid or some such thing.!
tried every variation of what i can think it would be, but nothing works.
have tried to install aircrack, but am obviously doing something wrong,
how do i actually get aircrack to run? in the list it says i have it installed on my system, i can even see the files, but after i have built it i still have no idea how to get it to fire up and try to find my own password.!!!!
or is it just buy another router time? even when i try and plug directly into my router ubuntu still wont let me change the password without first knowing the old one!
thanks for all the help so far,
ps, the TP LINK card still wont work no matter how hard i try, boot was trying for over 24hrs and still hadnt loaded with the TP card installed.!!!!!

---


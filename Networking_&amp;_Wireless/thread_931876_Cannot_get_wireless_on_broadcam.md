---
title: "Cannot get wireless on broadcam"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by daimere on 2008-09-27
I have ubuntu.  I am very unfamiliar with ubuntu. Originally, it wouldn't let me online even wired.

 I used this thread: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") using the Dapper and Edgy (and Feisty/Gutsy with ndiswrapper) method.  This let me get online via a wire.

I tried these two methods:
[http://tsupra88.blogspot.com/]("http://tsupra88.blogspot.com/").  Neither worked.

Although ONE of these methods, I am unsure of which, made the wireless icon by the on button of my laptop turn on but it didn't let it get online yet.

I tried this method:
[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105]("http://ubuntuforums.org/showpost.php?p=1189681&postcount=105")
But because of all my other attempts, I didn't work because when I got to the go to networks, the wireless option which was always there before, wasn't there.

Somewhere along the way, that blue light also is gone.  I don't know when it stopped showing because I don't usually notice it that is why I don't know when it showed up or left.

This is the version broadcom I have:
[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-1.png[/IMG]

Can anyone help me? 
 It's not fun dragging my laptop around a long cord around my house just for the internet. lol  Thanks!

Shannon

---

### Post by ajmorris on 2008-09-27
hi there,
the easiest method for getting broadcom cards to work on linux is the ndiswrapper method. So, can you please post the contents of your /etc/modprobe.d/blacklist  file
and also the output of ```
sudo ndiswrapper -l
``` from a terminal.

AJ

---

### Post by NoWayBill on 2008-09-27
I have a bcm-4312 and also had a hard time getting wireless to work.
None of the drawn out fixes worked.
The solution ended up being quite simple.
I installed b43-fwcutter from Synaptics, that reads the firmware on the chip.

Worked fine after reboot using proprietary "wl" driver.
Doesn't work quite as well as in Windo$e.
The range is about 10ft shorter, pffft, and the amber indicator light is dim.

I know they're not the same chip, but maybe....

Good luck!!!

---

### Post by superprash2003 on 2008-09-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by daimere on 2008-10-02
> **ajmorris said:**
> hi there,
the easiest method for getting broadcom cards to work on linux is the ndiswrapper method. So, can you please post the contents of your /etc/modprobe.d/blacklist  file
and also the output of ```
sudo ndiswrapper -l
``` from a terminal.

AJ

I couldn't retreive the blacklist.  but this is what I got when I did the sudo command.

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-2.png[/IMG]

---

### Post by superprash2003 on 2008-10-02
you didnt try the steps in between?? 2a or 2b or ..... depending on output

---

### Post by ittiam on 2008-10-02
> **daimere said:**
> I couldn't retreive the blacklist.  but this is what I got when I did the sudo command.

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-2.png[/IMG]

Looks like you did ndiswrapper -1 (one) and not ndiswrapper -l (letter L). Or am i being little lame here?

---


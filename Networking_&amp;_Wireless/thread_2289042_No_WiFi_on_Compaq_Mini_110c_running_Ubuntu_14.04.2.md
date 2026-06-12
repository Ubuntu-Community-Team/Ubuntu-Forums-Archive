---
title: "No WiFi on Compaq Mini 110c running Ubuntu 14.04.2"
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by blake11 on 2015-07-31
My brother asked me to fix his laptop, the microsoft OS was missing a system file and wouldn't start.  I installed Ubuntu 14.04.2 LTS using a USB drive.  Now when we log onto his computer, a Compaq Mini 110c, it won't connect to or identify any available wireless connections.  Need help getting the internet up and running on that laptop.  A pretty much a newb when it comes to Ubuntu, still learning the basics.

---

### Post by Hadaka on 2015-07-31
please open a terminal...ctrl/alt/t and do..
```
lspci -n | grep 280 
```
post the output...thanks

---

### Post by blake11 on 2015-07-31
This came up...

03:00.0 0280: 168c:0032 (rev 01)

---

### Post by Hadaka on 2015-07-31
Hi, please do..
```
rfkill unblock all
sudo modprobe -r ath9k
sudo modprobe ath9k
```
then do and post
```
dmesg | grep ath
```
and lastly please run the wireless script
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by blake11 on 2015-08-01
This is what came up...

[     1.340616] Loaded X.509 cert 'Magrathea: Glacier signing key: 3c66a93eb5d1a5681166b681a517938d081e4dc7'
[    21.940911] audit: type=1400 audit(1009861233.072:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=786 comm="apparmor_parser"

---

### Post by Hadaka on 2015-08-01
hi,from a working wired connection please post a wireless info. txt file
from here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by blake11 on 2015-08-01
Here you go

File is attached

Did what the link you posted said to do but still no luck with wireless internet, only wired internet working.

thank you for the help

---

### Post by kerry_s on 2015-08-01
your just missing firmware, plug in & run "additional drivers", it's slow just wait.

you should be using xubuntu or ubuntu-mate, standard ubuntu is going to bring that to a crawl.

grab xubuntu 15.04, select install 3rd party drivers when you install & wireless will be working when you reboot. you don't need to be connected when installing, you can connect if you want just run "additional drivers" while running live.

i have the same wireless in my hp-mini 210-1010nr

---

### Post by Hadaka on 2015-08-01
Hi, the very first question i asked of you was to post..,
```
lspci -n | grep 280
```
and you said the response was...
03:00.0 0280: 168c:0032 (rev 01) <<<<------ you dont even have that card
where did you get those numbers,,,???
anyway,,,try this.,,from a working wired connection do
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
also COPY AND PASTE this in., one line at a time.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

---

### Post by blake11 on 2015-08-01
I just realized I ran the first command you wanted on my own laptop and not the Compaq mini.
Should I run that command now and give you the update info?

---

### Post by Hadaka on 2015-08-01
I have the correct information from the info.txt file  so all is fine.
please run the the last 5 commands i gave you..
thanks

---

### Post by blake11 on 2015-08-01
HADAKA,

when i typed in the third line " sudo modprobe b43" and hit enter, is anything supposed to happen?  When I typed that in and hit enter all that happened was " chad@chad-Compaq-Mini-110c-1100:~$ " showed up for me to enter another command.  Is that what was supposed to happen?

As for the code you wanted me to copy and paste in one at a time, I did and nothing happened except for the same thing as above where it went to waiting for me to enter the next command.  I entered the first line and hit enter, " chad@ yada yada " came up.  Entered second hit and hit enter and same thing.  Was anything in particular supposed to happen beyond it just moving to the next line for additional commands?

---

### Post by Hadaka on 2015-08-02
when it doesnt say anything..it means it liked it.
please post the output of,,
```
sudo iw reg get
```
then,disconnect the ethernet cable and boot
is wireless now working??

---

### Post by blake11 on 2015-08-02
WINNER, WINNER, CHICKEN DINNER!

I don't know what all you did to help me get to this point but thank you very much Hadaka!

---

### Post by Hadaka on 2015-08-02
great !  ok..sign back in,click thread tools..and
mark this solved.
thanks.

---


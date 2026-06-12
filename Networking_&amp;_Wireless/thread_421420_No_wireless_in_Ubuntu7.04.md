---
title: "No wireless in Ubuntu7.04"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by SwaroopKunduru on 2007-04-24
Hi All,

I installed Ubuntu7.04 and was using 6.04 before. Before an upgrade I use to connect to wireless internet and was working fine. When I upgraded I cannot see the wireless device in network manager. Please see the attachments.

Regards,

Swaroop Kunduru.

---

### Post by solar george on 2007-04-24
Did the wireless work 'out of the box' on edgy?

p.s. which is your wireless card, I don't recognise any of the devices on your lspci as wireless cards

---

### Post by Andrea91 on 2007-04-24
hi,
i've the same problem ...... my wireless card is rtl8180....
on edgy it worked fine...but since i've installed feisty i cannot solve this problem
(the same screen of SwaroopKunduru)
please help.... drivers should be well-installed....but it doesn't work !!!
thank u

---

### Post by jakesr on 2007-04-24
Me too. I have BCM43XX wireless and even got my ndiswrapper 1.42 installed and show that my bcm43xx card is installed and ready to use. But when I open the network manager. There is no wireless network for me to configure.

---

### Post by solar george on 2007-04-24
jakesr:

What drivers are you using for the bcm card, I found that ones (attached) from an auto install script for edgy worked whereas the ones that came with my card didn't.

---

### Post by jakesr on 2007-04-24
george:
I am using bcmwl5a.inf file instead of bcmwl5.inf. Cuz Ndiswrapper is not working if use bcmwl5.inf.

---

### Post by bigred3373 on 2007-04-24
> **SwaroopKunduru said:**
> Hi All,

I installed Ubuntu7.04 and was using 6.04 before. Before an upgrade I use to connect to wireless internet and was working fine. When I upgraded I cannot see the wireless device in network manager. Please see the attachments.

Regards,

Swaroop Kunduru.  I HAVE THE SAME ISSUE MINE DISAPPEARED AFTER RESTART AND ITS NOT ACKNOWLEDGING IT SAME AS THE PHOTO  DO I HAVE TO REINSTALL FAWN????:confused: :confused:

---

### Post by bigred3373 on 2007-04-24
> **jakesr said:**
> george:
I am using bcmwl5a.inf file instead of bcmwl5.inf. Cuz Ndiswrapper is not working if use bcmwl5.inf.
 YOU LOST ME HERE?????

---

### Post by jakesr on 2007-04-24
bigred3373:
I was replying george question on wht driver files I using. Please refer to the driver tar file he has attached.

---

### Post by bigred3373 on 2007-04-24
> **jakesr said:**
> bigred3373:
I was replying george question on wht driver files I using. Please refer to the driver tar file he has attached. oh okay lol frustrated cannot get this to work

---

### Post by solar george on 2007-04-24
> 
Quote:
Originally Posted by jakesr View Post
bigred3373:
I was replying george question on wht driver files I using. Please refer to the driver tar file he has attached.
oh okay lol frustrated cannot get this to work


The drivers are only for broadcom 43xx cards.

What is yours and how did you get it working in the first place?

---

### Post by bigred3373 on 2007-04-24
[https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=%28WifiDocs%2FDevice%29")

i did those steps and back on the mac Intel forum there is alot of codes i did it worked until i shut off then rebooted and know its gone

these were the first steps i tried go the link you will see all the work [http://ubuntuforums.org/showthread.php?t=417731]("http://ubuntuforums.org/showthread.php?t=417731")

Broadcom 4310 card

---

### Post by SwaroopKunduru on 2007-04-24
Andrea91,

That was my problem. I was working on Ubuntu6.04 and wireless connection was O.K I used NDISwrapper and able to connect to net. I can't do the same now. I installed 7.04 day before yesterday

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2007-04-24
Hi All,

Please see the attachment.

Regards,

Swaroop Kunduru.

---

### Post by solar george on 2007-04-25
> That was my problem. I was working on Ubuntu6.04 and wireless connection was O.K I used NDISwrapper and able to connect to net. I can't do the same now. I installed 7.04 day before yesterday

Try removing the drivers that you have installed in ndiswrapper then remove the ndiswrapper packages (including ndiswrapper-common) with the 'Mark for complete Removal' option.

Reboot

Reinstall the ndiswrapper packages and install the newest drivers from the manufacturer website.

---

### Post by stchman on 2007-04-25
> **SwaroopKunduru said:**
> Hi All,

I installed Ubuntu7.04 and was using 6.04 before. Before an upgrade I use to connect to wireless internet and was working fine. When I upgraded I cannot see the wireless device in network manager. Please see the attachments.

Regards,

Swaroop Kunduru.

If it is a Broadcom card then follow my procedure only if it is a 43xx card.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

It works for Edgy so it might work for Feisty.

---

### Post by Andrea91 on 2007-04-25
Any suggestion 4 rtl8180 wifi card???
and if i reinstall edgy n then upgrade it to feisty?
it worked on it !......i'm fed up:mad: .....help me guys !
thank u very much...

---

### Post by sheine on 2007-04-25
Just a quick note to encourage the masters of Ubuntu to do something. With my prism card I could use my wireless in Edgy but cannot make it work in Feisty. Obviously from the number of posts in this thread and other threads this problem is widespread.

---

### Post by SwaroopKunduru on 2007-04-25
> Try removing the drivers that you have installed in ndiswrapper then remove the ndiswrapper packages (including ndiswrapper-common) with the 'Mark for complete Removal' option.

Reboot

Reinstall the ndiswrapper packages and install the newest drivers from the manufacturer website.


I have installed Ubuntu7.04 and it is brand new. There is no ndiswrapper at all.

Regards,

Swaroop Kunduru.

---

### Post by solar george on 2007-04-25
> I have installed Ubuntu7.04 and it is brand new. There is no ndiswrapper at all.

OK, try,
```
sudo aptitude install ndiswrapper
```
This will install ndiswrapper.

Download the latest drivers from the manufacturer website.
```
sudo aptitude install cabextract
cd *directorywithwindowsdrivers*
cabextract ./*downloadname*
```

Install the drivers using ndiswrapper,
```
sudo ndiswrapper -i ./*.inf
sudo ndiswrapper -m
```

Reboot,

You should now be able to configure wireless through System>Administration>Network

---

### Post by Andrea91 on 2007-04-25
Does anyone know where i can find rtl8180 drivers ?? (the .inf file)
can i download it or not ?
is it in a windows' directory ??

---

### Post by SwaroopKunduru on 2007-04-26
Any One,


Did any on has any luck? I still cant find wireless on my system. 

Thanks and regards,

Swaroop Kunduru.

---

### Post by solar george on 2007-04-27
Have you tried redoing the steps that got it to work in edgy?

---

### Post by SwaroopKunduru on 2007-04-27
Yes exactly I did the same but I donot see the wireless Icon also I cannot able to connet to wireless.

Thanks and regards,

Swaroop Kunduru.

---

### Post by solar george on 2007-04-27
What make/model is you wireless card?

---

### Post by SwaroopKunduru on 2007-04-27
> **solar george said:**
> What make/model is you wireless card?

Please refer to the attachments.

Thanks and regards,

Swaroop Kunduru

---

### Post by solar george on 2007-04-28
OK, this may work and may not,

Do 
```
sudo gedit /etc/modprobe.d/blacklist
```

and find the line that says
```
blacklist r818x
```
change it to,
```
#blacklist r818x
```

When you reboot you should be able to see you wireless card, however you may not be able to connect, if you cannot try adding another character to the end of you essid (in the network manger), so if your network was called wireless you could put wirelessS or wirelessZ.

---

### Post by SwaroopKunduru on 2007-04-28
Thanks  solar george,

It works and it do excellent. Thanks for your help.

Regards,

Swaroop Kunduru.

---

### Post by Andrea91 on 2007-04-29
Thank U very much solar george !!!
Your way works very well.....:KS :KS :KS :KS :KS 
I do thank u ........Andrea91

---


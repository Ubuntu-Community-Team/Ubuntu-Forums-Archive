---
title: "Please help with wireless network recognition"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by fortinbras22 on 2009-02-05
Hello, everyone,

Thank you to the people who have helped me try to resolve this issue in the past...

I am very new to Ubuntu 8.10 (well to linux period); I am a lifelong Windows user and I recently decided to convert to Linux in the last week. As such I am not overly familiar or comfortable with the linux jargon I have been presented- although I have finally figured out how to use the terminal and enter code...

My Ubuntu is not recognizing the wireless network my condo association provides. At home it is my only source of internet access, thus I cannot get online via an ethernet connection (which does function properly when I am at work). Vista recognizes the wireless network at home...

In a previous thread, some very helpful people tried to direct me to enter code that I suppose would download the appropriate driver from snapshots.madwifi.org; unfortunately, this site no longer seems to exist. When I typed the code into the terminal (verifying spelling)is says there is an error with the site 'snapshots.madwifi.org.' Whenever I try to so much as visit it via internet explorer, I get the typical cannot-find-site error. 

So now can anyone suggest an alternative site to go to to get the appropriate files? (.tar.gz extension?)

I have an Atheros AR5007 802.11b/g wifi adapter. 

Through googling "snapshots.madwifi.org" I have come across the site: [http://snapshots.madwifi-project.org](http://snapshots.madwifi-project.org).

On the page, there are links which may work, but I am not sure which ones to try:
madwifi-dfs.current.tar.gz
madwifi-free-current.tar.gz
madwifi-hal-0.10.5.6-current.tar.gz
madwifi-hal-testing-current.tar.gz
madwifi-trunk-current.tar.gz

Will any of these files help me?
If so, what is the correct code entry to download and install?

If not, can someone please recommend another avenue to solve this issue?

Thank you so much for everyone's assistance!

---

### Post by apjone on 2009-02-05
\You could try the following, it says 8.04 but should work with 8.10

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by bumanie on 2009-02-05
I could not get madwifi working. I used method 2 found [here]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")

---

### Post by stchman on 2009-02-05
> **fortinbras22 said:**
> Hello, everyone,

Thank you to the people who have helped me try to resolve this issue in the past...

I am very new to Ubuntu 8.10 (well to linux period); I am a lifelong Windows user and I recently decided to convert to Linux in the last week. As such I am not overly familiar or comfortable with the linux jargon I have been presented- although I have finally figured out how to use the terminal and enter code...

My Ubuntu is not recognizing the wireless network my condo association provides. At home it is my only source of internet access, thus I cannot get online via an ethernet connection (which does function properly when I am at work). Vista recognizes the wireless network at home...

In a previous thread, some very helpful people tried to direct me to enter code that I suppose would download the appropriate driver from snapshots.madwifi.org; unfortunately, this site no longer seems to exist. When I typed the code into the terminal (verifying spelling)is says there is an error with the site 'snapshots.madwifi.org.' Whenever I try to so much as visit it via internet explorer, I get the typical cannot-find-site error. 

So now can anyone suggest an alternative site to go to to get the appropriate files? (.tar.gz extension?)

I have an Atheros AR5007 802.11b/g wifi adapter. 

Through googling "snapshots.madwifi.org" I have come across the site: [http://snapshots.madwifi-project.org](http://snapshots.madwifi-project.org).

On the page, there are links which may work, but I am not sure which ones to try:
madwifi-dfs.current.tar.gz
madwifi-free-current.tar.gz
madwifi-hal-0.10.5.6-current.tar.gz
madwifi-hal-testing-current.tar.gz
madwifi-trunk-current.tar.gz

Will any of these files help me?
If so, what is the correct code entry to download and install?

If not, can someone please recommend another avenue to solve this issue?

Thank you so much for everyone's assistance!

The Acer Aspire One has a similar wireless card.  You can use my instructions for getting the wireless portion to work using your laptop.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Download the script and comment out the lines pertaining to getting the wireless LEDs to work.  This should do the trick.

---

### Post by fortinbras22 on 2009-02-05
Thank you for all your help... as soon as I get back to my ethernet access point, I will impliment these suggestions...

Thanks again...

---

### Post by wolfen69 on 2009-02-05
hey stchman, is your website the same instructions as the ubuntu site? are there any differences? i'm probably getting an aspire one soon. :-)

---

### Post by nothingspecial on 2009-02-05
There`s a couple of things you could try. On the madwifi snapshots page download the madwifi-hal-0.10.5.6-current.tar.gz. When firefox asks you what you want to do with it select open with archive manager. It will ask you where you want to extract it. For ease extract it to your desktop.

Then ```
cd Desktop/madwifi*
```

```
make
```

```
sudo make install
```

```
gksudo gedit /etc/modules
```

then add ```
ath_pci
``` to the end of the file.

Save 
Close 
Reboot.

OR,


Go to system > administration > hardware drivers then disable anything in there.

Then
```

sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver


```
sudo modprobe ath5k
```

To make it load everytime you boot
Code:

```
gksudo gedit /etc/modules
```

and add

```
ath5k
```

To the end of the file

save
close
reboot

If you have already added ath_pci to /etc/modules then delete ath5k and vice versa.

---

### Post by stchman on 2009-02-05
> **wolfen69 said:**
> hey stchman, is your website the same instructions as the ubuntu site? are there any differences? i'm probably getting an aspire one soon. :-)

Yes, I took information off od the Ubuntu Community Documentation site and made a nice easy script to get the wifi working well.  The Intrepid backports work(ath5k), but the wifi is spotty.  The latest madwifi drivers(ath_pci) work far better but are harder to implement.

Get the AAO, install Intrepid, follow my madwifi instructions, follow the SD card reader instructions, and it will work very well.

I installed netbook-remix as I like how it uses the smaller screen.

---


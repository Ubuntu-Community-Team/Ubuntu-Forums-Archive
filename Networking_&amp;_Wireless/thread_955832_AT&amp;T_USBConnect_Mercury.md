---
title: "AT&amp;T USBConnect Mercury"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by MWSTX on 2008-10-22
I'm running Ubuntu Studio (Hardy) on my HP Pavilion laptop.  I recently purchased an AT&T USBConnect Mercury (USB modem) and I have tried all of the threads/suggestions I could find to get it to work and had no success. Anyone out there think they can walk me through this? If I'm not mistaken, I think the AT&T USBConnect Mercury is the same as the Sierra Compass 885 but the suggestions I've read for the 885 haven't helped either.

---

### Post by moastad on 2008-10-23
I am also having the same problem , dell laptop, ubuntu 8.04 64bit, same usbconnect mercury card . I see it on the usb port as a storage device instead of a modem.

---

### Post by moastad on 2008-10-23
this solutions worked for me !!!!:

[http://ubuntuforums.org/showthread.php?t=946379](http://ubuntuforums.org/showthread.php?t=946379)

---

### Post by mcarrigan on 2008-10-24
Hey, were you all able to get this working?  I may be moving in that direction and wanted to check, Thanks

---

### Post by bipolar on 2008-11-13
The problem is that Hardy's version of the sierra/usbserial modules does not support this card. You can compile the modules downloaded from sierra's website to gain support for it. I'm creating a package for our laptops in the field to replace the modules with updated ones.

---

### Post by analogred on 2008-11-17
I'm running Intrepid, and I haven't been able to get the Mercury aircard to work on it. I've done what Sierra said to do, (KPPP), I tried Gnome-PPP, I added the .fdi to the hal and tried network-manager, but nothing works. I contacted Sierra Wireless' Linux department hoping they'd have a go, and they showed me a "new version" of the document that they had posted, which was actually just the exact same files, text, and everything as the "old version".

I have had nothing but weeks of problems so far. I really need an answer, this is driving me nuts.

---

### Post by crayzeewulf on 2008-12-19
Please see the following post for a solution on Ubuntu 8.10:

[http://docs.google.com/Doc?id=d9khzpw_0w4m774dd](http://docs.google.com/Doc?id=d9khzpw_0w4m774dd)

---

### Post by sahrjd on 2009-02-18
> **crayzeewulf said:**
> Please see the following post for a solution on Ubuntu 8.10:

[http://docs.google.com/Doc?id=d9khzpw_0w4m774dd](http://docs.google.com/Doc?id=d9khzpw_0w4m774dd)

Didn't work for me:(

---

### Post by knlgSeekr on 2009-02-21
> **crayzeewulf said:**
> Please see the following post for a solution on Ubuntu 8.10:

[http://docs.google.com/Doc?id=d9khzpw_0w4m774dd](http://docs.google.com/Doc?id=d9khzpw_0w4m774dd)

people.. no need to stress over this, the fix took me no more than 3 mins & you should have no problems doing it..

go to the link posted by crayzeewulf

*now here's the important part that will keep you from freakin out & wasting lots of time wondering what you're doing wrong*

-in order to get the fix to work, as is stated you need to edit 10-modem.fdi.. you obviously need root privileges to do that so the easiest way to do so in my opinion is by using the graphical interface:

*so first copy the part that you will need to add to the file (highlighted portion)
*then run gksudo nautilus from a terminal
-this will open a graphical user interface similar to windows explorer which gives you admin/root privileges
-within this gui, click on file system (on the left) and browse to /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
-right-click on 10-modem.fdi, select "open with text editor" scroll down to sierra wireless as per the instructions, paste the info that you copied earlier
-save the file & close it
*open a terminal and run sudo /etc/init.d/hal restart
-enter your password
*once thats done, plug in your aircard and you should she a configuration prompt pop up from network manager.. just follow the steps (select provider etc)
-and you should be all set and able to connect after that..:)

i know there are other ways to access & edit the file but i figured this is the simplest way.. this is my first day back using linux after 3yrs & i had just started using it before so i'm a total newb.. i am a pc tech so i know anyone who is a windoze user is more comfortable using a gui rather than the command prompt

finally got a decent laptop with some decent hard drive space, dual core processor & a good video card yaaay! (hp g60), running a dual boot with vista premium & i'm excited about getting my linux skills up to par.. :D

---

### Post by mazatl on 2009-03-10
I did this and Network Manager is recognizing the Mercury modem.However, when I try to start the modem it automatically disconnects. Network Manager is also not recognizing any wireless networks. Any help would be appreciated.

---

### Post by bwvick on 2009-03-31
The solution by crayzeewulf worked perfectly for me.  Thanks.

---

### Post by tosk on 2009-04-09
> **mazatl said:**
> I did this and Network Manager is recognizing the Mercury modem.However, when I try to start the modem it automatically disconnects. Network Manager is also not recognizing any wireless networks. Any help would be appreciated.
There's a bug in NetworkManager that ships with intrepid that prevents the access point ID from being set.
```
sudo apt-get update
sudo apt-get upgrade network-manager
```

---

### Post by Deadwulfe on 2009-04-09
> **moastad said:**
> this solutions worked for me !!!!:

[http://ubuntuforums.org/showthread.php?t=946379](http://ubuntuforums.org/showthread.php?t=946379)

This thread got me in the right direction. I'm running 8.10 and I have an AT&T Mercury USB adapter. I didn't do a lot of configuration to find out what worked, but I did end up having to configure it again after reinstalling Ubuntu.

Ultimately what worked for me was creating the modems.fdi file from the OP's post and placing it in the */etc/hal/fdi/information/* folder as baylinux states.

Then I followed the link to Sierra's website and installed the driver per the Sierra Driver Installation Instructions. I did NOT have to continue with any other steps from their site.
[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500)

After installing the driver I rebooted my computer; restarting hal didn't work for me. Then I plugged in my Mercury adapter, right-clicked on the Network Manager icon on the task bar to Edit/Add a new AT&T tethering with data acceleration connection under the Broadband tab. Finally, I edited the connection, deleting the username and APN, and leaving the phone number and password alone.

I closed those windows, clicked on the network manager, selected the AT&T connection, and now I'm here posting how I got on the internet! ):P

---

### Post by semjaza on 2009-08-24
I had an issue with the USBConnect only connecting to the 2g network, however when I used minicom to connect to /dev/ttyUSB3 and issued the 

AT!SELRAT?
it showed that it was set to ONLY connect to the 2g network.

So I issued an 
AT!SELRAT=03 

which tells the modem to prefer 3g but still connect to 2g when 3g is unavailable.

(it seems to retain this setting through disconnects from the computer as well)

More info about AT commands for the USBConnect can be found in this PDF [Supported AT command Reference Rev 21]("http://klamstwo.org/evad/wp-content/uploads/2007/05/2130617_supported_at_command_reference_rev_21.pdf")

Anyone else experience this?

---

### Post by rj_steinert on 2009-08-31
omg this worked out of the box my face is melting with techie bliss. support in core, see patch

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/306604](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/306604)

---

### Post by eksatx on 2009-11-25
I found that my USBConnect Mercury worked out of the box with Jaunty.

I am using Karmic now and things have taken a little step backwards.

The modem is always recognized and a connection is successful established.  The problem is that about half the time DNS does not work.  I can connect to sites by IP address, but not by name.

If I look at /etc/resolv.conf it just shows:

# Generated by NetworkManager

There is no nameserver entry.

I can usually get it to work if I disable wifi, pull out the 3g card, delete /etc/resolv.conf, then re-insert the 3g card.

I must admit that I haven't figure out the exact correct combination to get it to work every time -- it seems to be rather unpredictable.

Has anybody else experienced this?

Where can I start troubleshooting?

---

### Post by quincyglenn on 2009-12-09
I'm using Ubuntu 9.10 as well and have the same dns issue but other than that works right out of the box.

---

### Post by spyd3r0us on 2009-12-21
So I tried a couple of these methods and nothing got it working. It picked up the USB Mercury fine, and I was able to connect to the internet. I was only able to get to sites by IP address only, DNS was not working. 

I went into network connections and selected Mobile Broadband tab. Selected edit for my Connection name. Clicked on the IPV4 tab. Set the drop down to Automatic (PPP) addresses only and put in 8.8.8.8 (Google DNS server) and I am up and running. 

I made no changes to any config files. I left everything in the Mobile Broadband seetting tab as default, but I did try removing the APN and username and this method worked as well. and it took me about 20 mins to figure out. I am running Ubuntu 9.10 Netbook on a IBM Ideapad

---

### Post by witty68 on 2010-01-13
Only resolution I found was to modify the resolv.conf file after connecting and add nameservers such as 4.2.2.1 and 4.2.2.2.. Not sure why but the resolv.conf file is empty after connecting with Mercury USBConnect. Network Manager says it's connected so must be DNS issue, forcing dns entries fixed it temporarily.

---

### Post by pinoyboyf4i on 2010-01-28
> **spyd3r0us said:**
> So I tried a couple of these methods and nothing got it working. It picked up the USB Mercury fine, and I was able to connect to the internet. I was only able to get to sites by IP address only, DNS was not working. 

I went into network connections and selected Mobile Broadband tab. Selected edit for my Connection name. Clicked on the IPV4 tab. Set the drop down to Automatic (PPP) addresses only and put in 8.8.8.8 (Google DNS server) and I am up and running. 

I made no changes to any config files. I left everything in the Mobile Broadband seetting tab as default, but I did try removing the APN and username and this method worked as well. and it took me about 20 mins to figure out. I am running Ubuntu 9.10 Netbook on a IBM Ideapad

Thank you, this worked for me on 9.10 on a Thinkpad T60.  FYI in some cities I did not have to do this.

---

### Post by ionospheric on 2010-03-24
> **spyd3r0us said:**
> So I tried a couple of these methods and nothing got it working. It picked up the USB Mercury fine, and I was able to connect to the internet. I was only able to get to sites by IP address only, DNS was not working. 

I went into network connections and selected Mobile Broadband tab. Selected edit for my Connection name. Clicked on the IPV4 tab. Set the drop down to Automatic (PPP) addresses only and put in 8.8.8.8 (Google DNS server) and I am up and running. 

I made no changes to any config files. I left everything in the Mobile Broadband seetting tab as default, but I did try removing the APN and username and this method worked as well. and it took me about 20 mins to figure out. I am running Ubuntu 9.10 Netbook on a IBM Ideapad

Thanks, I am confirming that this solution works with Ubuntu 9.10. I like this solution because I can use the network manager applet from the notification area on the desktop.

---


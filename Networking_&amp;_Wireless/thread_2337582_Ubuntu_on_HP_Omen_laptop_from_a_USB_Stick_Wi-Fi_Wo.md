---
title: "Ubuntu on HP Omen laptop from a USB Stick Wi-Fi Won't Connect"
date: 2016-09-19
forum: Networking &amp; Wireless
---

### Post by slaveunit2 on 2016-09-19
Hello, all.


I am running Ubuntu on an HP Omen laptop from a USB stick.


On start-up, *Wi-Fi Networks* and *Wi-Fi is Disabled* appear grayed out when I click on the Wi-Fi logo the home screen.


Here's what I tried:
>`sudo rfkill list` 


Results in 
>`0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: acer-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no`


Then I do:
>`sudo modprobe -r acer_wmi`


and
>`sudo rfkill unblock all`


then
>`sudo rfkill list`


The line with *acer_wireless* disappears
>`0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no`


*Wi-Fi is Disabled* disappears.


*Wi-Fi Networks* is still there but is greyed out.


The *Create Wi-Fi Network* option when clicked and router info is punched in attempts to connect, but never connects.


Any assistance will be appreciated.  Thanks for your time.

---

### Post by wildmanne39 on 2016-09-19
Please do:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

If it does not connect click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by slaveunit2 on 2016-09-21
Hello, Wild Man.  Thanks for the reply.  'sorry about the delay.

It still wouldn't connect.

I did my steps + 

```
[COLOR=#000000][FONT=&amp]echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
```

I also tried
```
[COLOR=#000000][FONT=&amp]echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
```
for good measure.

I went ahead and ran your script which resulted in the attached tar.gz file.

Thanks for your time.

---

### Post by wildmanne39 on 2016-09-21
Did you reboot?

---

### Post by slaveunit2 on 2016-09-21
Yes.  Multiple times.  :(

Oh, and every time I reboot, it seemed like none of the script we put in to make it stick ```
echo...
```was there anymore.  I had to re-enter everything every time I rebooted.

Thanks.

---

### Post by Bucky Ball on 2016-09-22
Nothing will stick. You are running a 'Try Ubuntu' version from a USB installer. When you reboot, changes will be lost. Not sure why you're putting work into this when this is the case. Where's it going to save any changes to??? RAM, and that will be cleared on reboot.

You may have better luck on a full install to hard drive ...

---

### Post by Bucky Ball on 2016-09-22
Nothing will stick. You are running a 'Try Ubuntu' version from a USB installer. When you reboot, changes will be lost. Not sure why you're putting work into this when this is the case. 

You may have better luck on a full install to hard drive ...

Perhaps it might be better if Wild Man, if he knows, lets you know whether your wireless has any chance of working on a full install or if it would be better to invest in something that will work 'out of the box' in Linux.

---

### Post by wildmanne39 on 2016-09-22
His wifi should work fine and it should work in the live version but it has a softblock. 

When you say you have a usb stick with ubuntu I thought you meant you have a persistent usb stick did you create a persistent install or is it just the live usb version?

If it is persistent you need to run the wireless script again it following the directions on the page the link in my signature takes you to because the output as it is is in to bad of shape to make out.

---

### Post by jeremy31 on 2016-09-22
> **Wild Man said:**
> His wifi should work fine and it should work in the live version but it has a softblock. 

When you say you have a usb stick with ubuntu I thought you meant you have a persistent usb stick did you create a persistent install or is it just the live usb version?

If it is persistent you need to run the wireless script again it following the directions on the page the link in my signature takes you to because the output as it is is in to bad of shape to make out.

I think Bucky Ball is correct and the results were based on a Try without installing, live version as you called it as this is in the mangled script results
```
Parameters: file=/cdrom/preseed/ubuntu.seed, boot=casper, quiet, splash,
```

---

### Post by wildmanne39 on 2016-09-22
I thought he ran the script in the terminal one command at a time, I have seen such results when the person does that too, but yes I think he is correct.

---

### Post by slaveunit2 on 2016-09-22
Hello, all.  As you might have noticed already, I'm a newbie at this as anyone can be.  I really appreciate your assistance.

> [COLOR=#000000]Nothing will stick. You are running a 'Try Ubuntu' version from a USB installer. When you reboot, changes will be lost. Not sure why you're putting work into this when this is the case. Where's it going to save any changes to??? RAM, and that will be cleared on reboot. [/COLOR][COLOR=#000000]You may have better luck on a full install to hard drive ...[/COLOR]

Bucky Ball, I'm trying to learn to make websites with Ruby on Rails on my Windows laptop.  I have learned that that's like ramming a square peg into a round hole.  lol.  I read in forums that using Ubuntu is the way to go. Which is why I'm trying Ubuntu.  Now I'm trying to run it out of a USB stick because I'm afraid if I "run Ubuntu alongside" I might mess something up and wipe out/break my work in Windows.

> [COLOR=#000000]Nothing will stick. You are running a 'Try Ubuntu' version from a USB installer. When you reboot, changes will be lost. Not sure why you're putting work into this when this is the case. [/COLOR]
[COLOR=#000000]You may have better luck on a full install to hard drive ...[/COLOR]
[COLOR=#000000]Perhaps it might be better if Wild Man, if he knows, lets you know whether your wireless has any chance of working on a full install or if it would be better to invest in something that will work 'out of the box' in Linux.[/COLOR]

I was wondering about if work in the Try Ubuntu version will be saved.  This answered that.  Thanks!  

How risky with respect to the Windows side of my laptop is "running Ubuntu alongside"?

> [COLOR=#000000]His wifi should work fine and it should work in the live version but it has a softblock. [/COLOR]
[COLOR=#000000]When you say you have a usb stick with ubuntu I thought you meant you have a persistent usb stick did you create a persistent install or is it just the live usb version?[/COLOR]
[COLOR=#000000]If it is persistent you need to run the wireless script again it following the directions on the page the link in my signature takes you to because the output as it is is in to bad of shape to make out.[/COLOR]

Wild Man, what I did is I followed the ***How to create a bootable USB stick on Windows ***instructions from the Ubuntu website. Then, I restart the laptop with the USB stick plugged in and I select the first option which says something like "try Ubuntu".  I'm not sure what having a persistent USB stick means.

> [COLOR=#000000]I think Bucky Ball is correct and the results were based on a Try without installing, live version as you called it as this is in the mangled script results[/COLOR]
> [COLOR=#000000]I thought he ran the script in the terminal one command at a time, I have seen such results when the person does that too, but yes I think he is correct.[/COLOR]

What I did is I copied all the script and pasted it in the Terminal + ENTER.  Was that a right way to do it?

Again, thank you very much for your time, all.  I guess it all boils down to the question of should I continue chipping at this or should I run Ubuntu alongside ~ will I break my Windows and my files in it?

---

### Post by wildmanne39 on 2016-09-22
Here is a link for making a usb persistent bootable drive.
[https://usbubuntu.wordpress.com/make-it-persistent/](https://usbubuntu.wordpress.com/make-it-persistent/)
there are others if you want to look at more just google persistent usb pendrive.
> What I did is I copied all the script and pasted it in the Terminal + ENTER. Was that a right way to do it?No 
> If it is persistent you need to run the wireless script again it following the directions on the page the link in my signature takes you to because the output as it is is in to bad of shape to make out.
Until you have a persistent install or a dual boot there is no need to run it.

Any topic other then wifi is beyond the scope of this threads topic so if you need help with installing or creating a persistent pendrive please start a new thread in the appropriate section with a descriptive title, once you have done that if you still need help with wifi please post back.
Thanks

---

### Post by slaveunit2 on 2016-09-27
Hello, all!  It's fixed!  And all it was is that I had to do what Wild Man said, to make a [Persistent Bootable Ubuntu USB Flash Drive]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/"). 

Run Ubuntu from that.

Did this:
```
[COLOR=#000000]sudo modprobe -r acer_wmi[/COLOR]
```

Then punched in Wild Man's code:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

Voila!  Wi-fi running and changes saved even after restart.

Thanks, again!  You're all awesome.

---

### Post by wildmanne39 on 2016-09-27
Glad it is working!
Enjoy!

---


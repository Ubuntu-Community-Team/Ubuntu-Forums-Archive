---
title: "HP Wireless Assistant and Ubuntu"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Level1orc on 2009-12-18
So I just got Ubuntu last night, I'm working on getting it set up today.  I installed it to an HP laptop. 

When I tried to connect to the internet, I opened up Network Manager, and couldn't locate any wireless networks.  I noticed that my HP wireless assistant was off, so I tapped the button that turned it on--no result.

This always worked with Vista--do you have any idea how to pick up wireless networks/turn on the Wireless Assistant with Ubuntu?

Thanks in advance.  Please be patient with me, I'm still learning the basics--I've got a long way to go! :)

---

### Post by kestrel1 on 2009-12-18
If you go to System -> Administration -> Hardware Drivers
you may notice that there is a proprietry driver available for your wireless addaptor. You need to use an ethernet lead plugged in to your router to get an Internet connection, then enable the proprietry driver & this should be downloaded & installed, you should get access to your wireles networks then. Assuming that the wireless appears in the list.

---

### Post by coffeecat on 2009-12-18
It would help to know the actual wireless chipset in your laptop. Open a terminal (Applications > Accessories > Terminal) and post the output of:

```
lspci | grep "Wireless"
```

If you get no output, try this instead:

```
lspci | grep "802.11"
```

---

### Post by kestrel1 on 2009-12-18
> **cyndijw said:**
> Son was on his ubuntu and something happened, when we got it started back up, we had no internet connection, i've tried to find it but it keeps telling me that I don't have permission to access the terminal....don't know how that is possible, because I OWN it! How can it be reset to factory standards so that we can start all over again??? This is totally frustrating!!!!:confused::confused:
Can I suggest that you create a new post for this, as it will get answered quicker.

---

### Post by SlaughterDog on 2009-12-18
Level1orc: It sounds like you may need to install drivers. If none are automatically available for in the driver manager applet, figure out what kind of card you have, and see if you can find drivers on the Web.

---

### Post by electricFan on 2009-12-18
> **Level1orc said:**
> So I just got Ubuntu last night, I'm working on getting it set up today.  I installed it to an HP laptop. 

When I tried to connect to the internet, I opened up Network Manager, and couldn't locate any wireless networks.  I noticed that my HP wireless assistant was off, so I tapped the button that turned it on--no result.

This always worked with Vista--do you have any idea how to pick up wireless networks/turn on the Wireless Assistant with Ubuntu?

Thanks in advance.  Please be patient with me, I'm still learning the basics--I've got a long way to go! :)

With my HP laptop, pressing the switch turns the wireless on or off, but the light stays the same.  In other words the switch works but the light doesn't.  Sometimes it takes a minute or so for ubuntu to recognize that the wireless has been turned on or off after pressing the switch, too.  So you may find that playing around with the switch will solve your problem.  This is what worked for me hopefully it can help you too.

---

### Post by Level1orc on 2009-12-18
> **coffeecat said:**
> It would help to know the actual wireless chipset in your laptop. Open a terminal (Applications > Accessories > Terminal) and post the output of:

```
lspci | grep "Wireless"
```If you get no output, try this instead:

```
lspci | grep "802.11"
```

Here we go.  Output is:

02:00.0 Network Controller: Broadcom Corporation BCM4312 802.11 b/g (rev 01).

What's this mean, exactly?

---

### Post by Lupgaru on 2009-12-18
> **Level1orc said:**
> Here we go.  Output is:

02:00.0 Network Controller: Broadcom Corporation BCM4312 802.11 b/g (rev 01).

What's this mean, exactly?

That is your wireless adapter, Question, which Ubuntu did you install and what model HP Laptop? That would help.
    You stated tuning on the switch did nothing but as in one of the replies you might wait a minute or so for Ubuntu to catch on. I have had that problem before (Thinkpad and ACER laptops). My best results were with 9.04 on several different systems.
    Lately HP has been pretty good right out of the gate with Ubuntu. Hope it is just the switch.
Good Luck

---

### Post by Level1orc on 2009-12-18
> **Lupgaru said:**
> That is your wireless adapter, Question, which Ubuntu did you install and what model HP Laptop? That would help.
    You stated tuning on the switch did nothing but as in one of the replies you might wait a minute or so for Ubuntu to catch on. I have had that problem before (Thinkpad and ACER laptops). My best results were with 9.04 on several different systems.
    Lately HP has been pretty good right out of the gate with Ubuntu. Hope it is just the switch.
Good Luck
Thanks.  I'm using 9.10 on an HP Pavilion dv5 Notebook.

---

### Post by coffeecat on 2009-12-19
> **Level1orc said:**
> Here we go.  Output is:

02:00.0 Network Controller: Broadcom Corporation BCM4312 802.11 b/g (rev 01).

What's this mean, exactly?

Your wireless adapter is made by Broadcom. There's a minor issue with this in that the firmware can't be included in the default installation for licensing reasons. Have a look at this post:

[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)

To make simpler: you have a choice. Either download the b43-fwcutter package to install the firmware. When you install b43-fwcutter that in turn downloads the firmware, extracts it and copies it to the appropriate location in your system. The other alternative is to install the Broadcom STA driver.

But of course you can do neither if you have no internet connection. Catch-22. If you can connect your laptop to your router with an ethernet cable, do so. It will connect to the network automatically. Now open System > Administration > Synaptic and press the reload button. That will download up-to-date package metadata (information about packages and updates). Now close Synaptic and go to System > Administration > Hardware Drivers. Is that prompting you for the Broadcom STA driver? If so, try that. If that doesn't work, go back to Synaptic and install the b43-fwcutter package.

One or the other should get your Broadcom wireless working.

---

### Post by mrbomb on 2013-03-30
Hello, I just installed Ububtu 12.10 on My HP Probook 6570B and wireless is not working and the button stays orange. I do notice that Bluetooth turns on and off when pressed but no wireless. Any suggestions. Thank you

---

### Post by oldos2er on 2013-03-30
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---


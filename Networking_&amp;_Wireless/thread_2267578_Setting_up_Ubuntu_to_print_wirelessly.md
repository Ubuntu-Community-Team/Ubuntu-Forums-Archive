---
title: "Setting up Ubuntu to print wirelessly"
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by Jon_Lorton on 2015-03-02
Hi, I am a virtual novice with Ubuntu having been an increasingly dissatisfied DOS & Windows user for many years.  I am now determined to ditch MS products and switch to Linux/Ubuntu.  Before I bin my Windoze laptop I want to try and ensure I can do all I want/need to do with Ubuntu.  To this end I have set up an older laptop with Ubuntu 12.10 and using it is reasonably OK.  One thing I am unable to do however is to print wirelessly to my Canon MG6150 printer, something which I am able to do with my Windoze machine.

I have searched the web and a variety of Ubuntu forums looking for an answer to the question 'How do I setup wireless printing' with no success.  I have found a number of similar questions with incomplete or confusing answers but nothing to help me.

Can anyone give me a clear answer to my problem in simple terms, bearing in mind my lack of Ubuntu & Linux knowledge/experience.

Finally when I do take the plunge I will install Ubuntu 14.xx so if the process to install wireless printing under the current version is significantly different to 12.10 I would appreciate knowing what the differences are !

Thank you in advance.

---

### Post by jeremy31 on 2015-03-02
You might want to install 12.04 as 12.10 is now without support.  Current supported versions are 12.04, 14.04, and 14.10 
12.04 will be supported until 2017 and 14.04 is supported until 2019

---

### Post by ajgreeny on 2015-03-02
Can you print using a USB cable from your Ubuntu system? You must have the correct drivers for the printer in all cases and it does not matter if it is cable or wifi connected.

As jeremy31 says, 12.10 is not supported now so you should update in order to be able get updates to the system.  I suggest 14.04.2 as the best option.

---

### Post by chili555 on 2015-03-02
First, the driver for your printer exists in Ubuntu, at least in later versions, by default.

[ATTACH=CONFIG]260396[/ATTACH]

Next, there are three ways to use a printer wirelessly. First, you could have the printer attached to a computer on the network and print to it from any others. Second, the printer could be attached by USB to your router. Third, and I suspect this is your case, the printer could have wifi capability built-in.

If the latter is the case, I suggest you go into the administration pages of the router and determine the printers IP address. 

[ATTACH=CONFIG]260397[/ATTACH]

If you have the option to reserve the IP address used by the printer, please do so. For example: [http://screenshots.portforward.com/routers/Netgear/WNR2000v3/Address_Reservation.jpg](http://screenshots.portforward.com/routers/Netgear/WNR2000v3/Address_Reservation.jpg)

On your computer, find System Settings > Printers. Select 'Add new printer.' Then I would select Internet Printing Protocol. I would then use:

```
ipp://<IP address of printer>:631/lpr
```

You should then be asked for your printer's name; I suggest any name you and others on the LAN recognize; perhaps MG6150.

Test by printing a test page.

---

### Post by pdc on 2015-03-03
we aim to provide support on the ubuntu forum! 

chili555 has given you an excellent guide on setting up the wifi to your router;

to show you that the manufacturers aim to provide support, here is a link for UK Canon [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/) that lists the printers they sell; and how to connect the printer to the router;

they must not sell an MG6100 variant, but the MG6300 is described here [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mg6340_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mg6340_printer_wireless_connection_setup/) 

__________

this just gives you more information to choose from............personally I lack the enormous fluency in wifi that chili555 has ...........so the "press the WPS button" on the Canon printer.............and then "press the WPS button" on the router..........and invisible mating occurs wirelessly.............seems an easy way to my simple mind......................

---

### Post by tom195 on 2015-07-12
I am basically in the same situation as Jon_Lorton. Chili555, I think you may have solved this for me. My one question is about your first screenshot. Where do you find that list of printer drivers? I have Ubuntu 14.04

---

### Post by chili555 on 2015-07-12
> **tom195 said:**
> I am basically in the same situation as Jon_Lorton. Chili555, I think you may have solved this for me. My one question is about your first screenshot. Where do you find that list of printer drivers? I have Ubuntu 14.04I found the list when I set up a printer on my 15.04 system. After you specify the URI, the system searches for drivers. You are asked for the manufacturer; in this example, we used Canon. After selecting Canon, or any other manufacturer, you are offered a list of models from which to choose.

The available models and drivers may be included in 15.04 but not the earlier 14.04 version.

---


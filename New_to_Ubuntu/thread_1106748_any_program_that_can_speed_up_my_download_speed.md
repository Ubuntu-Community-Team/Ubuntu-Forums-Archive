---
title: "any program that can speed up my download speed?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Rockanium on 2009-03-26
its been running quite slow, and i would like it to go fster :D

---

### Post by linuxuser21 on 2009-03-26
A Firefox extension called Down Them All! is supposed to make it a lot faster.

---

### Post by Rockanium on 2009-03-26
no not just for firefox, for everything els aswell

---

### Post by lisati on 2009-03-26
Slow download speeds can be cause by a number of things, from busy servers,  through network congestion, and all the way to an ISP providing a bad connection speed. Sometimes BitTorrent processes (and similar) can alleviate the problem a little by spreading the load across different sources.

---

### Post by lisati on 2009-03-26
I found the following information at my ISP's [website]("http://telecom.custhelp.com/cgi-bin/telecom.cfg/php/enduser/std_adp.php?p_faqid=1299&p_created=1192068088&p_sid=8WfbBJtj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD0xNDUsMTQ1JnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWJyb2FkYmFuZCBzcGVlZA**&p_li=&p_topview=1&p_prods="):

> The stated speed of your plan is the maximum possible connection speed at which you can access the Internet.

There are several factors that can effect the maximum speed you can receive:

    *       The distance you are from your local phone exchange will effect your maximum connection speed.
    *       The wiring of your premises - Both the length and quality of any wiring in your house or office can affect maximum connection speeds
    *       Your computer - Your computer and modem or router will also affect the maximum speed of your broadband connection
    *       Your modem connection - How you connect your modem to your computer will effect your connection speed. For example, an Ethernet or Wireless connection is generally faster than a USB connection.
    *       Measures to enhance the overall stability of the network

More generally, the day-to-day speed of your broadband connection can also be effected by the following:

    *       The time of day - If you log on during busy periods when lots of people are using the Internet at the same time (usually between 4pm to midnight) speeds are likely to be slower.
    *       The websites you visit - Some websites limit the speed at which they send out information and sites that are further away (i.e. international) can be slower to download than sites hosted in New Zealand.
    *       Sharing your connection - More than one person using the same connection in your home or office can slow speeds.
    *       The application(s) you are using - Some applications may use all of the spare bandwidth or memory on your computer. You can check if this is the case by turning off each application that you might be using and then checking your speed again. Make sure you turn off any anti-virus software before you do this.
    *       Viruses and spyware on your computer - Your computer may have been infected by viruses or other unwelcome programs like Spyware. If you have anti-virus or anti-spyware software, make sure the software is up-to-date and that you run regular scans of your computer. Alternatively, you can run a free scan of your computer at Telecom.co.nz/security

Some potential options to improve the speed of your broadband connection

While some factors affecting connection speeds are outside your control, there are a number of things you can do in your home or office which can help get the best connection that's available:

    *       Use an Ethernet or Wireless modem - they generally connect faster than a USB modem.
    *       Check that all of the phone jackpoints you use and any devices needing a phone line (such as a burglar alarm) have broadband filters installed. Empty jackpoints won't need a filter.
    *       Get a splitter installed. This will separate your broadband connection from your phone line.
    *       If you can, use the most up-to-date computer and operating system.
    *       Avoid using long phone extension cords as these can slow the broadband speed on your phone line. Where possible, plug your modem into the main phone jackpoint.
    *       Regularly scan your computer for spyware, adware and viruses as these can all slow your connection speed. Visit Telecom.co.nz/security for more information.
    *       If you have a plan with a monthly data cap, check your monthly usage to make sure your connection has not been slowed to dial-up speeds.
I also found the following at [www.consumer.org.nz:](www.consumer.org.nz:)
> What can affect your broadband speed?

Broadband speed is affected by a number of variables, including:

    * What plan you're on: Your ISP can limit the speed available to you.
    * How many users are sharing the copper wire to a phone exchange and how far you are from an exchange: ADSL broadband slows down when more people are sharing a cable. The cable leading from your home to the telephone exchange can only transfer so much data at a certain speed. The more people using that cable and the more data they're trying to move, the slower it becomes. Think of it like a motorway - at 5am when the roads are empty, you can drive along at a good pace, but at 5pm when everyone wants to use the road - gridlock. The same happens with ADSL broadband.
    * The amount of traffic at a website and the amount of traffic with that ISP: The same slowing-down process happens at websites. If everyone tries to access one website at the same time, the cable can't handle the demand and sometimes the website will not be accessible ('crash'). If you're surfing the web, some websites of the same size will load faster than others because they're not so busy.
    * Your computer setup: If you have an old computer and/or it's setup inefficiently this can slow things down e.g you only have a tiny amount of free memory and your computer is forced to use your hard disk to store temporary data which slows things down significantly.


---

### Post by albandy on 2009-03-26
d4x
sudo apt-get install d4x

---

### Post by vasco.debian on 2009-03-26
hi

may try axel

sudo apt-get install axel

---

### Post by jerrrys on 2009-03-26
what kind of service do you have? DSL? Dialup? find out what speed your ISP
is providing and then check it against one of many internet speed test you can google. let us know the results...

---

### Post by starcannon on 2009-03-26
If your on a NAT router/modem provided by your ISP, and then pumping that into another Router, like Linksys or Netgear or etc..., you may be experiencing collisions; be sure to turn NAT off on your router/modem provided by your ISP and set it to Bridged mode, and let your Linksys, Netgear, or whatever router you may have in series do the NAT.

Just throwing that out there, as I see it being a common mistake that all of my home users make. 

GL

---


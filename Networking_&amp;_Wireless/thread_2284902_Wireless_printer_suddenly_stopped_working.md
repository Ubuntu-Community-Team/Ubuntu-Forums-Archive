---
title: "Wireless printer suddenly stopped working"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by JessicaNumber on 2015-07-02
I can't find any reference for a similar problem, I hope it's an easy enough fix or someone can direct me to troubleshooting!

Background:
Ubuntu 12.04 on HP Pavilion 15 
Basic wireless modem/router 
Brother HL-3170CDW

These guys have been talking to each other perfectly without a single issue for several months since I brought it home. It's already turned over its starter black toner a while back. Today: It printed a couple of pages, ran out of yellow, printed a couple of pages, ran out of magenta, printed a couple of pages, ran out of cyan, finished the job and disappeared from the network. 

The error message received is unable to reach/locate printer (I get a slight variation depending on which program I ask).

I've power cycled the printer. No change.

I've reset the wireless connection on the printer, basically manually reconnecting to the network. It was able to see the ssid and stated that it had connected properly but still not working. I can send a job to the printer but then a few moments later it decides it can't get the message through.

I've rebooted the notebook and power cycled the router. Still, I can select the printer, cups says it's online, print dialog says it's online, but as soon as I send a job to it, it's offline.

I'm using the same router to do this post so it seems to be working OK.

I've then reinstalled the printer. Using the wizard I'm able to find the printer on the network and then install the appropriate drivers manually (this was always the case) and send a test page. I'm no longer seeing an unable to reach printer error but the message is getting through at nearly zero speed. A simple test page has got to 6% complete after 25 minutes. 

It's a reasonably secure network in a quiet suburban street and I'm not aware of any new wireless devices having entered the house.

UPDATE I'm also having an error with pkexec. I can't even begin to imagine how these things are related to each other but it was weird so I thought better chuck it in.

---

### Post by JessicaNumber on 2015-07-02
Running update manager.

---

### Post by JessicaNumber on 2015-07-02
SOLVED

This rare printer model comes from OfficeWorks in Australia which has a reputation for slapping a new model number on a printer and changing the price. Not sure if this is the case here but I was able to connect beautifully over USB using the 3170CDW driver and then rebuilt the printer using the 4070CDW driver for a fantastic connection and quick print.

---


---
title: "Asus | WL-500g Premium | Wireless Router | Install &amp; Connection on the ADSL Modem"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by oxigen on 2007-09-01
Usually I can find answers on this excellent Ubuntu forums, but when I tried to connect my new wireless router I just couldn't find answers on my basic questions. So, I called my buddy...

I hope that you will find this post useful, and please add some other useful tip or info about **Asus WL-500gP Wireless Router** if you have some. I can share with you only basic stuff for now...

OK, you receive with the router also the manual, but not for the Linux. As I said, googling didn't work for me and connecting router on **ADSL Modem** also didn't work out of the box. :confused:

Here are my steps which successfully connected the router to the modem and the computer to the router:

[LIST]
[*]**Switch Off** the computer, the modem and the router *(in any case)*.

[*]Connect the (patch) cable from the modem to the router's **WAN Connector**.

[*]Connect the (patch) cable from the router's **LAN Connector **(1, 2, 3 or 4, in my case 1) to the computer's **Network Connector**.

[*]**Switch On** devices.
[/LIST]

OK, if are router's lights on (power, WAN, LAN and maybe AIR - *if you have some wireless signal from your neighborhood*) then you are ready for the next steps...

Now open terminal and write shell commands:

> $ sudo dhclient
$ sudo ifconfig

With this commands you will get status of the currently active interfaces, so you must find your new local IP adress from this info (inet addr), in my case was 192.168.1.**1** (it's important that is nr. **1** on the end!)

Now open your favorite browser, (Firefox on example) and go to the url of your local IP adress:

> [http://192.168.1.1](http://192.168.1.1)

If everything went OK, then you will be able to see interface for setting your router in your browser.  There you can set many things, here are some basic settings:

[LIST]
[*]**Quick Setup** - select time zone, set connection type, set ISP account (username & password) and  configure wireless interface. After pressing button "Finish" you will be able to browse the internet!
[/LIST]

OK, this is basic connection setup. Here is another tip: 
By default you have all ports closed from outside access, so if you have Apache or some other web or ftp server you will need to open port 80 (http), this you can set in "NAT Setting - Virtual Server" menu. There you will need to enable virtual server and insert your **local **IP adress *(use ifconfig, in my case is: 192.168.1.2)*; Port Range *(in my case: 80)*; Local Port  *(in my case: 80)*. Press "Add" button, save configuration and that's it! Thanks Luka! :)

---


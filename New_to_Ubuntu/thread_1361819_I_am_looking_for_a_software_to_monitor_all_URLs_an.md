---
title: "I am looking for a software to monitor all URLs and requests made by a softare"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by legolas_w on 2009-12-22
Hi
I am looking for a softwre which can show me which which requests are place by my browser and let me search in the logged urls and possibly filter them to find specific informations.

Is there something like that available either as firefox plugin or ubuntu application?

Thanks.

---

### Post by dingletec on 2009-12-22
If you don't mind using the command line (super fun), urlsnarf might be what you are looking for.  It comes with the dsniff package, so from the command line:

sudo apt-get install dsniff

to use:

sudo urlsnarf -i eth0

Ctrl-c to exit.

---

### Post by bodhi.zazen on 2009-12-22
Have you looked at using a web proxy ? Several options, everything from squid to a web debugging proxy to firefox addons

[http://livehttpheaders.mozdev.org/screenshots.html](http://livehttpheaders.mozdev.org/screenshots.html)

livehttpheaders is in the ubuntu repositories.

[http://packages.ubuntu.com/karmic/mozilla-livehttpheaders](http://packages.ubuntu.com/karmic/mozilla-livehttpheaders)

---

### Post by dingletec on 2009-12-22
It occurred to me that some people would prefer to use a GUI app for this, so another option is Wireshark (Ubuntu 9.10)

Search for and install Wireshark from Application -> Ubuntu Software Center

Your basic user doesn't have sufficient rights to open a network interface in Wireshark, so you will need to run it as root, which it will complain about.

Use Alt-F2 to bring up the "Run Application" dialog.

type in: gksudo wireshark

enter your password

Once Wireshark launches, you will choose the interface you want to monitor (ex: eth0). Enter http in the Filter text box and hit enter. If you click on each of the packets, you can expand the "Hypertext Transfer Protocol" drop down below to get at the info you are looking for.

---

### Post by legolas_w on 2010-01-04
Thank you all for your helps. I am using wireshark in combination with live http headers extension for firefox

---


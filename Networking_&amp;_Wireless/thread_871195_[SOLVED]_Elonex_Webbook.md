---
title: "[SOLVED] Elonex Webbook"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by mollyj on 2008-07-26
I'm new to UBUNTU but have been using Mandriva for a couple of months as it was on the cover of a mag.
Any one know anything about the Elonex Webbook. I bought one of these today without the 'orange' contract from Carphone warehouse as the price seemed good for the 'spec' and I've been looking at ultramobiles for a while.
However I can't seem to get the wireless working
The network manager has 'enable wireless' greyed out.
having gone through the 'troubleshooting' steps I have determined that the hardware lists an Intel wireless device there in the machine
Using lscs -C network tells me the lan is there and working but the wireless appears to be disabled with an ominous 'radio=off' and almost every other parameter zeroed.
The man in the shop didn't say anything about wireless being disabled if you didn't sign up with 'orange'.
Can anyone shed any light on the matter.

---

### Post by mollyj on 2008-07-27
solved this one :redface: the answer is easy as I was looking for the complex solution when there was a simple one. There is a 'soft' hardware key to enable/disable the wifi hardware fn f1.

---

### Post by mollyj on 2008-07-27
Me again; is there a record for talking to oneself?. Still this might be of use to prospective buyers of the Elonex. Warning:The machine sold by carphone warehouse comes with a 'four' page 'manual':rolleyes: and nothing else. It doesn't even mention the hardware lan in the description never mind the operation of the soft keys. The Elonex website appears to deny all knowledge of the machine and redirects you to the carphone website where you can get 'help' at about £10uk/ month.

---

### Post by codfather on 2008-07-29
I just noticed these being given away for free by the carphone wharehouse if you sign up to their 3G service. I was more interested to know what Ubuntu runs like on this box. 

Apart from your minor wifi issue, what is your overall experience like with the unit now you have it up and running. Did you get the 3G card working with Ubuntu?

Cod

---

### Post by Alan Bell on 2008-07-29
press alt+F2 to get the run program dialog
type in
gksudo gedit /etc/modprobe.d/options

add a line at the end and type the following

options ipw2200 led=1

this tells the wireless driver that it is also responsible for turning on and off the LED. Normally this should flicker every few seconds when active, it will be on constantly when associated with a hotspot.

Later models will have this set by default, unfortunately the first batch escaped without it.

There will be more information about the webbook at [http://webbookblog.com](http://webbookblog.com) and there will be some people monitoring these forums too.

---

### Post by oceanpink on 2008-07-31
Hi I am also having problems with the webbook wifi led light. I followed the instructions but still no light comes on when i tried to repeat the steps again with gedit, just a plain page comes up. is there a plugin i can download that can fix this wifi problem and how do i get files to show in gedit as i have had this problem when trying to configure the huawei e220 modem.

---

### Post by Alan Bell on 2008-07-31
I think if gedit is running but not loading a file then you are typing the file name wrong somehow. Did you put the dot in modprobe.d? When gedit is running you can go to file-open and browse the filesystem to go to the top level then open the etc folder then the modprobe.d folder then open the options file.
Configuring the E220 is a little more complex and uses different software to the Orange Icon 225. I will do a post on the webbookblog.com site on how to load the new dialer software and get all sorts of dongles working with the webbook.

---

### Post by mollyj on 2008-07-31
Alan: Thanks for the tip about the LED. 
Codfather : I didn't take up the 3G option I bought it as the plain machine. Overall my first impressions of the webbook are positive.The few 'extra' applications I've put on seem to work with the exception of one which is graphics intensive and I think this has something to do with the display not being 1024 by 768 but 1024 by 600. Otherwise I've not had a lot of chance to play.
Alan: One thing I've noticed: the system appears to have a couple of 'phantom' users 'hso' and 'root'. 
I noticed from your posts on the blog that there is a 'recovery' screen that gives you access to 'root' to reset stuff. This seems like a good idea and so I can understand why you might want one of the phantoms....... Does this have any security implications as the 'recovery' screen doesn't appear to need a password?. 
HSO doesn't have a home directory is it something to do with the hardware?

Sorry to be always asking questions but it's the only way I ever find anything out. One day I might get to know enough to provide a few answers.

---

### Post by Alan Bell on 2008-07-31
The hso user is indeed a bit of a phantom. We were trying to get the Orange broadband client to automagically launch when you insert the option 225 dongle. This turned out to be rather tricky because udev rules run as root but we didn't particularly want it running as root so we created the hso user for it to run under. We did lots of messing about with udev rules and things to try to get it working but in the end we gave up, we couldn't do it securely so we decided not to do it at all. You can leave the hso user or delete it, it doesn't matter. The existence of the root user is normal in Ubuntu. The user exists, but without a password so you can't directly log on as root.

---

### Post by Alan Bell on 2008-07-31
oh as for the recovery screen not having a password, indeed it doesn't. If you want a password on it (and if you promise not to come crying to me when you forget it:)) then you can type "sudo passwd root" at a terminal to set a password for the root user which you will then be asked for when going to the recovery mode console.

---

### Post by oceanpink on 2008-08-01
Alan: thank you for your help. my wifi led is now active. will be reading ur webbook blog for guidance as you write with easy to follow steps. well done and keep up the good work

---

### Post by mollyj on 2008-08-01
Alan: It's not that essential for me to have a root password for the recovery screen but I have noticed that certain utilities e.g. hardware tester for example requires access via a sudo command and when I type in my 'first user' password (the one with administrative privileges) it says that it isn't valid and then bombs with a message that says I need the 'root' password. 
ps. Does the webbook support Bluetooth? (there's a function key) and does it have a webcam? There's a tiny hole where you'd expect one to be. I'm unused to Ubuntu and can't find the equivalent of the hardware lister that performs beautifully and I've found essential on my Mandriva system which is based on an older machine and necessarily has had hardware add ons.

---

### Post by monkeynuts84 on 2008-08-14
> **codfather said:**
> I just noticed these being given away for free by the carphone wharehouse if you sign up to their 3G service. I was more interested to know what Ubuntu runs like on this box. 

Apart from your minor wifi issue, what is your overall experience like with the unit now you have it up and running. Did you get the 3G card working with Ubuntu?

Cod

Codfather - is your name Nick?

The 3G works fine. I've done a review of the web book here - 
[http://midbuyer.co.uk/elonex/orange-web-book-review/](http://midbuyer.co.uk/elonex/orange-web-book-review/)

---


---
title: "Firefox wont start"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by kingvik on 2007-06-12
just to let you all know I'm a noob at this. I just installed Ubuntu and the installation went smoothly, and everything is working fine but Firefox. It shows that I'm connected to my network but I keep on getting a pop-up  that asks for my password, so I keep entering it. When I try to open Firefox the cursor turns into the circle and looks like it's loading but then it just stops and nothing has happened. Please Help.

---

### Post by dmizer on 2007-06-12
open up a terminal and type:
```
firefox
```
hit <enter> and it should send an error to the terminal.  past the error here.

---

### Post by Vola on 2007-06-12
check if you have locks on your profile

in the folder:

/yourhomedir/.mozilla/firefox/xyzsomeprofile.default/

if you found a    lock    and/or  .parentlock   file, delete them and try to restart firefox.

note that .parentlock and .mozilla are hided files, display them with ls -al

---

### Post by kingvik on 2007-06-12
after typing "firefox" in the terminal i got this 
"Segmentation fault (core dumped)"

---

### Post by kingvik on 2007-06-12
I have now gotten it to connect to the network and now GAIM is working, it hadn't been working. But Firefox still wont start.

---

### Post by pardesi on 2007-06-12
open a tab in firefox and write 

```
about:config
```
and then go to 

```
network.dns.disableIPv6
```

change it's value to true if it's false.


it's very unlikelt that u have a problem due to IPv6 ...but give it a try:)

---

### Post by kingvik on 2007-06-12
Thank you everybody for all your help. I just changed my network from being password protected for now and then I was able to connect to my network but Firefox still wouldn't open but after installing updates it works now.

---

### Post by tgalati4 on 2007-06-12
sudo killall firefox-bin
firefox


Sometimes the firefox-bin program is left behind and a new instance of firefox won't load as a result.

---


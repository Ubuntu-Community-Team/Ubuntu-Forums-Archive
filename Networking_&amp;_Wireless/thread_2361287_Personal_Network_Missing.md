---
title: "Personal Network Missing"
date: 2017-05-14
forum: Networking &amp; Wireless
---

### Post by vandog2 on 2017-05-14
Hello everybody.

First of all I'd like to thanks the community for your work and the support.

I just installed Lubuntu on my netbook and I can't find my personal network.

Every other network appears, even the ones far away.

But when I go to "Edit Connections", on the "Network Connections" window, my network shows on the wi-fi section.

Is there any configuration that I have to do? If so, i there any link that I can go?

Thank you in advance

---

### Post by wildmanne39 on 2017-05-14
*Thread moved to **Networking & Wireless**.*

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by vandog2 on 2017-05-16
First of all, thank you for your help.

It was this that you were talking about?

[http://paste.ubuntu.com/24588196/](http://paste.ubuntu.com/24588196/)


My network still doesn't show

---

### Post by wildmanne39 on 2017-05-16
Please do:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot, if you do not know how to run the above commands just ask.
Thanks

---

### Post by vandog2 on 2017-05-16
Ok, I realised I don't know how to run that because nothing happened. It just changed to the root "directory"

---

### Post by wildmanne39 on 2017-05-16
After sudo -i did you enter you password? after that you just copy and paste one line at a time and hit enter until you have done that for all lines.

You will not se3e any messages in the terminal unless the command fails.

If you ran them all and did not see any messages all you need to do is reboot and the changes should take effect.

---

### Post by vandog2 on 2017-05-16
Ok. So after your last message, I done it again, one at the time. After the "exit" command it just said "logout" and I reboot the pc. But nothing appear to have changed. my network still don't show.

Can it be something with the router channels?

---

### Post by wildmanne39 on 2017-05-16
Please post a new file from the wireless script and we will make sure the changes took effect and we will check the settings in the router.
Thanks

---

### Post by vandog2 on 2017-05-16
This is the new link

[http://paste.ubuntu.com/24588405/](http://paste.ubuntu.com/24588405/)

---

### Post by wildmanne39 on 2017-05-16
You are connected to this nietwork NOS_WIFI_Fon that is not yours? if not what is the name of yours? it has no security enabled.

---

### Post by vandog2 on 2017-05-16
No, that's a public wi-fi. Mine is "Alkemist"

---

### Post by wildmanne39 on 2017-05-16
Go into your router and make sure wifi is enabled then save and reboot router, go into network manager and remove your network connection, after the router reboots reboot your computer and see if network manager finds your network. Also you need to use channels 1 thru 11

When did it stop working, what was the circumstances? I am going to be gone for a little while, I will check on you as soon as I get back.

---

### Post by vandog2 on 2017-05-16
Not sure if I can get into router because it's from the ISP and I belive it's locked. 

I just installed Lubuntu in my netbook and when I tried to connect my network was missing in the list. I don't have this issue on windows nor any other device (smartphones).

No worries You already helping a lot. Thanks

---

### Post by vandog2 on 2017-05-16
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8568109e-8aa1-4845-bf19-45284a488852 | **Alkemist**
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0baa5cfc-8084-4b2d-84a7-2aa166eac808 | NOS_WIFI_Fon

See, it's listed as available but doesn't show in the list

---

### Post by wildmanne39 on 2017-05-16
Did you reboot your router, then remove connections from network manager and reboot computer?
Thanks

---

### Post by vandog2 on 2017-05-17
I had some work to do and forgot to answer.

I manage to get into the router settings and change the channel. THAT was the problem! 

As soon as I changed to 11 the networked appeared right away. I felt so stupid!

Thank you so much for your help and sorry for the annoyance!

Cheers

---

### Post by wildmanne39 on 2017-05-17
In the beginning you had more then one thing going on, the commands you ran in post 4 removed an extra driver that would have caused very bad connection issues if you could connect at all.

Glad it is working.
Enjoy!

---


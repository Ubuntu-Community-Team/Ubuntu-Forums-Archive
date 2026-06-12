---
title: "how to connect to internet at my graduate school"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by ThoseTimesAreGone on 2013-10-02
Hey everyone. I have ubuntu 12.04 LTS. I can connect to internet at home just fine. However at my school Authentication is required and I was unable to connect last time i tried. Is there any special procedure of how to connect to these kinds of networks?

Here is what the school site says:

network authentication: WPA2

Data encryption AES

Authentication type: Protected EAP (PEAP)

PEAP Properties: secured password  (EAP-MSCHAP v2) 
Enable fast reconnect: Checked. 



Any ideas?

---

### Post by TheFu on 2013-10-02
Wired or wireless?
Are the notes above YOUR settings or what the school says is required?

---

### Post by ThoseTimesAreGone on 2013-10-02
On windows 7 the connection process is automatic and no configuration is needed.

On ubuntu 12.04 LTS  even after i enter my username and password it will not connect. I did not alter any settings so far.

What i wrote in my first post is what the school's guide is telling people to use who are still on windows XP. There is no guide for later versions b/c it works automatically.

And its wireless of course.

---

### Post by TheFu on 2013-10-02
What do the log files show?  /var/log/*
The IT group should have manual instructions available for others, but it is possible they only test with Win7/8 and don't worry about compatibility for other OSes.

BTW, lots of businesses only support 1 VPN tool, so anyone using any other solution is SOL.

---

### Post by Hadaka on 2013-10-02
Hi,please read post #6 and #7 at this thread..
[http://ubuntuforums.org/showthread.php?t=2176854](http://ubuntuforums.org/showthread.php?t=2176854)
hopefully this helps.

---

### Post by ThoseTimesAreGone on 2013-10-05
> **Hadaka said:**
> Hi,please read post #6 and #7 at this thread..
[http://ubuntuforums.org/showthread.php?t=2176854](http://ubuntuforums.org/showthread.php?t=2176854)
hopefully this helps.

thanks for trying to help! I tried this method but ca=cert is nowhere to be seen. Also, installing that .deb file only gave me errors and the system demanded I Uninstall it. Here is what the output showed... any ideas?

[http://imageshack.us/photo/my-images/706/rah7.png/](http://imageshack.us/photo/my-images/706/rah7.png/)

---

### Post by varunendra on 2013-10-05
> **ThoseTimesAreGone said:**
> thanks for trying to help! I tried this method but [COLOR="#FF0000"]ca=cert[/COLOR] is nowhere to be seen. Also, installing that .deb file only gave me errors and the system demanded I Uninstall it. Here is what the output showed... any ideas?

[http://imageshack.us/photo/my-images/706/rah7.png/](http://imageshack.us/photo/my-images/706/rah7.png/)

Actually the string to look for is "system-ca-certs=true", but I can see in the screenshot that even that does not exist (at least not in the key files that you checked in the screenshot). Please show us the outputs of -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
nmcli con
```

There will be no sensitive data in the above outputs, so please don't over-edit them (edit or obscure your user ID if you wish, although it is clearly visible in the screenshot ;)). Depending on these outputs, I may ask for more outputs specifically related to your school connection or overall system config.

**PS:**
And you shouldn't try installing any packages without understanding what they are for and whether they are required/suitable in your system or not.

---

### Post by ThoseTimesAreGone on 2013-10-09
Hi !

Thanks for your help. it took a while to get the output you wanted b/c i wasnt in school for 4 days. The connection That doesnt work is the one i blotted out in white that has the "M" next to it.

[http://imageshack.us/f/21/hunz.png/](http://imageshack.us/f/21/hunz.png/)

the connection "lith-uan-ian cha-mps" is what i use at home and that is the one that works well. Both of the guest accounts work sometimes and they also belong to the school. 

What do you think?

---

### Post by varunendra on 2013-10-10
Could you please explain the reason for that much 'censorship'? Sorry but I'm not comfortable with that and I believe I may not be able to help with that much 'hiding' of data, even if I wish to.

Most of us here, including me already take enough care to suggest the user to obscure or delete sensitive data if any is possible to show up in any output.

For now, I was expecting to see the exact name of your connection so that I could suggest you the exact command to check your 'key-file' for the connection. But anyway, you may try this -
```
sudo cat /etc/NetworkManager/system-connections/<whatever is the name with "M" next to it>
```
..and see if the "system-ca-certs=true" line exists. If not, you may have configured it improperly.

Note that the CA certificate can be "Ignored" for this type of connection, but is highly recommended. Since it is a school network, I doubt they don't have one. If they have, it may be what is preventing you from connecting to it. Usually, it is a file given to you by school authorities, which you add by clicking at the 'browse' button in front of "CA Certificate" field in the security settings of the connection, as shown in the screenshot below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246854[/IMG]

If everything is fine on that part, then I would ask you to run a script (from the "Wireless Script" link in my signature) and post its output, but then it may be too much trouble for you cuz it would contain too much data to be censored ;) (and may be useless for me 'After' the censorship).

---

### Post by ThoseTimesAreGone on 2013-10-10
Thanks for your help as always. I PMed you regarding the censorship. I will try to do my best to follow your steps and will post the output as soon as i can.

---

### Post by varunendra on 2013-10-10
Yep, read and replied your PM. No problem with editing out the SSID alone. Let me know (here or in PM) if you have doubts about anything else. We all respect anonymity of users. :)

---

### Post by ThoseTimesAreGone on 2013-10-15
So i am going to try to run the commands tomorrow. Looking at the connections tab I can tell you that PEAP was not enabled. Still, I do not have the CA-certificate but i know that the school requires one.

I looked at all other OS (xp/vista/7/8/ OSX)... Uppon attempt to connect the certificate is offered the user. But i as a ubuntu user do not get this certificate. Is there any way to obtain it like everyone else does? No other students have had to add it manually, it just works for them. Is there anyway for ubuntu to grab that certificate?

EDIT: SOLVED. i cant believe it but all that was needed was to change the connection type from "Tunneling" to "PEAP" in the drop down menu. 

Thanks!

---


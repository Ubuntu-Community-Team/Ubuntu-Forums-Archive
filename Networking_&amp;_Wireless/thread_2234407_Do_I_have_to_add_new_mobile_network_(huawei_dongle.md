---
title: "Do I have to add new mobile network (huawei dongle) every time I start Ubuntu?"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2014-07-14
So I have Ubuntu 14.04 (dual boot with Windows Vista) installed on my Dell Inspiron 1720 laptop...I'm using Flashback session...for internet access I use Huawei dongle with sim card, connected to usb port on my laptop. When I start Ubuntu I manage to establish my internet connection by going to System Settings/Network/Mobile network/Add new network - and I have to insert all data about my country, my internet provider,... Finally I save my new connection.

Internet works ok, but when I shut down or restart Ubuntu and start it again there is no trace of my previously saved mobile connection...I have to manually add new connection again. Is this supposed to be that way or is it possible to permanently save mobile connection or shorten procedure of adding new connection?

---

### Post by Chesslover on 2014-07-16
Anyone?

---

### Post by yancek on 2014-07-16
Your changes should be saved.  The behavior you are describing would be expected if you were running Ubuntu from a Live CD/DVD or from a flash drive created with unetbootin, pendrivelinux or similar software.  Same behavior if you did a frugal install to your hard drive.  If you did an actual full install of Ubuntu to a separate partition on a hard drive, something is very wrong.

> .I'm using Flashback session

I don't know what you mean by that term but, if you are using a flash drive created with software similar to what I mentioned above, then nothing is saved on reboot because it is a Live CD and than means read-only filesystem.  Please clarify the type of install.

---

### Post by Chesslover on 2014-07-17
I did a full instal of Ubuntu 14.04 on separate partition...plus I instaled gnome-session-flashback which I use instead of Unity. So you think the system should save my network? because it's pain in the ass constantly adding new mobile network...

---

### Post by h.hittini on 2014-07-17
If you can configure it using the terminal, I have a way in mind
You can type the commands in this file /etc/rc.local
And they are gonna be executed every the laptop starts

---

### Post by Chesslover on 2014-07-17
How exactly can I do that?

---

### Post by h.hittini on 2014-07-17
> **Chesslover said:**
> How exactly can I do that?

Give me the exact steps and options you use, I'll try to find the CLI equivalent commands

---

### Post by Chesslover on 2014-08-03
I don't use terminal...I go to system tools, system settings, network, mobile broadband...there should be stored the mobile connection from my last time, but it's not...when I click on the field "connection" I get just option "add new connection" and I have to manually add it again...and next time I start ubuntu again...and next time again

I'm sure this is not supposed to work in such way...

---

### Post by h.hittini on 2014-08-03
Try the solutions mentioned here [http://askubuntu.com/questions/137815/how-to-enable-disable-mobile-broadband-from-terminal](http://askubuntu.com/questions/137815/how-to-enable-disable-mobile-broadband-from-terminal)

---


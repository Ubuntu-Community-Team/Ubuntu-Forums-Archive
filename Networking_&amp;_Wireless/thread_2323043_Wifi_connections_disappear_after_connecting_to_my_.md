---
title: "Wifi connections disappear after connecting to my wifi network"
date: 2016-05-02
forum: Networking &amp; Wireless
---

### Post by Sid_Smith on 2016-05-02
[COLOR=#111111][FONT=Ubuntu]I am creating this post from a windows machine. Installed ubuntu 16LTS after erasing 12 LTS. Ubuntu 16 fails to connect to my wifi network. Then, the whole wifi symbol (and all the connections) disappears without any error message. Please tell me how to fix this.[/FONT][/COLOR]

---

### Post by RobGoss on 2016-05-02
Hello and welcome, When you first installed **Ubuntu 16.04** I'm assuming this is the correct version you're talking about, were you connected to the internet with a wired connection? 

And was your machine making a connection at all?

It's important you provide us with the specs for your machine in order to give you the help needed to get you connected

You can try connecting your machine using a **wire connection** and then open up **Software & updates **and choose **Additional Driver **Option this will scan to see what available drives are needed

---

### Post by jeremy31 on 2016-05-02
Please see the wireless-info link in my signature and use the code tags when posting the info.  There are a lot of reasons that this can happen

---

### Post by Sid_Smith on 2016-05-03
My machine was trying to make a connection, but failed. There is no ethernet port on my linux laptop.

---

### Post by Sid_Smith on 2016-05-03
I added the wireless info file for two cases. One is before I tried to connect to my wifi network. The other is when the connection fails and the wifi symbol disappears.
Thanks !

**BEFORE FILE: **[http://pastebin.com/ZHdhWk0W](http://pastebin.com/ZHdhWk0W)[B]

AFTER FILE:[/B] [http://pastebin.com/WgYMUCPr](http://pastebin.com/WgYMUCPr)

---

### Post by Sid_Smith on 2016-05-05
bounce !

---

### Post by jeremy31 on 2016-05-05
Can you change encryption on the wifi to WPA2 only as right now it has TKIP enabled.  We should set the regulatory info since that is still at the default setting
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

Your router also has the same SSID for both 2.4 and 5 GHz and the issue may be happening when Ubuntu decides for switch from one to the other.  If you rename the 5GHz, just add -5 or something to the end of the name that issue shouldn't occur

You must have Secure Boot turned off in BIOS or there isn't an option for it

---

### Post by Sid_Smith on 2016-05-09
Thanks. I'll try this soon. I don't have secure boot for sure.

---

### Post by Sid_Smith on 2016-05-11
Tried this now for my AT&T wifi-[https://www.youtube.com/watch?v=64y3K4vMLek](https://www.youtube.com/watch?v=64y3K4vMLek). I changed the SSID for the 5GHz freq as instructed. When I connect to 2.4, the same old issue occurs. Nothing happens after entering the password for 5Ghz.

---

### Post by jeremy31 on 2016-05-12
Can you also change the encryption to just WPA2-AES or WPA2-PSK.  I see TKIP is enabled

---

### Post by Sid_Smith on 2016-05-12
I did that & also restarted the radios. Still have the same problem. Should I just erase 16.04 and go back to 14.04 or 15.10 ?

---

### Post by jeremy31 on 2016-05-12
I would switch back to 14.04 or get a different wireless card. I don't know if Acer uses a whitelist to control what internal cards you can use.  I like my Intel 7260 cards but found out the hard way that Lenovo uses a whitelist and neither card would allow the laptop to boot

---

### Post by RobGoss on 2016-05-12
I don't see any were in your post how you installed Ubuntu **DVD or USB**, sometimes when we install Ubuntu at lease me, if I have trouble with one **ISO** file and I can't boot off the **USB** I will simply download another and give that ISO file a try. In most cases it will work I won't stick with any **USB or DVD** that keeps failing because I know my machines are capable of running Ubuntu

---

### Post by Sid_Smith on 2016-05-12
I installed it using an ISO DVD

---

### Post by RobGoss on 2016-05-14
> **Sid_Smith said:**
> My machine was trying to make a connection, but failed. There is no ethernet port on my linux laptop.

Hello Sid_Smith have you had any luck getting your Laptop connected?

---


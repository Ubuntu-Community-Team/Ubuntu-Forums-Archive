---
title: "How to get my Ubuntu Linux 8.04.1 LTS connected to the net? Please help!!!!?"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by Amit G on 2008-09-08
I have just installed Ubuntu Linux 8.04.1 LTS and am not able to get online through it, alongside it I have Windows XP and my system has a broadband connection via landline phone,now I am able to get online using Windows XP but not Ubuntu Linux and have been trying very hard to do so,please help me!!!

---

### Post by jigsaws on 2008-09-08
Is this DSL connection with USB modem? Check [UbuDSL]("http://www.ubudsl.com/").

---

### Post by thebigfatgeek on 2008-09-08
Hello Amit

Do you have your Ubuntu PC on a seperate machine, or on the same machine as XP (dual boot)?
Are you connecting through a Wireless or Wired connection?

Can you open a terminal window (Applications->Accessories->Terminal) and type:

```
ifconfig
```

at the prompt and identify the IP address (it could be 192.xxx.xxx.xxx, or even 169.xxx.xxx.xxx.xxx). If possible paste the output of the above command here, perhaps others can assist you better then.

You can of course try to left click on the network applet on the left of the top menubar, and ensure your network is active (selected)

---

### Post by Amit G on 2008-09-13
I have a pppoe broadband modem connected through the phone line.I tried out UbuDSL,didn't work ,it went on and on and on configuring and to no avail.I went to the Ubuntu help section on the desktop where it told me how to start up a pppoe connection through the terminal tried that but still it did not get connected-please can you guide me through it or give me a step by step procedure on how to go about it?I just can't download applications on Ubuntu,get updates or do anything until and unless I get on the web and I surf the web a lot,please guide me on how to get Ubuntu connected,I installed Ubuntu 8.04 alongside Windows XP SP2 on my system using Install within Windows function available with the Live CD.It's a pppoe broadband modem connected via my landline phone.please help me out

---


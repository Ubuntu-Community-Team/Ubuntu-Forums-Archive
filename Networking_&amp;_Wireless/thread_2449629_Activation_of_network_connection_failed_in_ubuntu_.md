---
title: "Activation of network connection failed in ubuntu 18.04 LTS"
date: 2020-08-31
forum: Networking &amp; Wireless
---

### Post by ahti-sc on 2020-08-31
I have already posted a question regarding my problem here:

[http://askubuntu.com/questions/1271027/activation-of-network-connection-failed-in-ubuntu-18-04lts?noredirect=1#comment2153093_1271027](http://askubuntu.com/questions/1271027/activation-of-network-connection-failed-in-ubuntu-18-04lts?noredirect=1#comment2153093_1271027)

But didn't got any helpful response &#65533;&#65533;

Basically I have a dual booted system with Windows 10 and Ubuntu 18.04 LTS. I can easily connect to my home WiFi with Windows but with Ubuntu I get the following error:

[HTML]Activation of network connection failed[/HTML]

For more info visit the link provided

---

### Post by drpjkurian on 2020-08-31
I understand from your post in 'ask ubuntu' that your issue may not be a driver issue since you are able to connect the machine with the hotspot provided by the mobile phone. Hence why don't you provide the same factor settings to your home wifi just like your phone hotspot?

---

### Post by ajgreeny on 2020-08-31
See Wireless-info in my signature and follow  the instructions there to run and report the details given by that script which you can download, make executable, and then run in terminal.
The information that the script provides  may help our network experts  come up with more help.

---

### Post by ahti-sc on 2020-08-31
Why is it so complicated ? In windows I can easily connect to my WiFi without changing any factor settings. Besides what factor settings you are talking about ? Can you give an example ?

---

### Post by ahti-sc on 2020-08-31
I don't understand how would I have to make executable from a text file ? I am new to ubuntu not familiar with it. Can you give a step by step procedure.

---

### Post by drpjkurian on 2020-08-31
> **ahti-sc said:**
> Why is it so complicated ? In windows I can easily connect to my WiFi without changing any factor settings. Besides what factor settings you are talking about ? Can you give an example ?

Hi
The 'same factor settings' in this issue shall be making your wifi visible and 'disabling the mac filter.

---

### Post by drpjkurian on 2020-08-31
> **ahti-sc said:**
> I don't understand how would I have to make executable from a text file ? I am new to ubuntu not familiar with it. Can you give a step by step procedure.

Select the text file and right-click it. In the pop-up menu, select 'properties'. A 'properties' window will open, select 'permission' and tick the checkbox meant for 'Execute'.

---

### Post by ahti-sc on 2020-08-31
But I want my WiFi to be hidden and protected with mac filter so that my neighbours don't missuse it. Would I have to do these steps everytime I have to connect my WiFi to ubuntu ?

---

### Post by ahti-sc on 2020-09-01
I saved the file as .txt and marked it as **Allow executing file as program** in the properties as suggested by @drpjkurian. Now how to run it ? I tried running it from the terminal but got **command not found**

---

### Post by ahti-sc on 2020-09-01
> **drpjkurian said:**
> Hi
The 'same factor settings' in this issue shall be making your wifi visible and 'disabling the mac filter.

I tried that too still got the same error.

---

### Post by deadflowr on 2020-09-03
> **ahti-sc said:**
> I saved the file as .txt and marked it as **Allow executing file as program** in the properties as suggested by @drpjkurian. Now how to run it ? I tried running it from the terminal but got **command not found**

Please read through the Networking sub forum sticky:
[https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

---

### Post by ahti-sc on 2020-09-03
Please help.

---

### Post by ajgreeny on 2020-09-04
If the file that you saved and made executable is in Downloads, open a terminal, type ```
cd Downloads
``` and the terminal prompt will change to **:~/Downloads$ **.  If the file is now elsewhere change the ***cd*** command appropriately, and don't forget Linux is case sensitive so Downloads is not the same as downloads.

Now run command ***./name-of-file***, using whetever name you gave the file, of course.  The script should run and show you a lot of detailed info which you need to copy back here for our wifi experts to see and hopefully give you more detailed help.

---

### Post by praseodym on 2020-09-04
SecureBoot is disabled?

---


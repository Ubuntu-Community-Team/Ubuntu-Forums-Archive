---
title: "HOWTO: Connect to the Internet through your cellphone"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by snowboard975 on 2007-02-17
I'm a newbie here, but I managed to connect to the Internet through my cellphone. 
Actually this thread is not a "HowTo" but a report of my experience. 
I don't guarantee this would work for all situations. I just want to share my experience with you. 

I referenced the following websites. 
[http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto]("http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto")
[http://onlyperl.egloos.com/2434318]("http://onlyperl.egloos.com/2434318")       (in Korean)

<Test Environment>
Cellphone Model: Samsung SCH-V650 (CDMA EVDO)
Linux: Ubuntu Edgy 6.10
Cellphone Service Provider: SK Telecom
Location: Seoul, South Korea

<Warning>
If you are not using the "Unlimited Data Option" or similar, for your cellphone plan, you could be charged thousands of dollars after surfing the Internet based on the amount you download from the Internet.

<Procedures>
1. Turn off your cellphone and turn it on again. (This is important for some reasons. If you don't do this, the following procedures could not work.)
2. Connect your cellphone to your computer by a USB cable.
3. open a terminal and run
```
dmesg
```
4. You'll see some messages like this at the end of the output.
```
[17180680.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17180680.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17180680.104000] usb 1-2: palm_os_4_probe - error -32 getting connection info
[17180680.104000] visor 1-2:1.1: Handspring Visor / Palm OS converter detected
[17180680.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
[17180680.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB3

```
5. At the end of this output, you will find your modem port that will be represented like this: ttyUSBx or ttyACM0 or similar, make note of it. You will need it later.
6. Run System>Administration>Networking. Uncheck all the check boxes beside "Wireless Connection", "Wired Connection", and "Modem Connection". Click Modem Connection and click Properties button.
7. Check "Enable this connection" 
8. Input your Internet service provider's phone number and dial prefix(Ask your cellphone company). In my case, phone number is 1501 and dial prefix is none.
9. Input your username and password(Ask your cellphone company this too). As for my case, username is sktelecom and password is none.
10. Click Modem tab.
11. Input your modem port that was acquired at the No. 5 procedure (with /dev). I tried /dev/ttyUSB0, /dev/ttyUSB1, /dev/ttyUSB2, and /dev/ttyUSB3. I finally found out that /dev/ttyUSB2 is right for me. 
12. Leave dial type as it is. (Both tone and pulse worked for me)
13. Set the volume "OFF"
14. Click Options tab.
15. Check "Set modem as default route to internet" and "Use the Internet service provider nameservers"
16. Uncheck "Retry if the connection breaks or fails to start" (Checking this would bother you when debugging your problem)
17. Click OK
18. Check the check box beside "Modem connection"
19. When you check it, your cellphone would dial up your ISP immediately. 
20. Open a terminal and run ```
ifconfig
```
21. If it shows ppp0 connection similar to the following, your internet is on now!
```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:211.115.18.75  P-t-P:192.168.54.178  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1887 errors:2 dropped:0 overruns:0 frame:0
          TX packets:1688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1998783 (1.9 MiB)  TX bytes:250817 (244.9 KiB)

```

22. If not, turn your cellphone off, turn it on again and try changing the modem port at the No. 11 procedure. After you change the modem port, uncheck the check box of No. 18 procedure and check it again. Your cellphone will dial up your ISP right after you uncheck and check it.

23. Repeat No. 22 procedure until you see ppp0 connection in the ifconfig messages as explained in No. 21 procedure. 

24. Got it? Congratulations!

tip) If you still experience problems, the following commands would help you to see what's happening inside during dial up. 
```
plog
```
or
```
cat /var/log/syslog
```

---

### Post by simonsphotos on 2007-02-17
thankyou that looks very useful I too need to connect to the internet via my cellphone I'll try it and let you know but my phone and ISP are not quite compatible anyway, under windows I use a program that was supplied with the phone to make the connection so it may or may not work

---

### Post by snowboard975 on 2007-02-17
> **simonsphotos said:**
> thankyou that looks very useful I too need to connect to the internet via my cellphone I'll try it and let you know but my phone and ISP are not quite compatible anyway, under windows I use a program that was supplied with the phone to make the connection so it may or may not work
I edited my thread especially the No. 6 procedure. I Inserted a sentence that says to uncheck all the check boxes beside "Wireless Connection", "Wired Connection", and "Modem Connection". 
And please note that modem port is not just ttyUSBx but /dev/ttyUSBx, which I forgot to mention before I edited my thread.

---


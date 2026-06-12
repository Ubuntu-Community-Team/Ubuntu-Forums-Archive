---
title: "Broadcom BCM4306 wireless card"
date: 2014-10-02
forum: Networking &amp; Wireless
---

### Post by Jon_Trofler on 2014-10-02
This is really driving me crazy because there are so many "fixes" already posted everywere. Nothing has worked. Is there anyone that can walk me through this? Thank you in advance.

---

### Post by jeremy31 on 2014-10-02
If you have a wired connection available run this command in terminal and then attach the resulting wireless-info file in a post.  ```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by Jon_Trofler on 2014-10-02
$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-10-02 11:23:55--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 50.19.93.196
Connecting to dl.dropbox.com (dl.dropbox.com)|50.19.93.196|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-10-02 11:23:56--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.215.118




















8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Saving to: `wireless_script'


100%[======================================>] 13,362      --.-K/s   in 0s


Last-modified header missing -- time-stamps turned off.
2014-10-02 11:23:56 (78.4 MB/s) - `wireless_script' saved [13362/13362]


[sudo] password for herbsthewerd:
, 50.16.205.195, 50.16.207.102, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.215.11
8|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropb
oxusercontent.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropb
oxusercontent.com
Location: [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script) [followin
g]
--2014-10-02 11:23:56--  [https://dl.dropboxusercontent.com/u/57264241/wireless_s](https://dl.dropboxusercontent.com/u/57264241/wireless_s)
cript
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.215.11

---

### Post by Jon_Trofler on 2014-10-02
Thanks for your reply jeremy31. I don't really know yet how to use the forums and didn't post the info directly back to you. I think I opened a new thread.

---

### Post by jeremy31 on 2014-10-02
> **Jon_Trofler said:**
> Thanks for your reply jeremy31. I don't really know yet how to use the forums and didn't post the info directly back to you. I think I opened a new thread.
There is a good alternative if you are not familiar with how this forum works- pastebin
```
sudo apt-get install pastebinit
``````
pastebinit wireless-info.txt
```

All I need is the URL from the second command

---

### Post by Jon_Trofler on 2014-10-02
[http://paste.ubuntu.com/8481082/](http://paste.ubuntu.com/8481082/)
I think I did that right?

---

### Post by jeremy31 on 2014-10-02
Try this and reboot```
sudo apt-get install firmware-b43-installer
```

---

### Post by Jon_Trofler on 2014-10-02
I don't see any change. When this laptop was running XP the wireless automatically showed a signal. Do I need to configure the "wireless network" now that I've switched to Ubuntu? The machine is an old Gateway M320 but the driver that showed "hardware installed" with ndiswrapper was for the M350 model. When the problem is fixed, will the wireless signal just show up when I reboot?

---

### Post by jeremy31 on 2014-10-02
> **Jon_Trofler said:**
> I don't see any change. When this laptop was running XP the wireless automatically showed a signal. Do I need to configure the "wireless network" now that I've switched to Ubuntu? The machine is an old Gateway M320 but the driver that showed "hardware installed" with ndiswrapper was for the M350 model. When the problem is fixed, will the wireless signal just show up when I reboot?

You should be able to detect wifi signals and see Access points in network manager or with ```
iwlist scan
```

---

### Post by Jon_Trofler on 2014-10-02
herbsthewerd@herbsthewerd-4026GZ:~$ iwlist scan
lo        Interface doesn't support scanning.


wlan0     Failed to read scan data : Network is down


eth0      Interface doesn't support scanning.

---

### Post by Jon_Trofler on 2014-10-02
Earlier I was trying to gain root and now when I'm in the terminal it has my user name twice with the @ symbol between them. Does that mean I have root or did I screw something up?

---

### Post by jeremy31 on 2014-10-02
> **Jon_Trofler said:**
> Earlier I was trying to gain root and now when I'm in the terminal it has my user name twice with the @ symbol between them. Does that mean I have root or did I screw something up?

That is normal.  To get root you can use sudo in front of a command that you need the privileges to execute, if you need to use a few commands and don't want to use sudo everytime, you can use ```
sudo -s
```  You should notice the prompt has changed from $ to #

Are you actually using Ubuntu 12.04 or Lubuntu or something else?  I am sure Varunendra uses 12.04, so he may be able to help you better than I

---

### Post by Jon_Trofler on 2014-10-02
It is 12.04 but it's Bodhi (non pae). I've had a lot of nagging issues including being able to "force PAE" the first time I switched from XP to Zorin, but now it's impossible to run the force pae command. I guess there is some sort of "motherboard" switch. I finally found Bodhi which is light weight and fairly intuitive but I've had all the same WiFi issues with all Ubuntu variations. Thank you jeremy for your time and effort, hopefully someone can help me so I don't have to switch back to Windows.

---

### Post by jeremy31 on 2014-10-02
> **Jon_Trofler said:**
> It is 12.04 but it's Bodhi (non pae). I've had a lot of nagging issues including being able to "force PAE" the first time I switched from XP to Zorin, but now it's impossible to run the force pae command. I guess there is some sort of "motherboard" switch. I finally found Bodhi which is light weight and fairly intuitive but I've had all the same WiFi issues with all Ubuntu variations. Thank you jeremy for your time and effort, hopefully someone can help me so I don't have to switch back to Windows.

I haven't tried installing Ubuntu on anything that didn't support PAE.  It is likely that my old desktop is non-PAE but I fear it will throw smoke everywhere if I try to power it up as I built it many years ago and it still has a 3.5 inch floppy drive

There is still a chance that one of the gurus here might have a solution.

---

### Post by mörgæs on 2014-10-02
Did you read the sticky note on Broadcom?
For the PAE problem this might help: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Jon_Trofler on 2014-10-02
Thanks again!

---

### Post by chili555 on 2014-10-03
You really needn't use ndiswrapper. The firmware and a reboot should work fine. Is it?

---

### Post by Jon_Trofler on 2014-10-03
Good morning chili (it's morning here), thank you for responding. I have done all the steps that you listed but no wireless signal is showing. I had previously done everything that people suggested to get ndis working so I did a clean install to start over. I then purged  bcmwl, ran apt-get update, ran apt-get install [*14e4:4306*] (rev 03) 			 		and rebooted. Maybe I need to try the "special cases"? Thanks again.

---

### Post by chili555 on 2014-10-03
Let's see what the logs say. Please open a terminal and run and post the results:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by Jon_Trofler on 2014-10-03
IT'S WORKING!!!!!!!!!!! THANK YOU CHILI!!!!!!!!!!! I can't believe I have been messing with ndiswrapper for a week! Thank you so much, I'm really enjoying Ubuntu (Bodhi) and didn't want to reload Windows. You're awesome, have a great day!

---

### Post by mörgæs on 2014-10-03
Good, please mark the thread 'solved'.

---


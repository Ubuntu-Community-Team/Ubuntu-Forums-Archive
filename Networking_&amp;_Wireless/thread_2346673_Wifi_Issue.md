---
title: "Wifi Issue"
date: 2016-12-17
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2016-12-17
After fresh install of ubuntu 16.04 on an HP pavilion dv7,  I am unable to connect to my WIFI. I can connect WIFI to with my dell no problem. My wireless card is BCM4313 802.11 bgn wireless network adapter.  I ran  wireless info.txt:  after running sudo apt-get update. This is the URL that shows the output of the wireless info report I ran on my HP DV7 Ubuntu 16.04 fresh install.  Any thing you could provide would be much appreciated.  

[http://paste.ubuntu.com/23643720/](http://paste.ubuntu.com/23643720/)

---

### Post by howefield on 2016-12-17
Thread moved to the "*Networking & Wireless*" forum.

You have posted a copy of the wireless script itself, not the resulting information that you get from running it.

---

### Post by rocky3 on 2016-12-17
Sorry about posting the script - my bad.  I went back and pasted the contents of the report with my info in paste.ubuntu.com.  This is the URL that show in the info on my HP DV7 Ubuntu 1604.

   [http://paste.ubuntu.com/23643720/](http://paste.ubuntu.com/23643720/)

---

### Post by wildmanne39 on 2016-12-17
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and your wifi should come on, if not post a fresh wireless script because we may have to unblacklist two drivers, but I think that will be done when you run the command above.

Also there are a few setting that will probably have to be change for your wifi to work at its best.
Thanks

---

### Post by rocky3 on 2016-12-17
Wildman 39,  Thank you so much for responding.  I executed the command you suggested . . . unfortunately, it did not work.  So I have updated my wireless info as you suggested and attached the URL from paste.ubuntu.com:  

[https://paste.ubuntu.com/23645221/](https://paste.ubuntu.com/23645221/)


BTW - When ever I try to connect, the authentication window keeps coming up for my password already applied.  It just keeps coming back saying it won't authenticate me.

---

### Post by wildmanne39 on 2016-12-17
Please do:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot and it should come on, but we may still have to fine to it if the connection is not stable.

---

### Post by rocky3 on 2016-12-17
Wildmanne39,  No luck. . . . I executed the commands but I couldn't connect.  I was able to connect to my hotspot once, but I couldn't get a browser to come up to confirm the connect.  then I turned off the UFW and rebooted again.  Then i couldn't get the hot spot or the WIFI to connect.  Please advise.

---

### Post by wildmanne39 on 2016-12-17
Please post a new wireless script information so we can see if the changes stuck.

---

### Post by rocky3 on 2016-12-17
Wildmanne,  This is the latest!  Thanks!

[http://paste.ubuntu.com/23645506/](http://paste.ubuntu.com/23645506/)

---

### Post by wildmanne39 on 2016-12-17
Please do:
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
That will set your regulatory domain for your router.

Then go to the top right corner of the screen and set your wireless settings in network manager to match the screenshots.

Check the settings in the router. WPA2-AES is best; not WPA and WPA2 mixed mode and please do not use TKIP. 

Next, if your router is capable of N speeds, you will have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Also use a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router and your computer.

If it does not connect please post a fresh script, there is an error message showing but I am not convinced it is an issue.
Thanks

---

### Post by rocky3 on 2016-12-17
Ok,  still no luck . . . . I followed all you instructions with one exception.  The router did offer WPA2 encryption (not mixed)  but, as you know, 14.04 offers the mixed (WPA & WPA2)  Thank you so much for working on this for such a long time! I have to get up early in the morning so I have to go to bed now, but, I would really appreciate the opportunity to continue to work with you or anyone who has the time and willingness to help. I have attached the URL for the latest wireless info config as you requested.

[http://paste.ubuntu.com/23645890/](http://paste.ubuntu.com/23645890/)

---

### Post by wildmanne39 on 2016-12-17
I should be here tomorrow, if for some reason I can not I am sure someone else will step in.

---

### Post by wildmanne39 on 2016-12-18
> The router did offer WPA2 encryption (not mixed) but, as you know, 14.04 offers the mixed (WPA & WPA2)In network manager it will say wpa/wpa2 but it is still best to change the setting in the router to just WPA.

What network are you trying to connect too?

Please do:
```
sudo apt-get update && sudo apt-get upgrade
```
Reboot did that help?

---

### Post by rocky3 on 2016-12-18
You are a genius!!!!  I connected WIFI!!  for the first time in over two years!!!  Thank you so much for taking the time to think about my problem!!!   

One interesting note . . . not a problem but My Dell won't connect, but that is a windows system which I can deal with Dell on.  I lost my dell connection after I changed the security setting in the dell and then I went out to the router and changed the password.  I lost the dell but then came over and ran your last upgrade code on the 14.04, rebooted and it came up recognizing Eldridge!!!  for the first time!!!    If its OK I would like to keep the issue open for 24 hours if possible . . . just to ensure I have a stable connection as you suggest.

The network I connected to was Eldridge.  


This current readout after connecting.

[http://paste.ubuntu.com/23650015/](http://paste.ubuntu.com/23650015/)

Rocky

---

### Post by Hadaka on 2016-12-18
Hi, everything looks basically ok and the suggestions wildmanne39 
had you try worked. You do have a module left over from your attempt
to load the incorrect b43 driver and it is groaning a bit in your dmesg
output. so let's get that out of there. open a terminal then copy and paste one
line at a time.
```

echo  'blacklist bcma' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf bcma
echo "sudo modprobe brcmsmac | sudo tee -a /etc/modules
```
remove wired connection and any usb devices..boot and test wireless
please post yet another wireless report.
Thanks.

---

### Post by rocky3 on 2016-12-19
hadaka,  thank you so much for due diligence in making sure I have a clean connection.  After running the commands I lost my connection.  The first line you suggested seemed to take.  the second line gave me an error msg:  FATAL - BCMA already in use.  The 3rd line didn't seem to work.  It brought me back to > prompt.  Not sure what to do with that.  But I ran a wireless report and then rebooted as you suggested and now it is no longer shows Eldridge network.  Unfortunately I am unable to find that wireless info report after the reboot.  This wireless report was produced just after I ran the commands and just before I rebooted.  The wireless info report command no longer works. . . I get this error:  failed: temporary failure in name resolution.  wget: unable to resolve host address 'github.com'  

Thanks for your patience!!

Rocky3

---

### Post by wildmanne39 on 2016-12-19
Please do:
```
sudo modprobe bcma
```
does it come back on?

---

### Post by rocky3 on 2016-12-20
Wildmanne39,  Thanks - Yes - the modprobe bcma brought the WIFI back - Im connected to Eldridge again. However, after I rebooted I had to run the same command to get Eldridge back.  I have attached the link to the latest wireless output

[http://paste.ubuntu.com/23661084/](http://paste.ubuntu.com/23661084/)

Also, what is to be done about the problem Hadaka suggested:  

You do have a module left over from your attempt
to load the incorrect b43 driver and it is groaning a bit in your dmesg
output.

---

### Post by jeremy31 on 2016-12-20
I think this can be fixed with
```
sudo sed -i 's/blacklist bcma/#blacklist bcma/' /etc/modprobe.d/blacklist.conf
```

You seem to have b43 blacklisted now so you should be good

---

### Post by rocky3 on 2016-12-21
Jeremy,  Thanks for getting back to me on this!  This is the response I got from the command you suggested i run:

turtlegeek@turtlegeek-HP-Pavilion-dv7:~$ sudo sed -i 's/blacklist bcma/#blacklist bcma/' /etc.modprobe.d/blacklist.conf
[sudo] password for turtlegeek: 
sed: can't read /etc.modprobe.d/blacklist.conf: No such file or directory



This is my wireless info output after trying to run the command:

[http://paste.ubuntu.com/23664885/](http://paste.ubuntu.com/23664885/)

---

### Post by jeremy31 on 2016-12-21
I edited the other post to fix the typo.  Try the fixed command and reboot

---

### Post by rocky3 on 2016-12-21
Jeremy,  roger, I see b43 is blacklisted.  My WIFI is up - thank you!  However, I am unable to printer WIFI.  I see the report shows my HL-2270DW printer. I did print directly via USB.  I found a driver:  2250DN - cups+gutenprint v5.  But I am to find the IP address of the printer.    Here is my latest wireless output.  anything you can do to assist would be greatly appreciated!

[http://paste.ubuntu.com/23666114/](http://paste.ubuntu.com/23666114/)

Rocky3

---

### Post by Hadaka on 2016-12-21
Hi, you still have the module bcma blacklisted , let's fix that.
please COPY and paste..
```
sudo sed -i '/bcma/ d'  /etc/modprobe.d/blacklist.conf
```
then do..
```
cat /etc/modprobe.d/blacklist.conf | grep -i bcma
```
you should get nothing...
Boot and test wireless
thanks.

---

### Post by rocky3 on 2016-12-22
Hadaka,  Thanks!   After I ran your commands, I ran the wireless output report and noticed BCMA was no longer blacklisted!   . . . . so I don't have to run commands to get my WIFI to come up . . . it comes up automatically!!  thanks -   

Printing - The only way I can print is when directly connected via USB.  It won't print wireless and it won't even print when connected via wired LAN.  When connected via USB, the only driver it offered me was this 2250DN CUPS+Gutenprint v5.2.11. . . . . my printer is a 2270DW.  Do you think that is what is preventing the printing?  Any assistance you could provide would be greatly appreciated

Here is the wireless output after running the BCMA commands and rebooting.

[http://paste.ubuntu.com/23668192/](http://paste.ubuntu.com/23668192/)


Rocky

---

### Post by Hadaka on 2016-12-22
Good news on the booting up like it should now !
Since this thread was about your wifi issue and that
has been resolved, please mark this thread as solved
by clicking **Thread Tools** near the top of the page and
then choose **Solved. **once you have that completed, please start
a new thread for the problem with the printer. I am not much of
a printer person but i am sure someone will be happy to help you.
Thanks.

---

### Post by rocky3 on 2016-12-22
Hadaka,  Jeremy,   Wildmann !!!  Thanks for helping me resolve this 16.04 WIFI issue!!  You  guy are awesome!!!!!

Rocky3

---

### Post by rocky3 on 2016-12-23
Hadaka,  I know this was solved at one point . . . . I'm so sad. I had to reconfigure my printer after my other computer (Dell) would not print.  Once I did that, I lost WIFI to 16.04 ubuntu again.  I looked in the router and this HP was no longer on the client table of the router.   Could you please take a look at my new wireless report one more time, please.  Anything you do to help would be greatly appreciated!

[https://paste.ubuntu.com/23672447/](https://paste.ubuntu.com/23672447/)

Rocky

---

### Post by wildmanne39 on 2016-12-23
Your report shows a hardblock which means the switch is off to the wifi, please turn the wifi on it can be a switch or a key combination, if you do not know, look up your computers documentation on the internet.
Thanks

---

### Post by rocky3 on 2016-12-25
Wildmann,  Thanks . . . . you were right. . . . . WIFI is back up!!!    and now the report shows hard blocked: no.   Merry Christmas to you Hadaka and Jeremy!!

Rocky 

[https://paste.ubuntu.com/23682359/](https://paste.ubuntu.com/23682359/)

---

### Post by wildmanne39 on 2016-12-25
I am glad it is working again!
Enjoy!:)

---


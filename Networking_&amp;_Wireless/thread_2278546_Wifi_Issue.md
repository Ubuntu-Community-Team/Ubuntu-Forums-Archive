---
title: "Wifi Issue"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by chris382 on 2015-05-17
Hello everyone. I just recently installed ubuntu 14.04 from a flash drive and everything seems fine except when i use the internet it gets slow and disconnects and reconnects. It's very annoying and i can't believe i got this problem after installing ubuntu. There is nothing wrong with my wifi connection and it works for every computer except for the one i just installed ubuntu on it's slow and disconnects every like four seconds.  Someone please help! I really wanted ubuntu and i wouldn't have got it if i knew this was going to happen.

---

### Post by Vladlenin5000 on 2015-05-17
Hi and welcome.

Please read the ["Before posting in Network & Wireless"]("http://ubuntuforums.org/showthread.php?t=370108") sticky. There are some suggestions about the preliminary troubleshooting and a script to gather more info if needed.

---

### Post by chris382 on 2015-05-17
*I've already tried it. Nothing is working. *

---

### Post by Vladlenin5000 on 2015-05-17
> **Vladlenin5000 said:**
> There are some suggestions about the preliminary troubleshooting _and a script to gather more info if needed_.

Please follow the instructions in that page and post back the results. Thank you.

---

### Post by wildmanne39 on 2015-05-17
Please run the script in that link and post the results here.
Thanks

---

### Post by chris382 on 2015-05-17
I am sorry for that. Here is what i got after running those commands in terminal >> pastebin.com/QQti8Vjk <<
I use to have Windows 8 running but just yesterday i installed ubuntu and everything is fine except the wifi disconnecting and being slow. It has nothing to do with my internet because it works perfect on all other devices and even use to on the computer that installed ubuntu on but ever since that change i cannot use the internet properly and it's so annoying. I'll do anything i have to do but i just want to be able to use the internet again without problems. I really wanted Ubuntu and i thought it was going to be great and now i have a computer that i can't use because the internet doesn't work properly on it. Please help me.

---

### Post by wildmanne39 on 2015-05-17
First let's run this command one line at a time and just copy and paste for accuracy
It will turn off the power saver mode that should help.
```
sudo -i
echo "options rtl8188ee fwlps=0"  >  /etc/modprobe.d/rtl8188ee.conf
modprobe -r rtl8188ee
modprobe rtl8188ee
exit
```
There are other things we can also do if needed.
Thanks

---

### Post by chris382 on 2015-05-17
Thankyou for the reply. I have ran those commands and restarted my computer and i can't really tell if it helped because it's still disconnecting and reconnecting.  I do feel that it did help but i'm still having connection issues. What else can we try?

---

### Post by wildmanne39 on 2015-05-17
Go into the router and change your encryption to just wpa2 (AES)(CCMP) not (TKIP)
save settings and close.
Then go into network manager and change the settings to match the screenshots:
If you still have issues then post a new file from the wireless script so we can see what is going on after making the changes.
Thanks

---

### Post by chris382 on 2015-05-17
I've went into my router settings and i only seen WPA2-PSK (AES) so i changed it to that. I've also went into network manager and matched my settings to yours in the screenshot. Internet is still not working properly. Here is the new wireless script >> pastebin.com/aWg4TCHV << Thankyou for staying with me. I'm determined to fix this issue and i really want to start using ubuntu to the fullest. Please get back to me on this and don't ignore me. I don't know how many times i asked about this issue and everyone continues to ignore me. Please help on this forum.

---

### Post by wildmanne39 on 2015-05-17
Please post the contents in this folder:
gksudo gedit /etc/modprobe.d/rtl8188ee.conf
you may have to install su and gedit is a text editor.

Reboot please.

The changes you made did not take effect but your wireless signal strength is a lot better.
Thanks

---

### Post by wildmanne39 on 2015-05-17
Here is a much improved driver so let's just install it, again copy and paste one line at a time for accuracy and watch for errors.
```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
sudo rm /etc/modprobe.d/rtl8188ee.conf
echo "options rtl8188ee ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```
Reboot

---

### Post by wildmanne39 on 2015-05-18
Maybe you need click on the number 2 at the top of the thread and go to page 2. I spent an hour last night getting you the answer even though I had to get up early this morning and leave town. After the mean pm I am done.

---

### Post by chris382 on 2015-05-19
Thankyou for your time to try helping me. I'm sorry for the mean PM.

---

### Post by chris382 on 2015-05-20
Thanks. When running the fifth command in the code i get "Power save disable only support rtl8188ce and rtl819ce" currently. All the other commands worked without errors. I restarted and the wifi connection is still unstable.

---

### Post by wildmanne39 on 2015-05-20
Hi, please post a new script file, where there any errors installing the new driver?
Let's see if we can rap this up in the next few minutes, I am extremely busy with many aspects of my life so if we can do this quickly tonight it will be best for you, other wise we have to work around my busy schedule and that will slow things down.

---

### Post by chris382 on 2015-05-20
Here is the new wireless script on pastebin "pastebin.com/m1pm3CdC" No, i didn't see any errors. I changed settings to wpa2-psk(AES) and matched the screenshots like before.

---

### Post by wildmanne39 on 2015-05-20
It does not look like the driver compiled, please do:
```
cd rtl8188ce-linux-driver
make clean
```
Then:
```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
sudo modprobe -r rtl8188ee
sudo modprobe rtl8188ee
```
This will take a while so watch for errors or post everything the commands output for us to look at.
Thanks

---

### Post by chris382 on 2015-05-21
[http://pastebin.com/DbWsJMbR](http://pastebin.com/DbWsJMbR)

---

### Post by wildmanne39 on 2015-05-21
That looks good the new driver should be loaded and being used. The settings in network manager and your router still did not stay but it might work okay without most of the changes but you need to set IPV6 in network manager to ignore for sure. 

When you changed the setting earlier did you save the setting before closing the window? 
I am about to go to bed for tonight, so try the changes in network manager again and see if you can get them to stay, if you do not understand exactly how to change the settings just ask and be specific and we will try to be too.
Thanks

---

### Post by chris382 on 2015-05-21
I have IPV6 on ignore and yes i saved the setting before i closed the window.

---

### Post by chris382 on 2015-05-22
> **Wild Man said:**
> That looks good the new driver should be loaded and being used. The settings in network manager and your router still did not stay but it might work okay without most of the changes but you need to set IPV6 in network manager to ignore for sure.   When you changed the setting earlier did you save the setting before closing the window?  I am about to go to bed for tonight, so try the changes in network manager again and see if you can get them to stay, if you do not understand exactly how to change the settings just ask and be specific and we will try to be too. Thanks   Is there something else i can do? I've already changed the settings in network manager. The settings in my router have changed to WPA2-PSK (AES). Thankyou.
Just incase here is the new wireless script [http://pastebin.com/9qZJQHtQ](http://pastebin.com/9qZJQHtQ)

---

### Post by wildmanne39 on 2015-05-22
Go into the router and change the channel to 6 or 11, because the channel you are on has 18 networks on it.
Thanks

---

### Post by chris382 on 2015-05-22
I was on channel 11 so i changed it to 6 but it's still unstable :(

---

### Post by wildmanne39 on 2015-05-23
Your connections are not named properly please do:
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules

```
Reboot
if you are still having issues make sure you set your channel to a fixed channel 6 and not auto,then in the router change 802.11bgn to just 802.11bg in the router.
Thanks

---

### Post by chris382 on 2015-05-23
I've done what you said and now things seem to be getting better but it's still not fully working correctly. My wifi connection still seems to stop and go slow.  Hmm.

---

### Post by wildmanne39 on 2015-05-23
Is it just slow or is it still disconnecting? Please post a new script file so we can see what is going on after all the changes.
Thanks

---

### Post by chris382 on 2015-05-23
Well at random times it goes slow saying "connecting" in firefox and then it just disconnects. I know that you've helped a lot because it doesn't disconnect as often but it still will. I've also noticed with skype that it shows me connected and then reconnects every ten seconds or so. Thanks for all the help, i hope that we can solve this issue. Here's the new wireless script [http://pastebin.com/Wd0hqLL4](http://pastebin.com/Wd0hqLL4)

---

### Post by wildmanne39 on 2015-05-24
Please do:
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Reboot does that help? if not post a new script and we will see if there is more we can do.

Right now there are 23 networks on channel 6 including yours, I guess they are all set to auto, you could run:
```
sudo iwlist scan
```
to see the best channel for you to be on when you turn your computer on.
Thanks

---

### Post by chris382 on 2015-07-26
Sorry for a very late reply. It's been a while now and i was forced to buy an ethernet cord and it works perfectly. Anyways, for some reason my wifi doesn't even connect and when i try to connect it just says "disconnected" now. Also, I've already tried to switch channels and i can't connect to any wifi network but on other devices i can connect to them. Before my wifi connection would actually connect yet it was very unstable and not working most of time but now it just tries to connect and then disconnects right after.

---


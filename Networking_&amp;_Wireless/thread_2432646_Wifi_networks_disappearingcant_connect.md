---
title: "Wifi networks disappearing/cant connect"
date: 2019-12-05
forum: Networking &amp; Wireless
---

### Post by bgmac on 2019-12-05
When I first boot up, all the available wifi networks are listed. I try to connect but after a few seconds all the wifi networks disappear and wont connect. I renamed one of the wifi networks and saw the new name on the list before they disappeared so I know the wifi adapter is working. It is not soft or hard blocked when I check the status. Its like my wifi adapter is turning off after about 30 seconds but all status indicate its working fine. I am using Ubuntu 18.04.3. 

lspci -knn | grep Net -A3; rfkill list  
Network controller [0280]: Realtek Semiconductor Co. Ltd. RTL8192EE PCI
eWireless Network Adapter [10ec:818b] (rev ff)
      Kernel driver in use rtl8192ee
      Kernal modules: rtl819ee
0: tpacpi_bluetooth_sw: Bluetooth
   Soft blocked: no
   Hard blocked: no
1: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no
2: hci0: Bluetooth
   Soft blocked: no
   Hard blocked:no


uname -a
 5.3.11-050311-generic #201911121635

---

### Post by wildmanne39 on 2019-12-05
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by bgmac on 2019-12-05
Attached is the wirless-info.txt

I still couldn't get the WiFi to work.

---

### Post by bgmac on 2019-12-05
Ok, I finally got it to connect.  Kind of a PITA though.  I rebooted several times like 10 times.  Each time, all the available wifi networks showed available and I quickly attempted to connect before they disappeared at about 30 seconds.  I set up another router not connected to the internet with no password and had my normal router running that is password secured. At about the 10th try, I was able to connect to the unsecure router with no internet connection which kept the wifi adapter alive I think.  Then connected to my normal password protected router and it worked.  It is like there is a setting that only allows 30 seconds or less then times out the wifi adapter unless it is connected.  I fear that next time the computer goes into suspend mode or shut off, then I will have to play the "How fast can I connect game" again.

---

### Post by wildmanne39 on 2019-12-05
Let's turn off power management that should help:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Now set a driver parameter and see if that helps:
```
sudo -i
echo "options rtl8192ee swenc=1"  >  /etc/modprobe.d/rtl8192ee.conf
exit
```
Click on network manager>settings>wifi>your network settings>ipv6>disable
Then reboot your computer and run the wireless script again and post the new text file while you are connected so we can get a look at your router settings to see if any more changes can be made to improve your connection further and to make sure the changes you made above stuck.

Thanks

---

### Post by bgmac on 2019-12-06
It worked!  When I rebooted, it connected the router automatically.  Thank you so much!  I am having trouble uploading the new wireless info file.  I tried pasting the text but the reply is too long.  Is there a section of the wireless info text that you wanted to see so I can paste it to keep it short enough?

---

### Post by wildmanne39 on 2019-12-06
Just paste the content of the file here:

[https://paste.ubuntu.com/](https://paste.ubuntu.com/)

Then post the link to the file here in your thread.

---

### Post by bgmac on 2019-12-06
Here is the link to wireless info txt

[https://paste.ubuntu.com/p/PfBVb4DVSB/](https://paste.ubuntu.com/p/PfBVb4DVSB/)

---

### Post by wildmanne39 on 2019-12-06
Your signal strength is very good, I see that you have two networks with the same name and almost the same signal strength and are on the same channel this is most likely going to cause your device to roam from one network to the other which means it will constantly get disconnected, I suggest you rename one of them and the one you plain to use set a fixed channel normally we say to 1, 6 or 11 since you have so many networks close to you and given the channels they are on I would set it to channel 3, this is done in your router. Here is a break down of how many devices are on each channel and it can cause interference with other devices being on the same channel.
```
16   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      4   APs on   Frequency:2.462 GHz (Channel 11)

```
Also while you are setting a fixed channel in the router I would change your encrpytion WPA2-PSK to WPA2-AES then save and reboot the router.

---

### Post by bgmac on 2019-12-06
Good catch on the 2 networks with the same name.  I will work on changing the name and make the encryption as you suggest.  I can't thank you enough for getting me straightened out.

---

### Post by wildmanne39 on 2019-12-08
Glad it is working please mark the thread solved by using thread tools at the top of the page.

Thanks

---

### Post by bgmac on 2020-01-18
> **wildmanne39 said:**
> Let's turn off power management that should help:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Now set a driver parameter and see if that helps:
```
sudo -i
echo "options rtl8192ee swenc=1"  >  /etc/modprobe.d/rtl8192ee.conf
exit
```
Click on network manager>settings>wifi>your network settings>ipv6>disable
Then reboot your computer and run the wireless script again and post the new text file while you are connected so we can get a look at your router settings to see if any more changes can be made to improve your connection further and to make sure the changes you made above stuck.

Thanks

Not sure if your still around.  Having the same issues again.  Beginning to think there is a problem with the wireless device.  I went through and ran everything again like you posted last month and cant seems to get it to work.  Same symptoms.  Sees all available wifi networks and wont connect, then all networks disappear after like 30 seconds.  I just ran the wireless info.
[https://pastebin.com/CT1ZRCCF](https://pastebin.com/CT1ZRCCF)

Thanks

---

### Post by jeremy31 on 2020-01-18
Try ```
echo "options rtl8192ee swenc=1 ips=N" | sudo tee /etc/modprobe.d/rtl8192ee.conf
```

Reboot, then check results for ```
iwconfig
```
If it shows Power Management:on
Then do ```
sudo iwconfig wlp3s0 power off
```

---

### Post by bgmac on 2020-01-18
Still not working.  it was listing power on, so I ran the power off code.  Still showed no wifi networks available.  I rebooted again and ran iwconfig again and it showed power on.  I ran the power off code again and it now shows power off.  No wifi networking showing available.

---

### Post by jeremy31 on 2020-01-18
Run the script again and post new results

---

### Post by bgmac on 2020-01-18
Just tried this since the chip set is rtl8192ee to make sure the driver was good.  Still not working....

[FONT=Arial]7. For the following Realtek wifi chipsets you can install the regular edition of the [/FONT][B]rtlwifi_new driver package from Larry Finger (lwfinger):
RTL8192CE, RTL8188CE, RTL8192SE, RTL8192DE, RTL8188EE, RTL8192EE, RTL8723AE, RTL8723BE and RTL8821AE.

[I]**Note:** for the RTL8723BE chipset, it's sometimes not necessary to replace the driver, because the current driver can sometimes be fixed as described in item 3 on this page.

a. First establish internet connection by other means, for example by ethernet cable.

b. Launch a terminal window.
[I](You can launch a terminal window like this: [*Click*]("https://easylinuxtipsproject.blogspot.com/p/terminal.html"))

c. [Copy/paste]("https://easylinuxtipsproject.blogspot.com/p/copy-paste.html") the following command line into the terminal:

[COLOR=blue]sudo apt-get install mokutil && mokutil --sb-state[/COLOR]

Press Enter. Type your password when prompted. [I]In Ubuntu this remains entirely invisible, not even dots will show when you type it, that's normal. In Mint this has changed: you'll see asterisks when you type. Press Enter again.

If it reports that Secure Boot is enabled: reboot and disable Secure Boot in the BIOS. In order to do this, you might need to set an administrator password in the BIOS first. Disabling Secure Boot is no loss: it adds no meaningful security anyway. It's primarily a means for Microsoft to enforce its vendor lock-in on your computer...

d. [Copy/paste]("https://easylinuxtipsproject.blogspot.com/p/copy-paste.html") the following command line into the terminal, in order to download and install the required build packages (the building tools with which you're going to build the driver):

[COLOR=blue]sudo apt-get install git build-essential linux-headers-$(uname -r)[/COLOR]

Press Enter. Type your password when prompted. [I]In Ubuntu this remains entirely invisible, not even dots will show when you type it, that's normal. In Mint this has changed: you'll see asterisks when you type. Press Enter again.

e. Download the actual driver (the construction kit) by means of git, with this command ([use copy/paste]("https://easylinuxtipsproject.blogspot.com/p/copy-paste.html")):

[COLOR=blue]git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)[/COLOR]

f. Copy/paste this line into the terminal, in order to enter the folder with the driver packages:

[COLOR=blue]cd rtlwifi_new[/COLOR]

Press Enter.

g. Now you're going to compile the required kernel module from the driver package. For that, run this command:

[COLOR=blue]make[/COLOR]

h. Finally, install the compiled module with this command:

[COLOR=blue]sudo make install[/COLOR]

i. Now you're going to remove the folder with the driver packages, which has become useless (and can't be used for other kernels, as it has been tailored to your current kernel by "make"). With this command:

[COLOR=blue]rm -v -R --interactive=never rtlwif*[/COLOR]

j. Reboot your computer.

k. Your wifi should work well now: click on the icon of Network Manager in the system tray, in order to see the available wireless networks.[/I][/I][/I][/I][/B]

---

### Post by bgmac on 2020-01-18
Here is the latest wireless info

[https://paste.ubuntu.com/p/nkZztbh4qK/](https://paste.ubuntu.com/p/nkZztbh4qK/)

---

### Post by bgmac on 2020-01-18
I turned the wifi power managment off in battery mode by editing the [COLOR=#444444][FONT=Roboto-Regular]/etc/default/tlp file and it worked!  Fingers crossed this sticks for a while.  That will be the first thing I check next time.

I also locked the kernel to avoid changes whenever updates are done.[/FONT][/COLOR]

---


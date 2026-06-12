---
title: "Wifi stops working after a period of time"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by ==Troy== on 2014-01-11
Hi! Having difficulty finding out what is the issue and how to solve it.

OS : Ubuntu 13.10
Wifi Card : Intel Corporation Wireless 7260 (rev 73)

Symptoms :
I am able to use the wireless and connect to wifi networks without an issue. The wifi tends to work for anywhere between 30s to ~2 days, after which internet connections simply time out (browser stuck on "Resolving host" etc). Additional symptom is that network monitor tends to show ridiculously huge spike of traffic, rather than normal activity within the limits of my internet bandwidth.

I have been having the issue since the release of 13.10, and updates did not seem to change much. I am not even sure where to begin, as majority of wifi troubleshooting guides deal with wifi not working or not connecting, mine, OTOH works but then "crashes" after a random period of time.

I am able to "reset" the wireless back to working order by stopping and starting it via "wifi on/off" key on the keyboard. If I do not do that, the wifi would not even connect to networks (or update found network list).

---

### Post by chili555 on 2014-01-11
I suggest you try the newer firmware that you can get here: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode) Download the file to your desktop. Now let's back up the current firmware:```
sudo mv /lib/firmware/iwlwifi-7260-7.ucode  /lib/firmware/iwlwifi-7260-7.ucode.bak
```Now copy the firmware file on your desktop to /lib/firmware:```
sudo cp ~/Desktop/iwlwifi-7260-7.ucode  /lib/firmware
```Now unload and reload the driver so it sees the newer firmware:```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```It may take a reboot. Please let us know the result for the benefit of the searchers.

Reference: [https://bugzilla.kernel.org/show_bug.cgi?id=66001](https://bugzilla.kernel.org/show_bug.cgi?id=66001) : Comment #17.

---

### Post by ==Troy== on 2014-01-18
Thank you chili555!

After about a week of using, I can confirm that this fix solves the problem. Wifi is stable, albeit wifi-N does not work, but is a non-concern for me (I also did not really look into this, so it might still support wifi-N and I simply did not enable it).

---

### Post by dmeyermail on 2014-08-02
Hello,
I seem to be having the same problem on Thinkpad T440s.

OS: Ubuntu 14.04
Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:c260]
    Kernel driver in use: iwlwifi

There is a wifi connection indicated, but I cannot connect. Sometimes I have to wait 5 minutes for a single page to load. After I have used the connection it becomes normal. 

Here modinfo part of wireless-info:

firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode

I do have newer versions in /lib/firmware (i.e., *-8.ucode and *-9.ucode are all there).

This is very frustrating for me, any help is really very much appreciated.

---

### Post by chili555 on 2014-08-02
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

---

### Post by dmeyermail on 2014-08-03
Hello chili,
thanks a lot I really appreciate the help. I changed from WPA +WPA2 to WPA2 (CCMP). 
From "sudo iw reg get" my county is DE. I still fixed this in /etc/default/crda. Will this be a problem when I travel?

Set IPv6 to "Ignore".

This made things a little better, still it would take me a minute or so on first opening a website.

However disbling n mode as you suggested did not work at all. In fact after this the computer was not able to connect at all. My wifi is set in the router to "n+g+b". Other options are "n+g", "b+g", "n+a". Best,

Daniel.

---

### Post by chili555 on 2014-08-03
> However disbling n mode as you suggested did not work at all. In fact after this the computer was not able to connect at all.I suggest you make the change to the conf file and reboot.```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Are you still unable to connect? If so, then remove the line:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Remove the line you added, reboot and check again.> My wifi is set in the router to "n+g+b". Perfect.> Will this be a problem when I travel?Probably not, however, you can always temporarily reset to one-size-maybe-fits-all:```
sudo iw reg set 00
```That's zero-zero.

---

### Post by dmeyermail on 2014-08-04
Hello chili,
this seems to work now. I'll report back in a couple of days, since it was erratic before and I want to see whether it keeps working. Thank you so much, I was getting quite frustrated at this point (Ubuntu 14.04 on Thinkpad T440s has been my worst linux experience ever...).

---


---
title: "Ubuntu 20.04:   WIFI shows up, but will not connect to internet"
date: 2020-10-07
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2020-10-07
I updated to Ubuntu 20.04 from 18.04.  I have the WIFI light on the desk top with 4 bars, but I cannot connect to the Internet.

[/code]dennis@dennis1:~$ sudo apt update
[sudo] password for dennis: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security InRelease             
Ign:5 [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) focal InRelease
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) focal InRelease                             
Err:8 [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) focal Release        
  404  Not Found [IP: 2001:67c:1560:8008::15 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-small (partner/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-hidpi (partner/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-small (partner/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons-hidpi (partner/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target CNF (partner/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
dennis@dennis1:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dennis@dennis1:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version (1.5.1-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dennis@dennis1:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2020-10-07 13:51:08--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 140.82.112.3
Connecting to github.com (github.com)|140.82.112.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2020-10-07 13:51:08--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.232.76.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.232.76.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  17.04K  --.-KB/s    in 0.04s   

Last-modified header missing -- time-stamps turned off.
2020-10-07 13:51:09 (407 KB/s) - ‘wireless-info’ saved [17452/17452]


Results saved in "/home/dennis/wireless-info.txt".

Results also archived in "/home/dennis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.[code/]


Sorry, I forgot how to post a long terminal posting and could not find out how?

---

### Post by SUPERFITTER on 2020-10-07
I had the computer hooked to an Ethernet cable for a while.  After about hour or so I disconnected the cable and the WIFI worked for 5 minutes and the I got a ? in the WIFI cone and I was disconnected from the internet.

---

### Post by chili555 on 2020-10-07
> Results also archived in "/home/dennis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.[code/]
How about sharing the wireless-info.tar.gz as an attachment to your reply so that we may examine it?

---

### Post by SUPERFITTER on 2020-10-07
How do I do that?

---

### Post by CelticWarrior on 2020-10-07
Click Go Advanced > click the paperclip button

---

### Post by SUPERFITTER on 2020-10-07
Double post, sorry

---

### Post by guiverc on 2020-10-07
You have many errors.
[B]
[http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/]("https://launchpad.net/~cairo-dock-team")[/B]

PPA's are 3rd party sources, so all security checks are your responsibility. You should check they are trustworthy, still maintained and good for your system. I see errors for that PPA which does not support releases after 15.04, thus provides no support for focal/20.04 & should not have been added. It should be removed.

[B]W: Target Packages (partner/binary-i386/Packages) is configured multiple  times in /etc/apt/sources.list:45 and  /etc/apt/sources.list.d/xenial-partner.list:4

[/B]You have duplicate entries, the error message tells you the file & lines where the entries can be deleted. The directory `/etc/apt/sources.list.d/` is empty for a new system, so entries there were added by someone post-install with `sudo` rights. Removing the duplicate entries will remove these warning messages.

---

### Post by SUPERFITTER on 2020-10-08
dennis@dennis1:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2020-10-07 23:58:31--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 140.82.113.4
Connecting to github.com (github.com)|140.82.113.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2020-10-07 23:58:32--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.232.76.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.232.76.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  17.04K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2020-10-07 23:58:32 (1.01 MB/s) - ‘wireless-info’ saved [17452/17452]

[sudo] password for dennis: 

Results saved in "/home/dennis/wireless-info.txt".

Results also archived in "/home/dennis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.




How do I get this file: /home/dennis/wireless-info.txt,  I cannot find this file?

---

### Post by chili555 on 2020-10-08
> How do I get this file: /home/dennis/wireless-info.txt, I cannot find this file?Open the file browser and click 'Name' to sort the files in your Home directory alphabetically. In the W's you will find wireless-info.tar.gz.

[IMG]https://i.postimg.cc/g0hPQHfc/Screenshot-from-2020-10-08-09-44-57.png[/IMG]

Attach it to your reply, please.

---

### Post by SUPERFITTER on 2020-10-08
made a mistake

---

### Post by SUPERFITTER on 2020-10-08
I cannot get that file to upload. I opened the file and as you know its 10 pages long.  How can I posted with it in a scroll-able box?

---

### Post by chili555 on 2020-10-08
Please paste the file here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by SUPERFITTER on 2020-10-08
x-special/nautilus-clipboard
copy
file:///home/dennis/wireless-info.txt


[https://paste.ubuntu.com/p/Z3PWgT7mRj/](https://paste.ubuntu.com/p/Z3PWgT7mRj/)

---

### Post by chili555 on 2020-10-08
Please try again. It is supposed to look like this: [https://paste.ubuntu.com/p/hQ2w5NvfdN/](https://paste.ubuntu.com/p/hQ2w5NvfdN/)

Your paste has no useful information that we can use to troubleshoot. Sorry.

---

### Post by SUPERFITTER on 2020-10-08
[https://paste.ubuntu.com/p/KyW9zbxkZz/](https://paste.ubuntu.com/p/KyW9zbxkZz/)

---

### Post by chili555 on 2020-10-08
Please execute these terminal commands. You may safely copy and paste:

```
sudo -i
echo "blacklist rtl8192cu  >>  /etc/modprobe.d/blacklist.conf
rm /etc/resolv.conf
ln -s /run/systemd/resolve/resolv.conf  /etc/resolv.conf
exit

```
Reboot and tell us if there is any improvement.

---

### Post by SUPERFITTER on 2020-10-08
I ran a 7 minute youtube video, no problem. When I started a second video, I lost the wireless connection, in a few seconds.

---

### Post by chili555 on 2020-10-08
> MOTO45DF      <MAC 'MOTO45DF' [AC1]>  Infra  1     2412 MHz  195 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2      yes     *  Is the channel in your router set to fixed channel 1 or autoselect. I recommend fixed.

What does this tell us?

```
lsmod | grep rtl
```Are all of your tests conducted with the ethernet cable disconnected?

---

### Post by SUPERFITTER on 2020-10-08
Is the channel in your router set to fixed channel 1 or autoselect. I recommend fixed. _ I do not know?_



_With cable connected_
dennis@dennis1:~$ lsmod | grep rtl
rtl8xxxu              131072  0
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                90112  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211              843776  4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu
cfg80211              704512  2 rtlwifi,mac80211
dennis@dennis1:~$ 


_With cable disconnected_

dennis@dennis1:~$ lsmod | grep rtl
rtl8xxxu              131072  0
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                90112  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211              843776  4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu
cfg80211              704512  2 rtlwifi,mac80211
dennis@dennis1:~$

 The channel in your router is set to fixed channel 1

---

### Post by chili555 on 2020-10-09
```
rtl8xxxu 131072 0
[COLOR="#FF0000"]rtl8192cu [/COLOR]73728 0
rtl_usb 20480 1 rtl8192cu
rtl8192c_common 53248 1 rtl8192cu
rtlwifi 90112 3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211 843776 4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu
cfg80211 704512 2 rtlwifi,mac80211
```You evidently did not blacklist rtl8192cu as I recommended. Please try again:

Please execute these terminal commands. You may safely copy and paste:


```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
rm /etc/resolv.conf
ln -s /run/systemd/resolve/resolv.conf  /etc/resolv.conf
exit
```> 
 I do not know?

Do you have administrative privileges for the router? Check in the router's administration or setup pages and find out.

---

### Post by SUPERFITTER on 2020-10-09
When I click exit I do not exit?  I logout?

dennis@dennis1:~$ sudo -i
[sudo] password for dennis: 
root@dennis1:~# echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
root@dennis1:~# rm /etc/resolv.conf
root@dennis1:~# ln -s /run/systemd/resolve/resolv.conf  /etc/resolv.conf
root@dennis1:~# exit
logout
dennis@dennis1:~$

---

### Post by chili555 on 2020-10-09
> **SUPERFITTER said:**
> When I click exit I do not exit?  I logout?

dennis@dennis1:~$ sudo -i
[sudo] password for dennis: 
root@dennis1:~# echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
root@dennis1:~# rm /etc/resolv.conf
root@dennis1:~# ln -s /run/systemd/resolve/resolv.conf  /etc/resolv.conf
root@dennis1:~# exit
logout
dennis@dennis1:~$That is the correct and entirely expected behavior.

How is the wireless working now?

---

### Post by SUPERFITTER on 2020-10-09
The wireless seems to be working now.  I ran several videos and rebooted three times, with success.  I will run this for a few days and see what happens, then close the posting.

Thank you very much for your time and patience. 


PS: Did you see any other things that I should be concerned with in the paste that i posted?

---

### Post by chili555 on 2020-10-10
> PS: Did you see any other things that I should be concerned with in the paste that i posted?None.

If the wireless is working as expected, please use thread tools at the top to mark Solved. The searchers will appreciate it.

---


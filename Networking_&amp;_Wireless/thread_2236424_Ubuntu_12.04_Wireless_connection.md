---
title: "Ubuntu 12.04 Wireless connection"
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by Lamin on 2014-07-26
Hello,

recently installed Ubuntu 12.04 32 bit. 

Ethernet connection works fine but there is something funny going on with wireless. My ssid will show up and it will allow to input the password, however, every time I have put in the password it stalls for an minute or two and then the original login prompt window pops up again as if I had never put in the original request for access. After the first couple of failed attempts I clicked on 'Show Password' to make sure I was entering the password correctly (I was) and Ubuntu still failed to established a wireless connection. 

I also have Ubuntu 14.04 64 bit and Windows 7 64 bit installed on computer and the wireless connection works fine on both of them. 

With the community's help I look forward to solving this problem.

---

### Post by Lamin on 2014-07-26
o'k, so i read the stickies up top and did the following in terminal ... Hopefully it is useful ... Don't want to bombard people with infor

larinkaare@larinkaare-Inspiron-N4010:~$  wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-07-26 18:47:02--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 184.73.186.230
Connecting to dl.dropbox.com (dl.dropbox.com)|184.73.186.230|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-07-26 18:47:02--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 107.21.115.150, 107.22.191.102, 184.73.179.178, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.21.115.150|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Location: [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-07-26 18:47:02--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.21.115.150|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4352 (4.2K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 4,352       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2014-07-26 18:47:03 (1.01 GB/s) - `wireless_script' saved [4352/4352]

[sudo] password for larinkaare: 

Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.

larinkaare@larinkaare-Inspiron-N4010:~$ lspci -nn -d 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
larinkaare@larinkaare-Inspiron-N4010:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf^C
larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get install [14e4:4727] (rev 01)
bash: syntax error near unexpected token `('
larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Reading package lists... Done
larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get install [14e4:4727] (rev 01)
bash: syntax error near unexpected token `('
larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get install [14e4:4727] rev 01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package [14e4:4727]
E: Regex compilation error - Unmatched [ or [^
E: Couldn't find any package by regex '[14e4'
E: Unable to locate package rev
E: Unable to locate package 01
larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get install 14er4:4727 rev 01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 14er4:4727
E: Unable to locate package rev
E: Unable to locate package 01
larinkaare@larinkaare-Inspiron-N4010:~$ ^C
larinkaare@larinkaare-Inspiron-N4010:~$

---

### Post by chili555 on 2014-07-26
> Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.Where is it? Did you forget to attach it?

---

### Post by Lamin on 2014-07-26
Sorry ... here it is ...

---

### Post by chili555 on 2014-07-26
You are using the driver *wl* provided by bcmwl-kernel-source. The sticky says the correct method for your device is:> For kernel versions 3.8 and later, use brcmsmac. Also see Special case #1.And special case #1 says:> Special case #1: This device uses the driver combination bcma and brcmsmac. It shouldn’t be necessary to install anything at all. Required firmware is installed by default in the package linux-firmware. Your kernel version is 3.11.0-xx. Let's try to fix it:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and let us have your report. It may take another tweak or two.

---

### Post by Lamin on 2014-07-26
Thank you. Will run code and get back to you asap.

---

### Post by Lamin on 2014-07-26
Before I reboot I ran code and copied output down below just in case it is important. 

larinkaare@larinkaare-Inspiron-N4010:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for larinkaare: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,668 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174597 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-26-generic
larinkaare@larinkaare-Inspiron-N4010:~$ ^C
larinkaare@larinkaare-Inspiron-N4010:~$

---

### Post by chili555 on 2014-07-26
So far, so good. Now please reboot.

---

### Post by Lamin on 2014-07-26
Back ... Rebooted and when I did so was in worst shape than what I started with. Wireless still didn't work but this time I couldn't connect to ethernet either. Finally after rebooting Linux and modem several times decided to load Windows to see if ethernet worked there. It didn't but all I had to do was reboot modum and it went back to normal. Once I had ethernet working in Windows, I rebooted Linux and eventually it connected to network. If you are still around what would you like me to do now.

---

### Post by Lamin on 2014-07-26
Update ... I can connect via phone which I was not able to do before but I still cannot connect via wireless ...

---

### Post by varunendra on 2014-07-26
It must be getting late in the night at Dr. Chili's home, but here at my place, it's just morning.. so while he's away, let me try what I can.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Remember that it is a slightly different script than the one you already used. It is supposed to provide us more info, and more is merrier :p

If it fails to generate the info (it fails sometimes due to a bug), use the regular script and post back its result.

Above all, don't panic. Dr. chili has set you on the correct path, it should be just some minor hindrance, probably one that we're already aware of (from the [sticky]("http://ubuntuforums.org/showthread.php?t=2214110")) :
> Special case #1: This device uses the driver combination bcma and brcmsmac....**In a few cases, it is necessary to blacklist b43 and ssb**:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by Lamin on 2014-07-26
Yes, since no one had replied in a while I went to look at the sticky and ran 

lspci -nn -d 14e4:

alone with 

uname -r.

It referred me back to special case # 1 so i tried 

sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit

and below is what I got an output of permission denied. Below is the text from the terminal 

larinkaare@larinkaare-Inspiron-N4010:~$ sudo -i
[sudo] password for larinkaare: 
Sorry, try again.
[sudo] password for larinkaare: 
root@larinkaare-Inspiron-N4010:~# 
root@larinkaare-Inspiron-N4010:~# echo "blacklist b43" >>  /etc/modprobe.d/blacklist.con
root@larinkaare-Inspiron-N4010:~# echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.confecho "blacklist b43" >>  /etc/modprobe.d/blacklist.confexit
root@larinkaare-Inspiron-N4010:~# exit
logout
larinkaare@larinkaare-Inspiron-N4010:~$ echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
larinkaare@larinkaare-Inspiron-N4010:~$ echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
larinkaare@larinkaare-Inspiron-N4010:~$

---

### Post by Lamin on 2014-07-27
O'k ... so i tried to run 

wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script

but terminal said it did not recognize '-t' so I ran the command again minus '-t' and got the following ... 

larinkaare@larinkaare-Inspiron-N4010:~$  -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script
-t: command not found
larinkaare@larinkaare-Inspiron-N4010:~$ wget -N 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-07-26 23:52:37--  [http://5/](http://5/)
Resolving 5 (5)... 0.0.0.5
Connecting to 5 (5)|0.0.0.5|:80... failed: Invalid argument.
--2014-07-26 23:52:37--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 54.243.65.97
Connecting to dl.dropbox.com (dl.dropbox.com)|54.243.65.97|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-07-26 23:52:37--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 50.19.228.218, 54.83.38.122, 54.243.243.165, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|50.19.228.218|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Location: [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-07-26 23:52:37--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|50.19.228.218|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4352 (4.2K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-07-26 23:52:38--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 4352 (4.2K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 4,352       --.-K/s   in 0s      

2014-07-26 23:52:38 (1017 MB/s) - `wireless_script' saved [4352/4352]

FINISHED --2014-07-26 23:52:38--
Total wall clock time: 1.5s
Downloaded: 1 files, 4.2K in 0s (1017 MB/s)
larinkaare@larinkaare-Inspiron-N4010:~$

---

### Post by varunendra on 2014-07-27
First, you have posted the result of the older script again, not the new one.
Second, what is "iwlwifi" doing there? Did you load it manually?
Third, if the report you posted above is a fresh one, either you never removed the "wl" driver, or installed it again. Please purge it -
```
sudo apt-get purge bcmwl-kernel-sourece
```
Then reboot, and if the problem persists, please post back the report of the newer script that I linked to (notice the address difference, the new one is "**http[COLOR="#FF0000"]s[/COLOR]://dl.dropbox.com/[B][COLOR="#FF0000"]s[/COLOR]**/qjc87hzk1z5x6z0/wireless_script[/B]" - starts with "**https:**" and there is "**s**" after "dl.dropbox.com/")

---

### Post by Lamin on 2014-07-27
Varunendra, 

first off, thank you for your help thus far. Below I answered each of your questions to the best of my ability. 

1) First, you have posted the result of the older script again, not the new one.

>  If it fails to generate the info (it fails sometimes due to a bug), use the regular script and post back its result.

As I stated in my last meassage, I tried to run the code that was provided in your hyperlink but at the time terminal did not recognize '-t', so I omitted '-t' and ran the code. I attached the results of that code. Admittedly, when I went to look for the text generated I could not find it because I did not see a new folder that was generated. Wireless-info.tar.gz was already there due to the first script I ran. However, when I right clicked on Wireless-info.tar.gz and clicked on properties I saw that it had been recently modified so I figured that the new results had been written/attached onto that folder. 

Regardless, I recently ran the script you provided again just to see if I could produce the same outcome as the first time (terminal does not recognize '-t') and the script happened to work. Clearly I cannot answer why it worked this time and not the first (I copied and pasted your code both times) but I have attached the results. 

2) > Second, what is "iwlwifi" doing there? Did you load it manually?

I cannot answer that. I have not done anything I was not instructed to do. 

3) > Third, if the report you posted above is a fresh one, either you never  removed the "wl" driver, or installed it again. Please purge it -

Again, I have not done anything I was not instructed to do. I already run the command 

sudo apt-get purge bcmwl-kernel-source

chilli555 instructed me to do. I even posted the results and he confirmed that everything went through o'k. 

> The following packages will be REMOVED:

bcmwl-kernel-source*

0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.

After this operation, 3,668 kB disk space will be freed.

Do you want to continue [Y/n]? y

(Reading database ... 174597 files and directories currently installed.)

Removing bcmwl-kernel-source ...

Removing all DKMS Modules

Done.

update-initramfs: deferring update (trigger activated)

Purging configuration files for bcmwl-kernel-source ...

update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-3.11.0-26-generic

> So far, so good. Now please reboot.

---

### Post by chili555 on 2014-07-27
> **Lamin said:**
> Update ... I can connect via phone which I was not able to do before but I still cannot connect via wireless ...Please run and attach a *wireless_script.* We need this to diagnose the issue.

---

### Post by Lamin on 2014-07-27
Hello Chili, 

how would I go about running a wireless-script?

Could you please post the exact command/code you would want me to run. 

Thank you.

---

### Post by chili555 on 2014-07-27
Happy to; If you can connect to internet via cable or other means, please open a terminal (Ctrl-Alt-T) and run (copy-paste) the following code in it ```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```Find the result it creates, most likely "wireless-info.tar.gz" and attach it to your reply.> It must be getting late in the night at Dr. Chili's home, but here at my place, it's just morning.. so while he's away, let me try what I can.You are quite correct; I was sound asleep! Thanks so much for pitching in; I'm quite sure that Lamin, as I do, appreciates it.

---

### Post by Lamin on 2014-07-27
Hello Chili, 

I recently ran that script. See post # 15. 

I will go ahead and post all three files that are on the file upload manager since ostensibly I am not loading the right one. When I uploaded the latest file in post # 15 I checked the size of the wireless-info.tar.gz in my home directory and uploaded the file in the file upload manager that had the corresponding size (6.9 KB). However, that one has the following heading 

> ########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux larinkaare-Inspiron-N4010 3.11.0-26-generic #45~precise1-Ubuntu SMP Tue Jul 15 04:04:35 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Kernel driver in use: atl1c


wheras the wireless-info.tar.gz currently in my home folder has the following heading 



> ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

larinkaare-Inspiron-N4010 3.11.0-26-generic i686,  Ubuntu 12.04.4 LTS, precise

CPU    : Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
Memory : 3831 MB
Uptime : 07:16:38 up 18 min,  2 users,  load average: 0.31, 0.16, 0.18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: bcma-pci-bridge
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam

---

### Post by chili555 on 2014-07-27
The latest, I assume, says:> State: connected (global)
================================o=============o==========o=============o=========o===========o==============o===========
 Interface & ID                 | Type        | Driver   | State       | Default | Speed     | Support      | HW Addr   
================================o=============o==========o=============o=========o===========o==============o===========
 eth0                           | Wired       | atl1c    | unavailable | no      |           |              | <MAC eth0>
--------------------------------+-------------+----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Verizon-SM-G900V-026B] | 802.11 WiFi | brcmsmac | [COLOR="#FF0000"]connected [/COLOR]  | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>And also:> Address:         192.168.43.50
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1
    DNS:             192.168.43.1So you are all fixed and happy and solved? Yes??

---

### Post by Lamin on 2014-07-27
Yes and no : ) / : ( 

As I stated, I'm currently connected through my phone acting as a hotspot. 

When I try to connect wireless through way of modum and router, Ubuntu will ask for authentification, ostebsibly spend 2-3 minutes authentifying, and then ask me for authentification again as if it were my first attempt at connecting wifi. It's the wireless circle of frustration : ) 

Should I connect ethernet again and run wireless script again under those circumstances?

---

### Post by chili555 on 2014-07-27
No. Please detach the phone and wait a few moments for Network Manager to see the change in state, and try to connect. As it is trying and failing to connect, run:```
nm-tool > lamin.txt
lsmod | grep -e wl -e brcm >> lamin.txt
cat /var/log/syslog | grep etwork | tail -n20 >> lamin.txt
```Find the file lamin.txt and post it here. Thanks.

---

### Post by Lamin on 2014-07-27
Chili, thanks for your patience thus far. 

I did what you ask and the terminal gives me no feedback. 

I search for lamin, .txt, and lamin.txt and the computer found nothing. 

One  thing I did notices was that the authentication process was a lot  shorter when I ran code you ask me to run. No longer took minutes, more  like 20-30 seconds. That was the only change I noticed. 

Below is what the terminal looked like when I ran code:

> larinkaare@larinkaare-Inspiron-N4010:~$ clear

larinkaare@larinkaare-Inspiron-N4010:~$ nm-tool > lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ lsmod | grep -e wl -e brcm >> lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ cat /var/log/syslog | grep etwork | tail -n20 >> lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ nm-tool > lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ lsmod | grep -e wl -e brcm >> lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ cat /var/log/syslog | grep etwork | tail -n20 >> lamin.txt
larinkaare@larinkaare-Inspiron-N4010:~$ ^C
larinkaare@larinkaare-Inspiron-N4010:~$

The first instance of 

> nm-tool > lamin.txt
lsmod | grep -e wl -e brcm >> lamin.txt
cat /var/log/syslog | grep etwork | tail -n20 >> lamin.txt

I ran collectively.

The second instance of 

> nm-tool > lamin.txt
lsmod | grep -e wl -e brcm >> lamin.txt
cat /var/log/syslog | grep etwork | tail -n20 >> lamin.txt

I ran separately but the outcome was the same. As stated above, I searched for lamin, .txt and lamin.txt both times and nothing showed up. 

Also, ran command while wireless was trying t connect as you stated.
 
Currently connected to ethernet but was not connected to ethernet when I was executing the code you asked me to run.

---

### Post by Lamin on 2014-07-27
Hey Chili,

apparently setting up manually worked in the following thread:

[http://ubuntuforums.org/showthread.php?t=2236517](http://ubuntuforums.org/showthread.php?t=2236517)

I want to try setting it up manually to see if it'll work but don't know how to access information. 

Apparently I'll need 

ssid

dssid 

device mac address 

cloned mac address 

mtu.

Obviously I know ssid and apparently device mac address is hardward on ifconfig and Mtu is clearly labeled but I don't know where to access the rest of the info. What in ifconfig corresponds to dssid and cloned mac address?

Once again thanks for all the help thus far. 

So far still on ethernet.

---

### Post by chili555 on 2014-07-27
I think it's premature to jump to a different solution that uses a different driver when we have, by no means, exhausted our diagnosis efforts.>  I searched for lamin, .txtWhy?? The file I asked for and the file you created, apparently, based on the result you posted was lamin.txt and not lamin, .txt nor lamin,.txt nor lamintxt. 

Please run and post:```
ls | grep lamin
```Doesn't it show the file you created as present? If so, and I suspect it does, find it and post it.

In some desktop environments, opening 'Files' may open to Desktop or Downloads or elsewhere. Be sure you navigate to your username directory.

---

### Post by Lamin on 2014-07-27
Hey Chili, 

thanks for the thumbnail. 

I attached the file you requested.

---

### Post by varunendra on 2014-07-27
Just noticed something that may be worth a try.

In the last wireless_script report (finally the desired one), the Access-Point that your card was repeatedly trying to connect (Jetstream) is using **WPA** encryption with AES (CCMP). As per my knowledge, this is a non-standard combination and shouldn't be allowed at all. By standards, WPA needs TKIP, which is also avoidable as long as possible.

In short, try this -
Log into your router/access-point and change its encryption to **WPA2-PSK** with **AES (CCMP)**.
No WPA, no WPA/WPA2 mixed mode, and no TKIP (refer to the router's user manual to know how to change encryption). Reboot the router after saving the changes, and try to connect again when it becomes ready.

Don't even think of playing with BSSID and Cloned mac address etc. Leave those at defaults (blank).

---

### Post by chili555 on 2014-07-27
> **varunendra said:**
> Just noticed something that may be worth a try.

In the last wireless_script report (finally the desired one), the Access-Point that your card was repeatedly trying to connect (Jetstream) is using **WPA** encryption with AES (CCMP). As per my knowledge, this is a non-standard combination and shouldn't be allowed at all. By standards, WPA needs TKIP, which is also avoidable as long as possible.

In short, try this -
Log into your router/access-point and change its encryption to **WPA2-PSK** with **AES (CCMP)**.
No WPA, no WPA/WPA2 mixed mode, and no TKIP (refer to the router's user manual to know how to change encryption). Reboot the router after saving the changes, and try to connect again when it becomes ready.

Don't even think of playing with BSSID and Cloned mac address etc. Leave those at defaults (blank).Sound advice and I recommend the same.

---

### Post by Lamin on 2014-07-30
Hello Chilli and Varunendra,

thanks for your help thus far. 

So update. 

I did what you guy's both recommended, logged onto router, changed encryption to WPA2-PSK with AES and rebooted router. 

Long story short, logged onto Ubuntu 12.04 and still could not connect to wireless signal from router. [**[COLOR=#DD4814][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")

Ended up calling the router's customer service department. Explained the whole history behind the dilemma and she suspected it may have something to do with the encryption/channel setting. Originally, the channel was on auto select and she had me changed it to X. She said it didn't really matter what channel it was on as long as it was not on auto select or Channel 1 or 2. At the time of the call, encryption was on WPA2-PSK with AES and she had me change it to mixed WPA/WPA2 and TKIP/AES. She also had me slightly change my ssid. Applied changes and logged out of Windows. Logged onto Ubuntu 12.04 32 Bit, selected the new ssid, input password and Ubuntu was finally able to make a connection : ) I assuming you told me not to do WPA/WPA2 and TKIP/AES out of security concerns but why do you think Ubuntu 12.04 was able to establish a connection with WPA/WPA2 and TKIP/AES and not WPA2 with AES? Or maybe it could just be attributed to the channel setting? I have yet to change anything on the router, and at least in Windows 7, the security type is WPA2-PSK and the encryption type is AES even though the router is set up to a mixed security mode along with a mixed wpa algorithm. Once again thank you for your help and hopefully this may be able to help someone else out.

---

### Post by chili555 on 2014-07-30
> why do you think Ubuntu 12.04 was able to establish a connection with WPA/WPA2 and TKIP/AES and not WPA2 with AES? Or maybe it could just be attributed to the channel setting?Without trying first one and then the other, it is probably impossible to tell. I suspect that Varun suggested, as I usually do, WPA2-AES because WPA2 is more secure than WPA and AES is likewise compared to TKIP. In my own case, with several different Ubuntu computers, phones, Pods and Pads, WPA2-AES works perfectly.

We have no way to say that with every wireless chipset and every driver and every router, this works and this other thing doesn't. All we can do is suggest and then note the result. The things Varun suggests are exactly my separate conclusions.

Here are suggestions from a device manufacturer themselves: [https://communities.intel.com/thread/46704](https://communities.intel.com/thread/46704)> Check the security encryption settings in both the computer wireless profile and the router. For home use we recommend WPA2-AES and avoid options related to TKIP.> Change from automatic channel selection to the least congested wireless channel on your router. The recommended channels are 1, 6, and 11 depending on your wireless environment. I think that guy stole all those things from Varun and me; or maybe *we* stole it from him!!

---

### Post by varunendra on 2014-07-31
My reasons for suggesting WPA2 with AES are basically the experience I have gained here + recommendations from more experienced experts like dr. chili above + some research I did myself, all of which boils down to these two explanations -

Why no TKIP : [http://ubuntuforums.org/showthread.php?p=12817495](http://ubuntuforums.org/showthread.php?p=12817495)
WPA2 Vs. Mixed mode : [http://ubuntuforums.org/showpost.php?p=12817442](http://ubuntuforums.org/showpost.php?p=12817442)

I still believe that WPA2 with AES is easy enough for most (or All Modern) drivers to decipher while also offering better security. Unless I can find a convincing explanation to the contrary, I suspect it was something other than the encryption change that helped the issues here.

---


---
title: "No network connections shown on new Acer Aspire R5-471T notebook"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-03-08
When I go to the network icon in the upper left corner, it displays nothing to connect to, just VPN connections, the toggle Enable Networking (which is on), Connection Information, and Edit Connections...

I would like to connect to my router. I am able to connect to the internet through tethering my phone and burning through my data plan, but just this, and for this reason I'm very hesitant to start a full package update. What should I do?

---

### Post by Hadaka on 2016-03-09
Hi, please post the output of..
```
lspci -n | egrep '0200|0280'
lsmod | egrep 'wl|b43|iwl|rtl|ath'
```

is the tethered connection showing as a wired connection?

thanks.

---

### Post by jdkcarlson on 2016-03-09
It shows up as "Wired connection 2." I've also been using Bluetooth.

The first line returns this:

[FONT=courier new]01:00.0 [COLOR=#ff0000]0280[/COLOR]: 168c:003e (rev 32)[/FONT]

The second line doesn't produce any visible output.

Thanks.

---

### Post by Hadaka on 2016-03-10
Hi, this is your wireless card..
```
[FONT=courier new]01:00.0 [COLOR=#ff0000]0280[/COLOR]: 168c:003e (rev 32)[/FONT]
```

the command i had you run should have showed your internal
wired card as well.. but did not. Disconnect the tethered connection
and try that first command again. Also we need to see what version
you loaded  14.04,15.04,15.10?? You dont need to be connected to the
internet to do these commands so please disconnect your tether and do..
```
lspci -n | grep 0200
lsb_release -a
arch
```
we only need to see what version from the second command..as in 15.10?
post the output
thanks.

---

### Post by jdkcarlson on 2016-03-10
I disconnected the phone. The first line, the

[COLOR=#000000][FONT=Ubuntu Mono]lspci -n | egrep '0200|0280'[/FONT][/COLOR]

yields the same 0280 response as earlier.

14.04.3 LTS is the version number I got.

---

### Post by Hadaka on 2016-03-10
Hi, your lspci output..
```
[FONT=courier new]01:00.0 [COLOR=#ff0000]0280[/COLOR]: [COLOR=#ff0000]168c:003e[/COLOR] (rev 32[/FONT]
```
requires the ATH10K driver,and that should be loaded on
a solid wired connection. I would not advise trying it on a
tethered connection. Providing your 14.04 install media is not
corrupted, i would suggest a fresh install, and a check in your
computer's BIOS to verify your Ethernet internal card is active.
you can try the command...
```
sudo modprobe ath10k
```but i doubt it will load.
also you forgot to post the output of..
```
arch
```
thanks.

---

### Post by jdkcarlson on 2016-03-11
The modprobe yielded a "FATAL: Module ath10k not found"

The arch yielded "x84_64"

How would you suggest I get a wired connection? My ports available seem to be three USB ports, an HDMI port, a USB-C port, and an SD card port. There's no obvious place to put in, say, an ethernet or phone cable. Is there a way to use one of my many USB ports other than tethering my poor phone?

---

### Post by Hadaka on 2016-03-11
Hi, you can buy a converter to do that..
do a search on ..."usb to ethernet device"
and you will see many choices and a wide range
of prices, still less expensive than burning tethered
data minutes.
keep us posted.
thanks.

---

### Post by jdkcarlson on 2016-03-13
I also have a Windows partition on the same machine for which the wireless card works just fine. Would it be possible to download something to the Ubuntu partition using this other partition, and then run it? This would save me on ordering a cable I probably wouldn't use again.

---

### Post by Hadaka on 2016-03-13
No,the windows drivers will not work in the Ubuntu
linux inviornment .It may be possible to down the linux
driver to a usb stick from a windows internet connection.
On the Ubntu os, please post the output of..
```
lspci -nnk | grep -iA2 net
```
thanks.

---

### Post by chili555 on 2016-03-13
The doctor has been called in on a consultation.

First, please show us:```
modinfo ath10k_pci | grep 003E
```If you get output like this:```
alias:          pci:v0000168Cd0000[COLOR="#FF0000"]003E[/COLOR]sv*sd*bc*sc*i*
```...then that means the correct driver is already in place (!!) but not the firmware. Load the driver and check the logs for messages about firmware:```
sudo modprobe ath10k_pci && dmesg | grep ath
```Once we see the cat scans...er, uh the logs, we'll propose a solution.

---

### Post by jdkcarlson on 2016-03-13
For Hadaka's question, the output I got was

[INDENT]Network controller [0280]: Qualcomm Atheros Device [168:003e] (rev 32)
 Subsystem: Lite-On Communications Inc Device [11ad:0807][/INDENT]

<hr>

By the way, before that, I had just done this—
[http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)
—after renaming the old folders. I downloaded the ZIP on my Windows partition then unpacked it and did mv in Ubuntu, then restarted. It didn't help, though.

> modinfo ath10k_pci | grep 003E

doesn't give any visible feedback at all.

> sudo modprobe ath10k_pci && dmesg | grep ath

yields

> 
[   0.645815] Loaded X.509 cert 'Magrathea: Glacier signing key: [something quite long in hexadecimal]'
[ 1134.473093]  [<ffffffff81074d8a>] warn_slowpath_common+0x7a/0xc0
[ 1134.473095]  [<ffffffff81074e06>] warn_slowpath_fmt+0x46/0x50


As I said to Hadaka, I just followed the steps here—
[http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)
—to the best of my ability, but it doesn't seem to have improved matters.

---

### Post by chili555 on 2016-03-13
> **jdkcarlson said:**
> As I said to Hadaka, I just followed the steps here&#8212;
[http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)
&#8212;to the best of my ability, but it doesn't seem to have improved matters.Let's see what went wrong. Please do:```
cd backports-20150313
make clean
make defconfig-ath10k
make
sudo make install
```Post any errors, warnings, etc. and we'll proceed.

---

### Post by jdkcarlson on 2016-03-14
It doesn't look like it went so well.

[INDENT]cd backports-20150313[/INDENT]

No such file or directory.

[INDENT]make clean[/INDENT]

No rule to make target 'clean'.  Stop.

[INDENT]make defconfig-ath10k[/INDENT]

No rule to make target 'defconfig-ath10k'.  Stop

[INDENT]make[/INDENT]

No targets specified and no makefile found.  Stop.

[INDENT]sudo make install[/INDENT]

No rule to make target 'install'.  Stop.

I tried finding the string "backports," and it gives me some things with long names starting with "security.ubuntu.com" in the directory /var/lib/apt/lists.

---

### Post by chili555 on 2016-03-15
You said in your post above that you followed the steps from askubuntu posted by our colleague jeremy13. The first step was to wget the backports package. You evidently didn't download it to your home directory. Maybe you downloaded it to Downloads or Desktop or ... who knows. Let's find it:```
sudo updatedb
```This will take a few moments; please be patient.```
locate backports | less
```The locate process will find every file in the directory and sub-directories, etc. What you actually need is the location of the directory itself. Here is a sample from my computer:```
/etc/modprobe.d/backports.conf
/home/chili/backports_compile.txt
/home/chili/Desktop/Forum/7260_backports.txt
/home/chili/Desktop/Forum/7260_backports.txt~
[COLOR="#FF0000"]/home/chili/Desktop/Forum/backports-20150313[/COLOR]
/home/chili/Desktop/Forum/backports-20150313.tar.xz
/home/chili/Desktop/Forum/backports-20150731
/home/chili/Desktop/Forum/backports-20150731.tar.gz
/home/chili/Desktop/Forum/backports-20150923
/home/chili/Desktop/Forum/backports-20150923.tar.gz
/home/chili/Desktop/Forum/backports-20151115
/home/chili/Desktop/Forum/backports-20151115.tar.gz
/home/chili/Desktop/Forum/backports-20151120
/home/chili/Desktop/Forum/backports-20151120.tar.gz
<snip>
```Ah, haaa! There it is. It is in Desktop/Forum. Now if I want to compile or re-compile, I need to change directories (cd) to the location of the file first. By the way, in the terminal the ~ symbol is shorthand for "/home/user/".

So, I need to do:```
cd ~/Desktop/Forum/backports-20150313
```After I press Enter, the terminal confirms that I am in the correct location:```
chili@T440p:~$ cd ~/Desktop/Forum/backports-20150313
chili@T440p:~/Desktop/Forum/backports-20150313$
```Now I can proceed:```
make clean
make defconfig-ath10k
make
sudo make install
```Please try again.

---

### Post by jdkcarlson on 2016-03-15
I see the confusion. My link didn't display the response I followed, but the question. So to clarify, I **did not** say I followed the answer from Jeremy31, and did not mean to give that impression. Rather, I tried the answer from V-Mark. The reason I chose this one was because the only way I seem to be able to get internet access on my Ubuntu machine is to log in from the small Windows partition I left or else to tether my phone and burn through my cellular data plan. I've already used a lot of it and I'm very loath to use it to download much more. I was worried that I'd run out my plan if I followed the Jeremy31 plan. So I downloaded the files from V-Mark's answer to the Windows partition and then manually moved them to the suggested folders using mv. 

Do you know how much data the Jeremy31 suggestion would use?

---

### Post by chili555 on 2016-03-15
jeremy31's answer compiles the driver, V-Mark's answer installs the firmware. Depending on your kernel version, you might need one or both. We know that:> ```
modinfo ath10k_pci | grep 003E
```
doesn't give any visible feedback at all.So you need to compile the driver. 

You said you already installed the firmware, so let's assume, for the moment, that part is good.

I estimate you'll need about 15 Mb.

---

### Post by jdkcarlson on 2016-03-16
Okay, I tethered my phone, ran Jeremy31's answer, and then ran your codes. Then I did the 

"modinfo | grep"

 you asked and it gave me the code you said indicates the firmware isn't in place. The other code, the 

"modprobe  && dmesg | grep", 

gives me a long list of error messages ending with 

"failed with error -2"

 I'd copy and paste this, but since I ran these steps and rebooted twice, my tethered phone is for some reason no longer connecting. I can copy the error messages in more detail if it will help, but it will take a bit of doing.

---

### Post by chili555 on 2016-03-16
> "failed with error -2"Please try just writing down the three lines leading up to and including that line and post them here. We needn't see the timestamp:```
[COLOR="#FF0000"][ 2554.966172][/COLOR] wlp3s0: send auth to a4:2b:b0:dc:45:86 (try 1/3)
[COLOR="#FF0000"][ 2554.968422][/COLOR] wlp3s0: authenticated
[COLOR="#FF0000"][ 2554.969340][/COLOR] wlp3s0: associate with a4:2b:b0:dc:45:86 (try 1/3)
etc., etc.

```

---

### Post by jdkcarlson on 2016-03-16
I assume the bracketed things are the timestamps? Okay, here goes. This is the first four lines.

> Loaded X.509 cert 'Magrathea: Glacier signing key: [omitted]'
ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/ACA6174/hw3.0/firmware-4.bin failed with error -2

There's more "could not fetch firmware file" for a bit, then "could not fetch board data" and "could not probe fw."

:/

---

### Post by chili555 on 2016-03-16
You said you followed V-Mark's instructions. As you see, it copies over the firmware in hw2.1. According to *dmesg*, your card and driver combination want the firmware in hw3.0.

You can find it in the most recent version of linux-firmware here: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.156_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.156_all.deb) Download it and drag and drop it to your desktop. Open a terminal and do:```
cd ~/Desktop
sudo dpkg -i linux*.deb
```Reboot.

---

### Post by jdkcarlson on 2016-03-17
Okay, I did this. dmesg again?

---

### Post by chili555 on 2016-03-17
Yes, please:```
dmesg | grep ath
```

---

### Post by jdkcarlson on 2016-03-18
Okay, did "dmesg | grep ath"! It says this:

```
[    0.728217] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    2.920391] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.143874] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    3.267483] ath10k_pci 0000:01:00.0: otp calibration failed: 3
[    3.267488] ath10k_pci 0000:01:00.0: failed to run otp: -22
[    3.267490] ath10k_pci 0000:01:00.0: could not init core (-22)
[    3.267520] ath10k_pci 0000:01:00.0: could not probe fw (-22)

```

Doesn't look too good, right?

---

### Post by jeremy31 on 2016-03-18
Try ```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```

And it might help to install a much newer version of backports like [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz)

---

### Post by jdkcarlson on 2016-03-18
Feedback is thus:

```
tee: etc/modprobe.d/ath10_core.conf: No such file or directory
options ath10k_core skip_otp=Y
```

"locate modprobe.d" also doesn't find this.

Thanks!

---

### Post by chili555 on 2016-03-18
> **jdkcarlson said:**
> Feedback is thus:

```
tee: etc/modprobe.d/ath10_core.conf: No such file or directory
options ath10k_core skip_otp=Y
```

"locate modprobe.d" also doesn't find this.

Thanks!However, Jeremy's command was:```
echo "options ath10k_core skip_otp=Y" | sudo tee [COLOR="#FF0000"]/[/COLOR]etc/modprobe.d/ath10k_core.conf
```Please try again.

---

### Post by jdkcarlson on 2016-03-18
Okay, now that I added the slash and the k that I'd missed in the "sudo tee" command, it just gives the one line of feedback

> options ath10k_core skip_otp=Y

Is this progress?

---

### Post by chili555 on 2016-03-18
> **jdkcarlson said:**
> Okay, now that I added the slash and the k that I'd missed in the "sudo tee" command, it just gives the one line of feedback



Is this progress?Probably so. Check the file and see if the text exists:```
cat /etc/modprobe.d/ath10k_core.conf
```If the text is there, reboot and see if the wireless connects. In either case, show us:```
dmesg | grep ath
```

---

### Post by jdkcarlson on 2016-03-18
The "cat" yields

```
options ath10k_core skip_otp=Y
```

The wi-fi menu has a new text: below "Wi-Fi Networks" appears now "device not ready", which I don't remember from before.

"dmesg | grep ath" nets me a bunch of error messages which I'll copy to a textfile and post from the Windows partition.

Here's the dmesg feedback:

```
[    0.642963] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    1.774136] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.727878] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    4.873509] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 htt 3.26 wmi 4 cal otp max_sta 32
[    4.873512] ath10k_pci 0000:01:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    4.952479] ath: EEPROM regdomain: 0x6c
[    4.952481] ath: EEPROM indicates we should expect a direct regpair map
[    4.952483] ath: Country alpha2 being used: 00
[    4.952484] ath: Regpair used: 0x6c
[   10.226915] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   13.226447] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   21.541064] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   24.540608] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   32.831337] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   35.830832] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   44.121359] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   47.121022] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   55.411493] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   58.411027] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   66.701738] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   69.701180] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   77.992138] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   80.991641] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   89.286142] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11
[   92.285547] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  100.576455] ath10k_pci 0000:01:00.0: failed to enable PMF QOS: -11

```

---

### Post by jeremy31 on 2016-03-19
Time to try newer backports.  Download [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz)
Get it on Ubuntu desktop, right click, 'Extract here'
Then in terminal
```
cd Desktop/backports-4.4.2-1
make defconfig-ath10k
make
sudo make install
```
Reboot

Post ```
ls /lib/firmware/ath10k/QCA6174/hw3.0/
```

---

### Post by jdkcarlson on 2016-03-19
Thanks!

Feedback from ls:

```
board.bin  firmware-4.bin  notice_ath10k_firmware-4.txt
```

Unrelated question: is there a way to make this forum stop logging me out? Every time I suspend my laptop and I try to reply, I have to do this SSO login, and then it directs me to the front page of the forum rather than to this thread. (Or is this the intended behavior?)

---

### Post by jeremy31 on 2016-03-19
> **jdkcarlson said:**
> Thanks!

Feedback from ls:

```
board.bin  firmware-4.bin  notice_ath10k_firmware-4.txt
```

Unrelated question: is there a way to make this forum stop logging me out? Every time I suspend my laptop and I try to reply, I have to do this SSO login, and then it directs me to the front page of the forum rather than to this thread. (Or is this the intended behavior?)

If there is a way to avoid the log out, I haven't found it

Any luck with the newer backports?

---

### Post by jdkcarlson on 2016-03-19
Ugh, that's really annoying.

I'm not sure what success looks like. I take it the ls feedback is what we hoped for? 

The pulldown menu for wi-fi looks the same: logo is an empty sector of a circle, no nearby routers listed, and "device not ready."

Just to be safe, here's another "dmesg | grep ath".

```
[    0.643601] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    1.718112] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.164561] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    2.167182] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    2.167188] ath10k_pci 0000:01:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    2.237703] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.357450] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.357453] ath10k_pci 0000:01:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    7.354977] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[    7.423553] ath: EEPROM regdomain: 0x6c
[    7.423555] ath: EEPROM indicates we should expect a direct regpair map
[    7.423557] ath: Country alpha2 being used: 00
[    7.423558] ath: Regpair used: 0x6c
[   12.682161] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   18.681237] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   24.008349] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   30.007402] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   35.318661] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   41.317733] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   46.624878] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   52.623829] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   57.931039] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   63.930103] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   69.237224] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   75.236235] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   80.543458] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   86.542448] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   91.861660] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   97.860712] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  103.167885] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  109.167065] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  114.474133] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  120.473279] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  125.780378] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  131.779396] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  137.086692] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  143.085729] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  148.392788] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  154.391994] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  159.702960] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  165.702133] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  171.009211] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  177.008407] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  182.319413] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  188.318539] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  193.629607] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  199.628829] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  204.939890] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  210.938991] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  216.250185] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  222.249251] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  227.560255] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  233.559487] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  238.866612] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  244.865678] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  250.176781] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  256.175900] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  261.482885] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  267.482145] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  272.793192] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  278.792338] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  284.099498] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  290.098546] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  295.409560] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  301.408728] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  306.715867] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  312.714957] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  318.021983] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  324.021120] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  329.332241] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  335.331413] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  340.638474] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  346.637648] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  351.944713] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  357.943793] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  363.254937] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  369.254089] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  374.565202] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  380.564269] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  385.871405] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  391.870513] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  397.181576] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  403.180653] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  408.487716] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  414.486871] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  419.793883] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  425.792983] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  431.100284] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  437.099372] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  442.406383] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  448.405478] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  453.712714] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  459.711722] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  465.018943] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  471.018012] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  476.329097] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  482.328216] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  487.635200] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  493.634447] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  498.941502] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  504.940681] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  510.251641] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  516.250838] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  521.557963] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  527.557031] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  532.864213] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  538.863260] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  544.174440] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  550.173476] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  555.480517] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  561.479764] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  566.786787] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  572.785975] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  578.097056] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  584.096095] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  589.403222] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  595.402298] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  600.709408] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  606.708484] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  612.019641] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  618.018822] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  623.329840] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  629.329019] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  634.640133] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  640.639204] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  645.946344] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  651.945398] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  657.256516] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  663.255687] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  668.562692] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  674.561834] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  679.873008] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  685.872078] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  691.183181] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  697.182320] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  702.493451] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  708.492449] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  713.799646] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  719.798739] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  723.256493] Modules linked in: arc4 rtsx_usb_ms rtsx_usb_sdmmc memstick rtsx_usb hid_multitouch uvcvideo usbhid hid videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media btusb rfcomm bnep bluetooth joydev snd_hda_codec_hdmi acer_wmi sparse_keymap snd_hda_codec_realtek snd_hda_codec_generic nls_iso8859_1 snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm x86_pkg_temp_thermal coretemp kvm_intel ath10k_pci(OE) kvm ath10k_core(OE) ath(OE) crct10dif_pclmul mac80211(OE) crc32_pclmul snd_seq_midi ghash_clmulni_intel aesni_intel aes_x86_64 snd_seq_midi_event lrw snd_rawmidi cfg80211(OE) gf128mul glue_helper snd_seq ablk_helper cryptd snd_seq_device compat(OE) snd_timer serio_raw snd soundcore i915_bpo shpchp intel_ips drm_kms_helper drm i2c_algo_bit wmi video mac_hid acpi_pad parport_pc ppdev lp parport psmouse ahci libahci
[  723.256534]  [<ffffffff81074d8a>] warn_slowpath_common+0x8a/0xc0
[  723.256536]  [<ffffffff81074e06>] warn_slowpath_fmt+0x46/0x50
[  728.200629] ath10k_pci 0000:01:00.0: failed to set tx-chainmask: -11, req 0x3
[  731.200344] ath10k_pci 0000:01:00.0: failed to set arp ac override parameter: -11
[  737.199416] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  742.510438] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  748.509617] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  753.820773] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  759.819709] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  765.130915] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  771.130045] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  776.437168] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  782.436124] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  787.743376] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  793.742379] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  799.049615] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  805.048694] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  810.355808] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  816.354805] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  821.662028] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  827.661105] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  832.972280] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  838.971335] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  844.282328] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  850.281556] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  855.592734] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  861.591668] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  866.898936] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  872.897768] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  878.209031] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  884.208180] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  889.515137] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  895.514386] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  900.825376] ath10k_pci 0000:01:00.0: failed to enable adaptive qcs: -11
```

---

### Post by jeremy31 on 2016-03-19
[https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin?raw=true](https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin?raw=true)

Transfer it to Ubuntu desktop then
```
sudo cp Desktop/board-2.bin /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin
```

Reboot, if same error occurs
```
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin.bak
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bin
```

Reboot

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343) says that this worked but another post said that they needed both board.bin and board-2.bin so we will try both

---

### Post by jdkcarlson on 2016-03-19
Did the first thing. Network still wasn't connected. For the two sudo mv's, I assume the second one is a typo? As my computer points out, they are the same destination. I took a guess you wanted me to move board-2.bin to board.bin and that's why board.bin had been moved to board-2.bin.bak in advance, but I could be wrong.

Anyway, *I see routers now*! 

I found the one that's right next to me and selected it, but have a new error message:

> **Connection activation failed**

(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/1' failed in libnm-glib.

But I still feel hopeful now!

---

### Post by jeremy31 on 2016-03-19
Even though your network is not hidden, try Connect to a hidden network, type the info in and see if it works

---

### Post by jdkcarlson on 2016-03-19
Yep, that worked finally! I'm entering this message from Ubuntu!

Thank you all so much!

(P.S.: I have some other questions, like how to get my phone to tether again now if I need it to. Should I start a new thread?)

---

### Post by jeremy31 on 2016-03-19
Your mobile provider may have a limit on how many times you can tether without paying the tethering fee, start a new thread for that and use thread tools at the top of the page to "mark as solved"

---

### Post by jdkcarlson on 2016-03-19
Okay, thanks!

Other question (maybe this is a new thread too): is there a way to get it so that I can connect to networks normally rather than treating them as hidden?

---

### Post by jeremy31 on 2016-03-23
It might be a network manager bug

---

### Post by jdkcarlson on 2016-03-26
Assuming that it is, do you know if there's anything I could do about it?

---

### Post by jeremy31 on 2016-03-27
[http://ubuntuforums.org/showthread.php?t=2239214&p=13096999#post13096999](http://ubuntuforums.org/showthread.php?t=2239214&p=13096999#post13096999)

That should fix it

---

### Post by jdkcarlson on 2016-04-13
Update: my computer crashed and when it came back the wireless had stopped working. I don't understand why this would be. I've tried to run though everything from this thread but somehow it hasn't brought wireless back. I've started a new post with more details:

[http://ubuntuforums.org/showthread.php?t=2320324&p=13469504#post13469504](http://ubuntuforums.org/showthread.php?t=2320324&p=13469504#post13469504)

---


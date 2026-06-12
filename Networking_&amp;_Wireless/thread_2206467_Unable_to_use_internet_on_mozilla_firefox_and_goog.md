---
title: "Unable to use internet on mozilla firefox and google chromium on ubuntu 10.04"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by Harsha_Sanjeev on 2014-02-19
Hello All,

          I am using Ubuntu 10.04 [ required for my application ] and Tata photon plus for connecting to internet. I am able to get connected to internet only through terminal and synaptic package manager, which signifies that its not an internet connection issue. But I am not able to use internet on Mozilla Firefox or Google Chromium. 

          I have gone through the previous posts and tried to resolve this issue, however i was not successful. I have tried disabling the IPv6 on the browser and on the computer. I have tried changing the sysctl.conf, reinstalling and upgrading the mozilla firefox,  however i am unable to resolve this issue. 

Any help in resolving this is appreciated. 

Thank you!

---

### Post by varunendra on 2014-02-19
> **Harsha_Sanjeev said:**
> I am using Ubuntu 10.04 [ required for my application ] and Tata photon plus for connecting to internet. I am able to get connected to internet only through terminal and synaptic package manager, which signifies that its not an internet connection issue. But I am not able to use internet on Mozilla Firefox or Google Chromium.

Welcome to the forums Harsha!

How are you using the Photon? Via Ubuntu's native Network Manager or via some third party client like "Mobile Partner" (or some program that might have come with the Photon)?

If using a third party program, that may be the problem. Usually these programs can only be installed with root privileges (with sudo), and the network session they start can only be used by the root (or by normal programs that run with root privileges). So what needs to be done greatly depends on how you are connecting to the network, and the steps you needed to use the modem.

---

### Post by Harsha_Sanjeev on 2014-02-20
Hello Varun, 

           Thank You, 
I have installed the photon following the procedure below. 

On Terminal

[I][B]cd /dev/disk/by-id
[/B][/I]
[I][B]ls
[/B][/I]
[I][B]sudo mount usb-HUAWEI_Mass_Storage_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-0\:0 /mnt
[/B][/I]
[I][B]cd /mnt
[/B][/I]
***sudo sh ./install_linux***

After these steps, the dashboard of the Tata Photon Plus appears on the screen. I click on connect. Thats how I get access to internet on synaptic manager and terminal. However Mozilla and chromium doesnt work. 

Kindly advise

---

### Post by varunendra on 2014-02-20
> **Harsha_Sanjeev said:**
> 
**[COLOR="#FF0000"]sudo[/COLOR] sh ./install_linux**

After these steps, the dashboard of the Tata Photon Plus appears on the screen. I click on connect. Thats how I get access to internet on synaptic manager and terminal. However Mozilla and chromium doesnt work.

I'm 100% sure now that the problem is what I suspected/explained above.

You ran some program that came with Tata Photon and it installed its connection client with root access. Now when you run this client, it connects to the net but the access is granted to root only.

We may try to reinstall the program as a normal user, but that would probably fail.
We may also try to do some tweaks so that a normal user can get access to the connection established by it, but that would be cumbersome and may take a some (or a lot of) experimenting.

**The quickest and most promising solution** is to NOT USE that client program at all, and use Ubuntu's Network Manager instead.
If the program runs automatically when you insert the USB modem, then it may be a problem *(because then it may take control before Network Manager could)*, but shouldn't be difficult to solve.

Soo.. when you insert the modem but don't run the dashboard program (or close it if it auto-starts), do you see any prompt in Network Manager's drop-down menu (in the upper right corner) to setup a "New Mobile Broadband Connection.." ?

If yes, click it and proceed with the prompts. It should automatically setup the connection for you.

If not, goto (at the bottom of the same drop-down menu) "Edit Connections..." > "Mobile Broadband" tab > click "Add" button . In the "..mobile broadband device" field there, do you see your modem listed?

If yes, proceed with the prompts, just answer the questions and it will set it up automatically exactly as above.
If not, post back what you see, along with the following command outputs -
```
lsusb
dmesg | tail -20
```
(Run the above commands after about 20 to 30 seconds AFTER plugging in the modem)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

**PS:**
In your current setup, you may run the browsers as roots (if there is a button in the dashboard to open a browser, it will do just that). But that is almost _like sending printed Invitation cards to Hackers to hack into your system and rule it_.

**PPS:** Also, a VERY IMPORTANT QUESTION : Do you need to enter your login password when you run any command with "sudo"?? If not, this is a serious problem that you should IMMEDIATELY fix. The kind of dashboard program you mentioned often do this absolutely ridiculous and unsafe modification to the system.

---

### Post by Harsha_Sanjeev on 2014-02-28
Hello Varun, 

Thank you for educating me to use Code tags. 

Regarding the issue, 

    I have not used the autorun program that popped up when i plugged the photon+. I edited the network connections and created a mobile broadband connection. The last used status is "Never".

    The lsusb outputs the following
```

root@hash-laptop:/# lsusb
Bus 002 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd.
Bus 002 Device 002: ID 8087:0020
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6409 Microdia
Bus 001 Device 002: ID 8087:0020
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The dmesg output is as follows
```

root@hash-laptop:/# dmesg | tail -20
[ 5665.713217] USB Serial support registered for GSM modem (1-port)
[ 5665.713268] option 2-1.2:1.0: GSM modem (1-port) converter detected
[ 5665.713675] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[ 5665.714120] option 2-1.2:1.1: GSM modem (1-port) converter detected
[ 5665.714272] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[ 5665.714311] option 2-1.2:1.2: GSM modem (1-port) converter detected
[ 5665.714446] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2
[ 5665.714473] usbcore: registered new interface driver option
[ 5665.714476] option: v0.7.2:USB Driver for GSM modems
[ 5668.322163] usbcore: registered new interface driver huawei_ether
[ 5670.653685] usb-storage: device scan complete
[ 5670.655397] scsi 10:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 0
[ 5670.657396] scsi 10:0:0:1: Direct-Access HUAWEI SD Storage 2.31 PQ: 0 ANSI: 2
[ 5670.673289] sr1: scsi-1 drive
[ 5670.673494] sr 10:0:0:0: Attached scsi CD-ROM sr1
[ 5670.673674] sr 10:0:0:0: Attached scsi generic sg2 type 5
[ 5670.674056] sd 10:0:0:1: Attached scsi generic sg3 type 0
[ 5670.684292] sd 10:0:0:1: [sdb] Attached SCSI removable disk
[ 5673.917591] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 5673.930831] ISOFS: changing to secondary root

```



What could be done to resolve this?

And yes, when i use sudo access there is no password required. The access is granted directly. How do I correct this? I have tried uninstalling/ removing the tata photon+ package that was installed earlier, but with no success. 

Kindly advice.

---

### Post by varunendra on 2014-02-28
> **Harsha_Sanjeev said:**
> I have not used the autorun program that popped up when i plugged the photon+. I edited the network connections and created a mobile broadband connection. The last used status is "Never".
Was the modem detected in the "Use this device.." field while creating the connection?

The device you have -
```

root@hash-laptop:/# lsusb
Bus 002 Device 004: ID **[COLOR="#0000CD"]12d1:140b[/COLOR]** Huawei Technologies Co., Ltd.

```
..is natively supported by usb_modeswitch and "option" driver, so it should work out-of-box without needing any third party application.

I am not sure about these two messages that appear AFTER the device is detected and probed -
```
[ 5673.917591] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 5673.930831] ISOFS: changing to secondary root

```
But I suggest to note down the profile and connection settings from the photon+ application, then uninstall it. It is possible that the device may be getting locked by that application when it autoruns, thus not granting Network Manager access to it.

> **Harsha_Sanjeev said:**
> I have tried uninstalling/ removing the tata photon+ package that was installed earlier, but with no success.
The Uninstall script should be located in the same directory where the application has been installed, usually the **/usr/local/*<application folder>*** or **/user/local/bin/*<application's own directory>***

> **Harsha_Sanjeev said:**
> And yes, when i use sudo access there is no password required. The access is granted directly. How do I correct this?
It must have added a new line in your /etc/sudoers file, at its bottom -
```
ALL ALL=(ALL) NOPASSWD:ALL
```
This line should be deleted or commented out, but VERY CAREFULLY! The sudoers file should be handled with extreme care as even a single minor error in formatting or punctuation will corrupt it. A corrupt "sudoers" file means you will loose the right to gain root privileges with "sudo", thus not being able to perform ANY administration level tasks on your own system. Although the is a way to fix that but why go there when we can do it safely and easily.

Check if the above line exists in your sudoers file. It requires root access to even read that file, so run your command with 'sudo' -
```
sudo cat /etc/sudoers
```
Does it have the "ALL ALL=(ALL) NOPASSWD:ALL" line in it? I'm sure there is.

Either delete, or comment it out. To comment it out -
```
sudo sed **[COLOR="#0000CD"]-i[/COLOR]** 's/^ALL.*NOPASSWD:ALL/# &/' /etc/sudoers
```
Run the above command without the "**[COLOR="#0000CD"]-i[/COLOR]**" option first. That will show you how the file will look after the modification without actually modifying it.

When you are satisfied that only the target line is getting modified as expected, run the command with the "**[COLOR="#0000CD"]-i[/COLOR]**" option, exactly as above. This will actually modify it instead of showing the output on the screen.

Once the application is removed (and the sudoers file corrected, which is not related but recommended for security), try deleting the connection in Network Manager > replug the modem > recreate a fresh connection. If no Mobile Broadband connections exist in Network Manager (after deleting the existing ones), the nm menu should show you the "New Mobile Broadband connection.." option. Click it to run the connection wizard > answer the prompts > done.

If this doesn't get you connected, please match the settings that you saved from the existing photon+ connection, and post back if they are the same and still there is connection problem.

---


---
title: "driver RT2870 STA_v1.2.1.0 not working. Wifi adapter SMCWUSB-N LUBUNTU (Ubuntu 15.10)"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2016-01-05
Hello

I have been trying to get this WIFI adapter working under this LUBUNTU (Ubuntu 15.10) with no success so far. Apparently the official website for Ralink devices was closed and  I had to try therefore with different versions of the driver RT2870. I found all of them in "driverscollection dot com". The last driver I have tried is 2007_1220_RT2870_Linux_STA_v1.2.1.0. The launch of the command "make" did not end successfully with driver as you can see in the following lines:

```

CC [M]  /home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.o
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:778:20: error: ‘struct task_struct’ has no member named ‘fsuid’
  orgfsuid = current->fsuid;
                    ^
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:779:20: error: ‘struct task_struct’ has no member named ‘fsgid’
  orgfsgid = current->fsgid;
                    ^
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:780:9: error: ‘struct task_struct’ has no member named ‘fsuid’
  current->fsuid=current->fsgid = 0;
         ^
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:780:24: error: ‘struct task_struct’ has no member named ‘fsgid’
  current->fsuid=current->fsgid = 0;
                        ^
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:1369:9: error: ‘struct task_struct’ has no member named ‘fsuid’
  current->fsuid = orgfsuid;
         ^
/home/x/Descargas/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:1370:9: error: ‘struct task_struct’ has no member named ‘fsgid’
  current->fsgid = orgfsgid;

```


What is more, all of these drivers displayed different errors after launching the command "make". That is why I would really appreciate if you could help me by replying with any suggestion to get this adapter working properly.

Please find attached my file [ATTACH]266567[/ATTACH] with the corresponding information that might give an insight about the problem I am dealing with.

By the way, I know this USB Wifi adapter is not broken because it keeps working great under Windows Vista.

Thanks in advance for any tip or guideline you can think of.

---

### Post by chili555 on 2016-01-05
>  The last driver I have tried is [COLOR="#FF0000"]2007[/COLOR]_1220_RT2870_Linux_STA_v1.2.1.0. > rt_profile.c:1370:9: error: ‘struct task_struct’ has no member named ‘fsgid’What you see here is Linux code for, "Stop. Quit.You can't compile a 2007 antique on my shiny new 15.10 (built in October, 2015) system."

You already have the correct driver,* rt2800usb*. It scans and sees networks. 

I do see this:> Region: Europe/Madrid (based on set time zone)

country 00: DFS-UNSETI recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Reboot with the ethernet detached and tell us what happens.

---

### Post by thosecars822 on 2016-01-07
Thank you for your tip. I appended "ES" after "REGDOMAIN=" in this file "/etc/default/crda" as you suggested, then I unplugged the ethernet cable and I rebooted my computer eventually. For some reason I keep on however seeing this country code "00" as follows after launching the command "sudo iw reg get":

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

I just created the file wireless-info.txt. I will attach here the recreated file [ATTACH]266587[/ATTACH]

Needless to say the Wifi adapter does not work either after updating the file "/etc/default/crda" as explained.

Thanks in advance for any other suggestion.

---

### Post by nicotra-davide-5 on 2016-01-07
I'm having troubles with the pci 3290... have you tried to downgrade your kernel? Some threads about the 3290 suggests to downgrade and that to attempt to build the driver.

---

### Post by thosecars822 on 2016-01-07
Thank you. I have not found yet any thread for the driver RT2870 that said something about that. What is more, I have never downgraded a kernel before. I'll take a look at this approach. Thank you for the idea by the way.

Which Linux kernel should I downgrade to in order to try the last suggestion?

---

### Post by chili555 on 2016-01-07
> **nicotra-davide-5 said:**
> I'm having troubles with the pci 3290... have you tried to downgrade your kernel? Some threads about the 3290 suggests to downgrade and that to attempt to build the driver.He doesn't have the infamous 3290. He has 157e:300e TRENDnet SMC SMCWUSB-N 802.11bgn 2x2:2 Wireless Adapter [Ralink RT2870]

---

### Post by chili555 on 2016-01-07
> **thosecars822 said:**
> Thank you for your tip. I appended "ES" after "REGDOMAIN=" in this file "/etc/default/crda" as you suggested, then I unplugged the ethernet cable and I rebooted my computer eventually. For some reason I keep on however seeing this country code "00" as follows after launching the command "sudo iw reg get":

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

I just created the file wireless-info.txt. I will attach here the recreated file [ATTACH]266587[/ATTACH]

Needless to say the Wifi adapter does not work either after updating the file "/etc/default/crda" as explained.

Thanks in advance for any other suggestion.Yikes; just yikes.

Please let us see:```
sudo modprobe -r ndiswrapper
sudo modprobe rt2800usb
iwconfig
```You have tried a little bit of everything, it appears!

---

### Post by thosecars822 on 2016-01-07
The output for the mentioned code
```

sudo modprobe -r ndiswrapper
sudo modprobe rt2800usb
iwconfig

```
is the following:

```

x@x-G31T-M2:~$ sudo modprobe -r ndiswrapper
[sudo] password for x: 
x@x-G31T-M2:~$ sudo modprobe rt2800usb
x@x-G31T-M2:~$ iwconfig
wlx0013f7c99c1b  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

ens33     no wireless extensions.


```

Now the device blinks again but it does not work anyways.

---

### Post by chili555 on 2016-01-07
> **thosecars822 said:**
> The output for the mentioned code
```

sudo modprobe -r ndiswrapper
sudo modprobe rt2800usb
iwconfig

```
is the following:

```

x@x-G31T-M2:~$ sudo modprobe -r ndiswrapper
[sudo] password for x: 
x@x-G31T-M2:~$ sudo modprobe rt2800usb
x@x-G31T-M2:~$ iwconfig
wlx0013f7c99c1b  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

ens33     no wireless extensions.


```So now you have a wireless interface. Does it scan and see networks?```
sudo iwlist scan
```

---

### Post by thosecars822 on 2016-01-07
Yeah, that outputs the information about all the networks around. I have also tried to connect to a router I have that has no security whatsover for the time being but it seems it does not connect. I tried this:

```

x@x-G31T-M2:~$ sudo iwlist scan
wlx0013f7c99c1b  Scan completed :
          Cell 01 -

```
........
```

Cell 07 - Address: 74:EA:3A:AC:19:80
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:off
                    ESSID:"TP-LINK_AC1980"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000ca56c95
                    Extra: Last beacon: 320ms ago
                    IE: Unknown: 000E54502D4C494E4B5F414331393830
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0800000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD860050F204104A0001101044000101103B000103104700100000000000001000000074EA3AAC19801021000754502D4C494E4B10230009544C2D4D523332323010240003312E3010420003312E301054000800060050F20400011011001E576972656C657373204E20334720526F7574657220544C2D4D5233323230100800020086103C000101

```

Then I tried this:
```

x@x-G31T-M2:~$ sudo iwconfig wlx0013f7c99c1b essid TP-LINK_AC1980
x@x-G31T-M2:~$

```
After doing that I logged ([http://192.168.1.1](http://192.168.1.1)) in the router's admin admin website in order to check whether my computer shows up in the list of the devices connected wirelessly to the router. Unfortunately I do not see it there yet.


```

x@x-G31T-M2:~$ iwconfig
wlx0013f7c99c1b  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

ens33     no wireless extensions.

x@x-G31T-M2:~$

```


Moreover, I have the MAC filtering disabled in the router settings and as I said network security is also disabled(no wep, no wpa, no wpa2...it is open). I do not understand yet therefore, what the problem might be. 

Moreover I can connect to this router via wifi with an android phone successfully.

I really appreciate your help. I do not know what has been happening so far. I mean I just used the terminal interface so far (ctrl+alt+T). I just decided however to use to preferences->network connections and set up properly the wifi network connection. I already had tried a test without success with another router previously. The SSID and the wpa2 password from this other router were still there. What I did was filling this:

By means of this tool called "Network connections" (GUI):
1. I filled the correct SSID of the router that has no security in the WIFI connection that I had previously created.
2. I disabled the network security in the same WIFI connection.

Once I did that, the command iwconfig's output shows that the adaptor is already associated.

Now I must try to connect to the router that has WPA security. Let's see what happens.

Well, I do not really know whether it is associated. I got happy too quickly.

The command iwconfig for the router that has no security displays the following:

```

x@x-G31T-M2:~$ iwconfig
wlx0013f7c99c1b  IEEE 802.11bgn  ESSID:"TP-LINKAC1980"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

ens33     no wireless extensions.


```
It seems it is not associated. I thought it was associated because I saw the string <<ESSID:"TP-LINKAC1980">> in the iwconfig's output.

I did not know how to associate the WIFI adapter to the router by means of using commands in the terminal. I just saw however the reason why the app (nm-applet) that controls the WIFI did not get displayed on the bottom right side of the task bar. I just went to menu->preferences->LXSession apps and there I added nm-applet for automatic start. Then I logged out and in again and so I could see the WIFI adapter icon. By left clicking on this icon I could see the list of visible networks and then I just picked up the network I wanted. It worked fine. After that I tried with the WPA secured network and then it asked for the password and it worked also great.

Thank you for your help. I still wonder though, what it should have got done to make it work by only making use of the commands in the Linux's terminal. Unless someone wants to say a possible explanation, that is however not really important  because it worked fine thanks to the nm-applet GUI anyways.

---

### Post by chili555 on 2016-01-07
> Then I tried this:
Code:

x@x-G31T-M2:~$ sudo iwconfig wlx0013f7c99c1b essid TP-LINK_AC1980
x@x-G31T-M2:~$

After doing that I logged ([http://192.168.1.1](http://192.168.1.1)) in the router's admin admin website in order to check whether my computer shows up in the list of the devices connected wirelessly to the router. Unfortunately I do not see it there yet.There is a step missing:```
sudo dhclient wlx0013f7c99c1b
```It may not succeed with Network Manager running, but let's see what it reports.

---

### Post by thosecars822 on 2016-01-07
There is still something. I need to type "sudo modprobe rt2800usb" whenever I boot Linux in order to get the adapter working. This is kind of a hassle. I tried by appending the line "modprobe rt2800" to the file "/etc/modules" but it did not work after booting again.

Do you have any suggestion about this?

Thanks

I just had to replace the line "modprobe rt2800" that I had appended to the file "/etc/modules" with the line "rt2800usb". That fixed it. Now the Wifi adapter associates itself to the router automatically at Linux's boot time.
Thank you a lot.

---

### Post by chili555 on 2016-01-07
> **thosecars822 said:**
> I just had to replace the line "modprobe rt2800" that I had appended to the file "/etc/modules" with the line "rt2800usb". That fixed it. Now the Wifi adapter associates itself to the router automatically at Linux's boot time.
Thank you a lot.You blacklisted rt2800usb when you tried ndiswrapper. Let's fix all that. Please run:```
ndiswrapper -l
```That's a lower-case L for 'list.' Is the ndiswrapper driver rt2870? If so, erase it:```
sudo ndiswrapper -e rt2870
sudo rm /etc/modprobe.d/ndiswrapper.conf
```Now do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the line:```
blacklist rt2800usb
```Proofread carefully, save and close the text editor. Reboot and you should be all set.

---

### Post by thosecars822 on 2016-01-07
Thank you. I guess I must also remove the line "#blacklist rt2x00lib". I think I had added at the same time for testing purposes as well.

```


x@x-G31T-M2:~$ ndiswrapper -l
x@x-G31T-M2:~$ sudo ndiswrapper -e rt2870
[sudo] password for x: 
couldn't delete /etc/ndiswrapper/rt2870: No such file or directory
x@x-G31T-M2:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
x@x-G31T-M2:~$ sudo gedit /etc/modprobe.d/blacklist.conf

** (gedit:1933): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files

(gedit:1933): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files



```

Do you know why I get those two warnings whenever I launch "gedit"?

---

### Post by chili555 on 2016-01-07
> **thosecars822 said:**
> Thank you. I guess I must also remove the line "#blacklist rt2x00lib". I think I had added at the same time for testing purposes as well.

.....

** (gedit:1933): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files

(gedit:1933): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files



Do you know why I get those two warnings whenever I launch "gedit"?I haven't any idea. It works as expected despite the warnings, at least in my case.

You needn't remove #blacklist rt2x00lib because the leading # means that it's a comment and not an action to be executed. Usually, this technique is used to include notes as to why or how the change was made; for instance:```
#See forum post blah-blah and bug report 287511
blacklist some_module
```

---

### Post by thosecars822 on 2016-01-08
Thank you very much. Geditor works as well in my case as expected.

---

